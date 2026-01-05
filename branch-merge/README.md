# Branch and Merge

## Branch

1. Ensure you are on the main branch

```bash
git checkout main
git pull origin main
```

2. Create a Branch

```bash
git checkout -b my-feature-branch
```

or

```bash
git branch my-feature-branch
git checkout my-feature-branch
```

3. Push the Branch to the Server

```bash
git push -u origin my-feature-branch
```

4. In first push set upstream

```
git push --set-upstream origin my-feature-branch
```