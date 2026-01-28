# Git Flow Branching Strategy – Demo Repository

This repository is created **only to demonstrate Git Flow branching strategy**.
The focus is on **branching, merging, and workflow**, not on application code.

---

##  Branches Used

### `main`

* Represents **production-ready code**
* Always stable
* Only receives code from `release/*` or `hotfix/*`

### `develop`

* Integration branch
* Contains latest completed features
* Base branch for feature development

### `feature/*`

* Used for developing individual features
* Created from `develop`
* Merged back into `develop`

Example:

```
feature/add-book
```

### `release/*`

* Used to prepare a new production release
* Created from `develop`
* Used for version updates and minor bug fixes
* Merged into **both** `main` and `develop`

Example:

```
release/1.0
```

### `hotfix/*`

* Used for **urgent production fixes**
* Created from `main`
* Merged into **both** `main` and `develop`

Example:

```
hotfix/1.0.1
```

---

## Git Flow Workflow

```
main
 └── develop
      ├── feature/add-book
      ├── feature/borrow-book
      └── release/1.0
              └── hotfix/1.0.1
```

---

## Practical Steps Followed in This Repo

### Create `develop` branch

```bash
git checkout -b develop
```

---

### Create feature branch

```bash
git checkout -b feature/add-book develop
```

Work on feature and commit changes:

```bash
git commit -m "Add add-book feature"
```

Merge back to develop:

```bash
git checkout develop
git merge feature/add-book
```

---

### Create release branch

```bash
git checkout -b release/1.0 develop
```

Prepare release (version update, fixes):

```bash
git commit -am "Prepare release 1.0"
```

Merge release:

```bash
git checkout main
git merge release/1.0

git checkout develop
git merge release/1.0
```

---

### Create hotfix branch

```bash
git checkout -b hotfix/1.0.1 main
```

Fix production bug:

```bash
git commit -am "Fix critical production bug"
```

Merge hotfix:

```bash
git checkout main
git merge hotfix/1.0.1

git checkout develop
git merge hotfix/1.0.1
```

---

## Author

**Rakshit Saxena**
Intern – Git & Version Control Practice
