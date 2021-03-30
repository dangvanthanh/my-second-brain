Tags: #nodejs 

---

# Installing Node With Brew Fails

When you install Node with Brew is fails. Try again:


```shell
$ brew uninstall --force node
$ brew uninstall icu4c && brew install icu4c
$ brew unlink icu4c && brew link icu4c --force
$ brew install node

```