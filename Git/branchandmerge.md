**Home**
- [Home](../index.md)
---

# Git Branching and Merging

## To create a **branch**
```console
git branch branch-name
```

## View created **branchs**
```console
git branch
```

## Switch to a **branch**
```console
git checkout branch-name
```

## Merge **branch** to **master branch**
- Fist checkout to **master branch** then:
```console
git merge branch-name-to-merge
```

## Update a branch when **master** is updated
- Fist checkout to the **branch** then:
```console
git rebase master
```

## To delete a branch
```console
git branch -d branch-name
```