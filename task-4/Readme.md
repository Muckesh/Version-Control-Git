# Simulating and Resolving Merge Conflicts in Git

Learning how to simulate and resolve merge conflicts in Git. Creating two branches, making conflicting changes, and manually resolving the conflicts.

## Steps to Simulate Merge Conflict

### 1. Initialize Git Repository
```sh
git init
```

### 2. Create a File and Commit It
```sh
echo "Hello world" > merge-conflicts.txt
git add .
git commit -m "merge conflict file"
```

### 3. Creating Two Branches
```sh
git branch branch1
git branch branch2
```

### 4. Switch to `branch1` and Modify the File
```sh
git checkout branch1
echo "This is branch1 change" >> merge-conflicts.txt
git add .
git commit -m "Updated file in branch1"
```

### 5. Switch to `branch2` and Modify the File
```sh
git checkout branch2
echo "This is branch2 change" >> merge-conflicts.txt
git add .
git commit -m "Updated file in branch2"
```

## Resolving Merge Conflict

### 6. Switch Back to `branch1`
```sh
git checkout branch1
```

### 7. Merge `branch2` into `branch1`
```sh
git merge branch2
```
This will create a merge conflict since both branches have modified `merge-conflicts.txt`.

### 8. Check Differences
```sh
git diff
```

### 9. Manually Resolving the Conflict
Open `merge-conflicts.txt` and modify the conflicting section to keep the desired content. Example:
```plaintext
Hello world
This is branch1 change
This is branch2 change
```

### 10. Checking Status and Staging the Resolved File
```sh
git status
git add .
git commit -m "Resolved merge conflicts between branch1 and branch2."
```

### 11. Verifying Commit History
```sh
git log --oneline
```
