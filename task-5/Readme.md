# Interactive Rebasing for Clean Commit History

Interactive rebasing helps modify commit history interactively in Git. It helps to clean up and refine the commit history before pushing changes to a repo.

- **Squash**: Combine multiple commits into a single commit.
- **Reorder commits**: Change the order of commits.
- **Edit**: Modify existing commit messages.
- **Drop unwanted commits**: Delete specific commits from history.

## Steps to Perform Interactive Rebase

### 1. Create a Text File and Make Multiple Commits
```sh
echo "First line" > rebasing.txt
git add .
git commit -m "First commit"

echo "Second line" >> rebasing.txt
git add .
git commit -m "Second commit"

echo "Third line" >> rebasing.txt
git add .
git commit -m "Third commit"
```

### 2. Check Commit History
```sh
git log --oneline
```

### 3. Perform Interactive Rebase for the Last N Commits
```sh
git rebase -i HEAD~n
```
This opens an interactive editor with a list of the last `n` commits.

### 4. Interactive Editor Options
- **pick**: Keep the commit as it is.
- **reword**: Edit the commit message.
- **edit**: Modify the commit before continuing the rebase.
- **fixup**: similar to squash but discards the commit changes.
  - Change `pick` to `edit`, and Git will stop at that commit.
  - Run the following commands to modify and continue:
    ```sh
    git add .
    git commit --amend
    git rebase --continue
    ```
- **squash**: Merge the commit with the previous one.
- **drop**: Delete a commit (may raise conflicts if an intermediate commit is removed).

### 5. Handling Merge Conflicts During Rebase
If a conflict occurs during rebasing:
```sh
git add .
git rebase --continue
```
To abort the rebase and revert changes:
```sh
git rebase --abort
```


