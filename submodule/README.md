# Submodule

1. Add the submodule: `git submodule add <repo-url> <path>`

2. Commit the changes, you’ll see: 
   - .gitmodules
   - the submodule directory 

**To cloning a repo with submodules, you can use:**

```bash
git clone --recurse-submodules <repo-url>
```

or

```bash
git submodule init
git submodule update
```

**To update a submodule later:**

You can, pull latest changes from the submodule’s default branch

```bash
cd libs/library
git pull origin main
cd ../..
git commit -am "Update submodule"
```

Or from the root:

```bash
git submodule update --remote
```

**You also can checkout the submodule:**

To a tag:

```bash
cd libs/library
git checkout v1.2.3
```

or to a hash:

```bash
cd libs/library
git checkout a1b2c3d4
```

**To remove a submodule, you can:**

```bash
git submodule deinit -f libs/library
git rm -f libs/library
rm -rf .git/modules/libs/library
git commit -m "Remove submodule"
```

