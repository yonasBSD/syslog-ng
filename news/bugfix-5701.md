`cfg`, `tls`: respect `perm()` when writing security-sensitive files

The `--preprocess-into` config dump and the `tls(keylog-file())` output
are now created via a new `file_perm_options_fopen()` helper that
honours the global `perm()`/`owner()`/`group()` options with a `0600`
floor. Previously both files inherited the process umask (typically
`0644`); depending on the enclosing directory's permissions, this
could leave config secrets and TLS session keys readable to other
local users on the host.

Note for admins: the helper opens these two files with `O_NOFOLLOW`,
so if the target path is a symlink at the final component the open
will now fail with `ELOOP` instead of writing through the link.
Replace any such symlinks with the real destination path.
