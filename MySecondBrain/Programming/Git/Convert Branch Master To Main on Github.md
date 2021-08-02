Tags: #git

---

# Convert Branch Master To Main on Github

## Move the `Master` branch to `main`

```sh
$ git branch -m master main
```

## Push `main` to remote repo

```sh
$ git push -u origin main
```

## Point HEAD to `main` branch

```sh
$ git symbolic-ref refs/remotes/origin/HEAD refs/remotes/origin/main
```

## Change default branch on Github

## Delete `master` branch on the remote repo

```sh
$ git push origin --delete master
```

## Summary

```
$ git branch -m master main
$ git fetch origin
$ git branch -u origin/main main
$ git remote set-head origin -a
```