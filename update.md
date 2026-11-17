
# Update from Originating Repository

**Ensure upstream:**

```bash
git remote -v

```

In the output if you see

```txt
upstream        https://github.com/sujaykundu777/devlopr-jekyll.git (fetch)
upstream        https://github.com/sujaykundu777/devlopr-jekyll.git (push)
```

If not add the remote repository

```bash
git remote add upstream https://github.com/sujaykundu777/devlopr-jekyll.git

```

## Merge

1. Fetch the changes

   ```bash
   git fetch upstream

    ```

2. Merge the changes

    ```bash
    git merge upstream/master

    ```

3. Correct any conflicts using the IDE

---
