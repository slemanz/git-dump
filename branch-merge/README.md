# Branch and Merge

## Branch

1. Ensure you are on the main branch:

```bash
git checkout main
git pull origin main
```

2. Create a branch:

```bash
git checkout -b my-feature-branch
```

or using the newer `switch` command:

```bash
git switch -c my-feature-branch
```

3. Push the branch and set upstream in one step:

```bash
git push -u origin my-feature-branch
```

4. List branches:

```bash
git branch          # local branches
git branch -r       # remote branches
git branch -a       # all branches
```

5. Rename a branch:

```bash
git branch -m old-name new-name
```

6. Delete a branch:

```bash
git branch -d my-feature-branch          # safe delete (only if merged)
git branch -D my-feature-branch          # force delete
git push origin --delete my-feature-branch  # delete remote branch
```

## Merge

7. Switch to the target branch and merge:

```bash
git checkout main
git merge my-feature-branch
```

8. Types of merge:
    - **Fast-forward:** If `main` has no new commits, Git just moves the pointer
    forward. No merge commit is created.
    - **Three-way merge:** If both branches have new commits, Git creates a merge
    commit combining the two histories.

9. Force a merge commit even when fast-forward is possible:

```bash
git merge --no-ff my-feature-branch
```

This is useful to keep the branch history visible in the log.

10. If conflicts arise during merge:

```bash
# 1. resolve the conflicts in the files
# 2. stage the resolved files
git add <resolved-files>
# 3. finish the merge
git merge --continue
```

11. Abort a merge: `git merge --abort`

**Other cases:**

- **See which branches are already merged into main:**

```bash
git branch --merged main
```

- **See which branches have NOT been merged:**

```bash
git branch --no-merged main
```

- **Squash merge (combine all branch commits into one):**

```bash
git merge --squash my-feature-branch
git commit -m "feat: add my feature"
```
