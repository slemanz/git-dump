# Blame

git blame shows who last modified each line of a file and in which commit. It is
useful for understanding the history behind a piece of code and finding the right
person to ask about a change.

1. Basic usage: `git blame <file>`

```bash
git blame src/main.c
```

Each line shows: commit hash, author, date, and the line content.

2. Blame a specific range of lines:

```bash
git blame -L 10,20 src/main.c
```

3. Ignore whitespace changes: `git blame -w <file>`
    - Useful when formatting changes hide the real author

4. Show the original commit even after the code was moved or copied:

```bash
git blame -C src/main.c
```

- Use `-C -C` (twice) to also detect code moved from other files
- Use `-C -C -C` (three times) to detect across all files in the commit

5. Blame a file at a specific commit:

```bash
git blame <commit-hash> -- src/main.c
```

6. Show email instead of name: `git blame -e <file>`

**Useful combinations:**

- **Blame with a short hash:**

```bash
git blame --abbrev=7 src/main.c
```

- **Find who introduced a specific line, then inspect the commit:**

```bash
git blame src/main.c
git show <commit-hash>
```

- **Ignore revisions that are just formatting (e.g. a linter commit):**

```bash
echo <commit-hash> >> .git-blame-ignore-revs
git blame --ignore-revs-file .git-blame-ignore-revs src/main.c
```

You can configure this globally:
`git config blame.ignoreRevsFile .git-blame-ignore-revs`
