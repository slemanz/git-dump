# Tag

1. Commit your last changes to release the version:

```bash
git add --all
git commit -m "v1.0.0"
git push
```

2. Create a new tag and add a massage, then push:

```bash
git tag -a v1.0.0 -m "v1.0.0"
git push origin --tags
```

3. To show all tags use:

```bash
git tag
```

Then now, we can create a release version with the tag in github or gitlab.