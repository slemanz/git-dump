# Cherry-pick

git cherry-pick applies the changes of a specific commit from one branch onto
your current branch. Unlike merge or rebase, it picks individual commits
without bringing the entire branch history.

1. Identify the commit you want: `git log --oneline <source-branch>`

2. Switch to the target branch:

```bash
git checkout main
```

3. Cherry-pick the commit:

```bash
git cherry-pick <commit-hash>
```

A new commit is created on your current branch with the same changes.

4. Cherry-pick multiple commits:

```bash
git cherry-pick <hash1> <hash2> <hash3>
```

5. Cherry-pick a range of commits:

```bash
git cherry-pick <start-hash>^..<end-hash>
```

6. If conflicts arise, resolve them and continue:

```bash
git add <resolved-files>
git cherry-pick --continue
```

7. Abort the cherry-pick: `git cherry-pick --abort`

**Other cases:**

- **Cherry-pick without committing (stage changes only):**

```bash
git cherry-pick --no-commit <commit-hash>
```

Useful when you want to combine changes from several commits into one.

- **Cherry-pick a merge commit:** You must specify the parent with `-m`:

```bash
git cherry-pick -m 1 <merge-commit-hash>
```

- **Typical use case — hotfix:** You fixed a bug on `develop` and need it on
`main` right now without merging the entire branch:

```bash
git checkout main
git cherry-pick <bugfix-commit-hash>
git push
```
