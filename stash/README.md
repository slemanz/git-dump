# Stash

git stash saves your uncommitted changes (staged and unstaged) to a temporary
stack, letting you switch context without committing incomplete work. You can
reapply them later.

1. Stash current changes:

```bash
git stash
```

2. Stash with a descriptive message:

```bash
git stash push -m "work in progress on login page"
```

3. List all stashes:

```bash
git stash list
```

Output looks like:
```
stash@{0}: On feature: work in progress on login page
stash@{1}: WIP on main: abc1234 last commit message
```

4. Apply the most recent stash (keeps it in the stack):

```bash
git stash apply
```

5. Apply and remove from the stack:

```bash
git stash pop
```

6. Apply a specific stash:

```bash
git stash apply stash@{2}
git stash pop stash@{2}
```

7. See what a stash contains:

```bash
git stash show            # summary
git stash show -p         # full diff
git stash show stash@{1}  # specific stash
```

8. Drop a specific stash:

```bash
git stash drop stash@{0}
```

9. Clear all stashes:

```bash
git stash clear
```

**Other cases:**

- **Stash including untracked files:**

```bash
git stash push -u
```

- **Stash including untracked AND ignored files:**

```bash
git stash push -a
```

- **Stash only specific files:**

```bash
git stash push -m "partial stash" -- src/main.c src/utils.c
```

- **Create a branch from a stash:**

```bash
git stash branch new-branch stash@{0}
```

This creates a new branch from the commit where the stash was made, applies
the stash, and drops it. Useful when applying the stash on the current branch
would cause conflicts.
