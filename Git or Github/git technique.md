## Revert changes but remain existing commit for references

Retrieve the latest file from base branch 
`git checkout main -- path/to/file`

Just add the file you trying to recover/revert and do commit


## Move file location
`git mv <source> <destination>`

**Example:** `git mv src/components/xxx/aaa.js src/components/aaa.js`


## Changing Base Branch and Retaining Relevant Commits with Cherry-Pick

### Scenario

You have a branch `B` based on branch `A1` with the following commit history:

```
commit1: step 1 done
commit2: step 2 done
commit3: Merge branch A1
commit4: step 3 done
```

Now you want to change the base branch from `A1` to `A2`, and retain only the relevant commits (`step 1`, `step 2`, and `step 3`), excluding the merge commit from `A1`.

### Steps

1. **Fetch the Latest Changes**:

   ```bash
   git fetch origin
   ```

2. **Switch to Your Feature Branch**:

   ```bash
   git checkout B
   ```

3. **Create a Backup Branch (Optional but Recommended)**:

   ```bash
   git checkout -b B-backup
   ```

4. **Create a New Branch Based on `A2`**:

   ```bash
   git checkout -b B-new origin/A2
   ```

5. **Cherry-Pick the Relevant Commits**:

   ```bash
   git cherry-pick 3095de2
   git cherry-pick feebe63
   ```

6. **Force Push the New Branch to Remote**:

   ```bash
   git push --force origin B-new:B
   ```

### Full Command Sequence

```bash
git fetch origin
git checkout B
git checkout -b B-backup
git checkout -b B-new origin/A2
git cherry-pick 3095de2
git cherry-pick feebe63
git push --force origin B-new:B
```

### Handling Conflicts

If conflicts arise during the cherry-pick process, Git will stop and allow you to resolve them. After resolving conflicts, you can continue the cherry-pick:

```bash
git add .
git cherry-pick --continue
```

### Sync Local Branch `B` with Updated Remote `B`

1. **Fetch the Latest Changes from Remote**:

   ```bash
   git fetch origin
   ```

2. **Switch to Your Local Branch `B`**:

   ```bash
   git checkout B
   ```

3. **Reset Your Local Branch to Match the Remote Branch**:

   ```bash
   git reset --hard origin/B
   ```

### Full Command Sequence

```bash
git fetch origin
git checkout B
git reset --hard origin/B
```

### Important Note

Using `git reset --hard` will discard any local changes that you have not committed. If you have any uncommitted work that you want to keep, make sure to stash or commit those changes before performing the hard reset:

- To stash your changes:

  ```bash
  git stash
  ```

  You can later apply the stashed changes using:

  ```bash
  git stash apply
  ```

- To commit your changes:

  ```bash
  git add .
  git commit -m "Save work before syncing with remote"
  ```



   
