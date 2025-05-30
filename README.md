# Combine Old Git Repositories into Subdirectories

This guide walks you through importing another Git repository into a subdirectory of a new GitHub repository, preserving its full history.

## Steps

### 1. Create a New Repository on GitHub

- Visit: [https://github.com/new](https://github.com/new)
- Repository name: `old_repos`
- **Do not** initialize with a README, `.gitignore`, or license.

---

### 2. Clone the New Empty Repository Locally

```bash
git clone https://github.com/manishb9/old_repos.git
cd old_repos
```

---

### 3. Add the Old Repository as a Remote

```bash
git remote add books https://github.com/manishb9/books.git
git fetch books
```

---

### 4. Merge the Old Repo into a Subdirectory (e.g., `books/`)

```bash
git read-tree --prefix=books/ -u books/main
```

> ⚠️ If the `books` repo uses a different branch name (e.g., `master`), replace `main` with the correct branch name.

---

### 5. Commit the Changes

```bash
git commit -m "Imported books repository into books/ subdirectory with full history"
```

---

### 6. Remove the Temporary Remote

```bash
git remote remove books
```

---

### 7. Push Everything to GitHub

```bash
git push origin main
```

---

## Result

You now have the entire commit history of the `books` repository inside a `books/` subdirectory of your new `old_repos` repository.

You can repeat steps 3–6 to add more repositories under different subdirectories.
