# Transferring a Repository from Codeberg to GitHub (Retaining History)

---

## Steps

### 1. Clone the Codeberg Repository Locally

Clone the repository as a mirror (includes all branches and tags):

```bash
git clone --mirror ssh://git@codeberg.org/your-username/your-repo.git
cd your-repo
```

> **Note:** The folder will be named `your-repo` (without `.git` suffix).

---

### 2. Create a New Empty Repository on GitHub

- Go to [GitHub](https://github.com/new) and create a **new empty repository**.
- **Do not** initialize it with a README, `.gitignore`, or license.

---

### 3. Push to GitHub

Set the new GitHub repository as the remote and push all refs:

```bash
git remote set-url origin git@github.com:your-username/your-repo.git
git push --mirror
```

---

### 4. Clean Up (Optional)

If you want a fresh working directory (without the bare repository structure):

```bash
cd ..
rm -rf your-repo
git clone git@github.com:your-username/your-repo.git
```

---

## Notes

- **`.git` Folder**: The hidden `.git` folder is required for Git to work. Do not delete it.
- **Authentication**: Use SSH (`git@github.com:your-username/your-repo.git`) or HTTPS with a [GitHub personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).
- **Large Files**: For large repositories, consider using [Git LFS](https://git-lfs.com/).
- **Issues/Pull Requests**: These are not part of Git and will not transfer. Export/import them manually if needed.