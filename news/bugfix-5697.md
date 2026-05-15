`pdbtool`: use fixed ISO-8601 timestamp format in patternize progress messages

Patternize progress lines now use `YYYY-MM-DDTHH:MM:SS.UUUUUU` formatting instead of
`ctime()` output, making them consistent with other syslog-ng message timestamps.
This also avoids relying on `ctime()` in this path, reducing possible multithreading issues.
