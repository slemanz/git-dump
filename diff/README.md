# Diff

git diff shows the differences between various states of your repository:
working directory, staging area, commits, and branches. It is one of the most
used commands for reviewing changes before committing or merging.

## Working directory and staging

1. See unstaged changes (working directory vs staging area):

```bash
git diff
```

2. See staged changes (staging area vs last commit):

```bash
git diff --staged
```

3. See all changes (working directory vs last commit):

```bash
git diff HEAD
```

4. Diff a specific file:

```bash
git diff -- src/main.c
git diff --staged -- src/main.c
```

## Comparing commits

5. Diff between two commits:

```bash
git diff <commit1> <commit2>
```

6. Diff the last commit against the one before it:

```bash
git diff HEAD~1 HEAD
```

7. Show only the names of changed files:

```bash
git diff --name-only <commit1> <commit2>
```

8. Show a stat summary (files + lines changed):

```bash
git diff --stat <commit1> <commit2>
```

## Comparing branches

9. See what changed in `feature` compared to `main`:

```bash
git diff main..feature
```

10. See only what `feature` introduced since it diverged from `main`:

```bash
git diff main...feature
```

The triple dot (`...`) compares `feature` against the common ancestor, so it
ignores new commits on `main` that happened after the branch point.

11. Compare a specific file between branches:

```bash
git diff main..feature -- src/main.c
```

## Comparing with remote

12. See what you are about to push:

```bash
git fetch origin
git diff origin/main..HEAD
```

13. See what would be pulled:

```bash
git fetch origin
git diff HEAD..origin/main
```

**Useful options:**

- **Word-level diff:** `git diff --word-diff` — highlights changes inline
instead of showing full lines.

- **Ignore whitespace:** `git diff -w` — ignores all whitespace differences.

- **Color only:** `git diff --color-words` — shows only the changed words in color.

- **Generate a patch file:**

```bash
git diff main..feature > changes.patch
git apply changes.patch
```
