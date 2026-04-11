# Rebase

git rebase moves or replays your commits on top of another base commit. It
rewrites history to create a cleaner, linear timeline without merge commits.

## Basic rebase

1. Switch to your feature branch: `git checkout feature-branch`

2. Rebase onto main:

```bash
git rebase main
```

This takes the commits from `feature-branch` that are not in `main` and
replays them on top of `main`.

3. If conflicts arise, resolve them and continue:

```bash
git add <resolved-files>
git rebase --continue
```

4. To abort a rebase at any point: `git rebase --abort`

5. Force push after rebase (since history was rewritten):

```bash
git push --force-with-lease
```

## Interactive rebase

Interactive rebase lets you edit, reorder, squash, or drop commits.

1. Start an interactive rebase for the last N commits:

```bash
git rebase -i HEAD~3
```

2. The editor opens with a list of commits and actions:

```
pick abc1234 first commit message
pick def5678 second commit message
pick ghi9012 third commit message
```

3. Available actions:
    - `pick` — keep the commit as is
    - `reword` — keep the commit but edit the message
    - `squash` — merge into the previous commit (keeps both messages)
    - `fixup` — merge into the previous commit (discards this message)
    - `drop` — remove the commit entirely
    - `edit` — pause to amend the commit

4. Save and close the editor to apply.

**Other cases:**

- **Rebase onto a specific commit:**

```bash
git rebase --onto <new-base> <old-base> <branch>
```

- **Pull with rebase instead of merge:**

```bash
git pull --rebase origin main
```

- **Autosquash fixup commits:**

```bash
git commit --fixup=<commit-hash>
git rebase -i --autosquash main
```

- **When NOT to rebase:** Never rebase commits that have already been pushed
and shared with others. It rewrites history, which forces everyone to reset
their local branches.
