# Amend

git commit --amend lets you modify the most recent commit. You can change the
commit message, add forgotten files, or both. It replaces the last commit with
a new one (new hash), so it rewrites history.

## Changing the commit message

1. Amend only the message of the last commit:

```bash
git commit --amend -m "new commit message"
```

2. Open the editor to edit the message:

```bash
git commit --amend
```

## Adding forgotten changes

3. Stage the files you forgot and amend:

```bash
git add forgotten-file.c
git commit --amend
```

The new files are included in the last commit. The editor opens so you can
update the message if needed.

4. Amend without changing the message:

```bash
git add forgotten-file.c
git commit --amend --no-edit
```

## Changing the author

5. Fix the author of the last commit:

```bash
git commit --amend --author="Name <email@example.com>"
```

## After pushing

6. If the original commit was already pushed, you need to force push:

```bash
git push --force-with-lease
```

Use `--force-with-lease` instead of `--force` — it checks that no one else
pushed new commits to the branch, preventing you from overwriting their work.

**Important:**

- **Never amend commits that are shared with others** (e.g. already merged into
`main`). It rewrites history and will cause problems for everyone.

- **Amend only replaces the last commit.** To modify older commits, use
`git rebase -i` instead.

- **The original commit still exists** in the reflog for a while, so you can
recover it if something goes wrong: `git reflog`
