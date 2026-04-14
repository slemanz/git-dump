# Reset

git reset moves the HEAD (and optionally the staging area and working directory)
to a specific commit. It is used to undo commits, unstage files, or completely
discard changes. The key is understanding the three modes.

## The three modes

1. **Soft reset** — moves HEAD, keeps staging and working directory:

```bash
git reset --soft HEAD~1
```

The commit is undone but all changes remain staged, ready to commit again.
Useful when you want to redo the commit message or combine commits.

2. **Mixed reset (default)** — moves HEAD, resets staging, keeps working directory:

```bash
git reset HEAD~1
git reset --mixed HEAD~1   # same thing
```

The commit is undone and changes are unstaged, but still present in your
files. Useful when you want to restage selectively.

3. **Hard reset** — moves HEAD, resets staging AND working directory:

```bash
git reset --hard HEAD~1
```

The commit and all changes are completely discarded. **This is destructive.**

## Unstaging files

4. Unstage a file (keep changes in working directory):

```bash
git reset HEAD <file>
```

or using the newer command:

```bash
git restore --staged <file>
```

5. Unstage all files:

```bash
git reset HEAD
```

## Resetting to a specific commit

6. Reset to a specific commit hash:

```bash
git reset --soft <commit-hash>
git reset --mixed <commit-hash>
git reset --hard <commit-hash>
```

7. Reset to match the remote branch:

```bash
git fetch origin
git reset --hard origin/main
```

## Comparison table

| Mode | HEAD | Staging | Working directory |
|------|------|---------|-------------------|
| `--soft` | moves | unchanged | unchanged |
| `--mixed` | moves | reset | unchanged |
| `--hard` | moves | reset | reset |

**Recovery:**

- If you did a `--hard` reset by mistake, the old commit is still in the
reflog for ~30 days:

```bash
git reflog
git reset --hard HEAD@{1}
```

**Reset vs Revert:**

- `reset` rewrites history — use it for local, unpushed commits.
- `revert` creates a new commit that undoes changes — use it for commits that
were already pushed and shared.
