`secure-logging`: add configure switch and disable by default

The secure logging (slog) module and its command line tools
(slogkey, slogencrypt, slogverify) are now build-conditional and
disabled by default. Enable them with the `--enable-slog` /
`--disable-slog` autotools switches, or with `-DENABLE_SLOG=ON` /
`-DENABLE_SLOG=OFF` when building with CMake. The official DEB
and RPM packages no longer ship slog; it can be re-enabled by
building with the `sng-slog` Debian build profile or with
`--with slog` on RPM.
