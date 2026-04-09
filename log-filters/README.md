# Log Filters

git log has many options to filter commits by author, date, message, file, or
content. This is useful when you want to find a specific change in a large
history without scrolling through every commit.

1. Basic log with a compact format: `git log --oneline`

2. Filter by author: `git log --author="slemanz"`
    - Matches partial names and is case-insensitive by default
    - Use `--perl-regexp -i` for regex matching

3. Filter by date range:

```bash
git log --since="2024-01-01" --until="2024-12-31"
git log --since="2 weeks ago"
```

4. Filter by commit message: `git log --grep="fix"`
    - Combine with `-i` for case-insensitive search
    - Use `--all-match` with multiple `--grep` to require all patterns

5. Filter by file or path: `git log -- path/to/file`
    - Shows only commits that touched that file or directory

6. Filter by code content (pickaxe): `git log -S"functionName"`
    - Finds commits that added or removed the given string
    - Use `-G"regex"` for regex matching on the diff

7. Limit the number of commits: `git log -n 5`

**Useful combinations:**

- **Who changed a file and when:**

```bash
git log --oneline --author="slemanz" -- src/main.c
```

- **Commits in a branch but not in main:**

```bash
git log main..feature-branch
```

- **Pretty format with graph:**

```bash
git log --oneline --graph --decorate --all
```

- **Show the diff of each matching commit:**

```bash
git log -p --author="slemanz" --since="1 month ago"
```

- **Stats per commit:** `git log --stat` shows files changed and line counts.
