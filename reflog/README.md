# Reflog

git reflog is a command that records updates to the tip of branches and other
references in your local repository. It acts as a safety net, letting you
recover commits, branches, or changes that would otherwise seem "lost" after
operations like reset, rebase, amend, or branch deletion.

1. View the reflog of HEAD: `git reflog`

2. View the reflog of a specific branch: `git reflog show <branch-name>`

3. Each entry looks like: `abc1234 HEAD@{2}: commit: my message`
    - `HEAD@{2}` means "where HEAD was 2 moves ago"
    - You can reference it directly in other commands

4. Recover a commit that was lost (e.g. after a hard reset):

```bash
git reflog
git reset --hard HEAD@{1}
```

5. Recover a deleted branch:

```bash
git reflog
git checkout -b <branch-name> <commit-hash>
```

6. Undo a bad rebase or amend: find the entry before the operation in the
reflog and reset to it:

```bash
git reset --hard HEAD@{5}
```

**Other cases:**

- **Expire old entries:** Reflog entries are kept for 90 days by default (30
for unreachable commits). You can force cleanup with: `git reflog expire --expire=now --all`

- **Reflog is local only:** It is not pushed to the remote, so it only helps
you recover things on the machine where the operation happened.

- **Inspect before resetting:** Use `git show HEAD@{n}` to confirm the content
of an entry before moving HEAD to it.
