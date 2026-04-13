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
