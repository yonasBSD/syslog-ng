`filter-blank`: Fix race condition when evaluating from multiple threads

The per-evaluation result was stored in a shared struct field, so
concurrent worker threads could read each other's intermediate state,
causing `blank()`/`not blank()` to return incorrect results.
