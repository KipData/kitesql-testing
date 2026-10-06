# KiteSQL Testing

Large test corpora for [KiteSQL](https://github.com/KipData/KiteSQL), kept out of the main
repository and pulled in as a git submodule only when needed.

## Layout

| Path | Content |
|---|---|
| `data/sqlite/` | SQLite sqllogictest scripts, rewritten to run on KiteSQL |
| `scripts/` | Conversion scripts that produce `data/sqlite/` from the upstream corpus |

## Source

`data/sqlite/` is derived from the SQLite
[sqllogictest](https://www.sqlite.org/sqllogictest/doc/trunk/about.wiki) corpus, taken from the
mirror <https://github.com/gregrahn/sqllogictest> at commit
`c67f97bf3ca7e590d12e073408bcacaf2ff0f3a0`.

Files are converted by `scripts/` (for example adding a primary key where a table has none,
since KiteSQL requires one) and then fixed by hand where a script cannot. Expected results are
the original SQLite ones.

## Running

From the KiteSQL repository:

```shell
git submodule update --init
make test-slt-sqlite
```
