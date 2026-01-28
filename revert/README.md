# Revert

git revert is a command used to undo the changes made by a specific commit. It
creates a new commit that applies the inverse of the changes from the commit you
specify, effectively canceling them out without altering the project history 

1. Ensure your working directory is clean: `git status`

2. Identify the commit to revert: `git log --oneline`

3. Run the git revert command: `git revert <commit-hash>`
    - To revert the most recent commit, you can use the shortcut HEAD: `git revert HEAD`

4. Edit the commit message (if needed)

5. Resolve conflicts (if any)
    - After resolving conflicts in the files, use `git add <file-name>` for each
    resolved file. Continue the revert process with: `git revert --continue`

6. Push the changes: `git push origin <branch-name>`

**Other cases:**

- **Revert a range of commits:** You can revert multiple commits at once by specifying
a range, for example: `git revert HEAD~3..HEAD~1`. Note the caret (^) symbol might
be needed to include the starting commit (`git revert <hash1>^..<hash2>`).

- **Reverting a merge commit:** Reverting a merge commit requires specifying which
parent is the "mainline" using the -m option: `git revert -m 1 <merge-commit-hash>`