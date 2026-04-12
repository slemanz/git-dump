# Clean

git clean removes untracked files from your working directory. It is useful for
getting rid of build artifacts, generated files, or anything that is not being
tracked by Git.

1. Preview what would be deleted (dry run):

```bash
git clean -n
```

Always run a dry run first — clean is irreversible.

2. Remove untracked files:

```bash
git clean -f
```

The `-f` (force) flag is required by default as a safety measure.

3. Remove untracked files and directories:

```bash
git clean -fd
```

4. Remove untracked files, directories, AND ignored files:

```bash
git clean -fdx
```

This is useful for a truly clean build from scratch (removes `node_modules/`,
`__pycache__/`, `.o` files, etc.).

5. Remove only ignored files (keep untracked files):

```bash
git clean -fX
```

Useful for cleaning build artifacts without deleting new files you created.

6. Interactive mode:

```bash
git clean -i
```

Lets you choose file by file what to delete.

7. Clean a specific path:

```bash
git clean -fd -- src/
```

**Common workflows:**

- **Full reset to match the repo exactly:**

```bash
git checkout -- .
git clean -fd
```

- **Nuclear clean (working directory identical to the last commit):**

```bash
git reset --hard HEAD
git clean -fdx
```

- **Difference between the flags:**

| Flag | Effect |
|------|--------|
| `-n` | Dry run, show what would be removed |
| `-f` | Force, actually remove files |
| `-d` | Include untracked directories |
| `-x` | Include ignored files |
| `-X` | Only ignored files |
| `-i` | Interactive mode |
