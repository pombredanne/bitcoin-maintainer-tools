External repository for Bitcoin Core related maintenance tools.

clang-format
------------

A script to format cpp source code according to the .clang-format file in the bitcoin repo.
This should only be applied to new files or files which are currently not actively developed on.
Also, git subtrees are not subject to formatting.

Note: The script is currently untested and unmaintained, but kept for archival reasons, in
case it is planned to be used some day.

build-for-compare
--------------------

Build for binary comparison.

See `build-for-compare.py --help` for more information.

Builds from current directory, which is assumed to be a git clone of the bitcoin repository.

**DO NOT RUN this with the nocopy=1 flag set on working tree if you have any local additions, it will nuke all
non-repository files, multiple times over. By leaving nocopy off (default) the git tree is copied to a temporary
directory and all operations are performed there.**

Example:
```bash
git clone https://github.com/bitcoin/bitcoin.git bitcoin-compare
cd bitcoin-compare
../bitcoin-maintainer-tools/build-for-compare.py 4731cab 2f71490
sha256sum /tmp/compare/bitcoind.*.stripped
git diff -W --word-diff /tmp/compare/4731cab /tmp/compare/2f71490
```

unittest-statistics
--------------------------

`unittest-statistics.py` can be used to print a table of the slowest 20 unit tests.

Usage:
```bash
unittest-statistics.py </path/to/test_bitcoin> [<subtest>]
```

For example:
```bash
unittest-statistics.py src/test/test_bitcoin wallet_tests
```

treehash512
--------------

This script will show the SHA512 tree has for a certain commit, or HEAD
by default.

Usage:

```bash
treehash512.py [<commithash>]
```

This should match the Tree-SHA512 commit metadata field added by
github-merge.
