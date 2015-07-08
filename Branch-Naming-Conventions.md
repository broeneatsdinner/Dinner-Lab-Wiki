#### Branch Prefixes
##### wtd when creating branches

**Bugfix** `bug-`
Typically used for fixing bugs against a release branch. Also can be used to fix bugs in develop branch and merged back into develop.

**Feature** `feature-`
used for specific feature work, branches from and merges back into develop

**Hotfix** `hotfix-`
quickly fix the master branch, merged into master and then into develop

**Release** `release-`
branched off of develop and merged into master every tuesday

---

Created from `develop` and merged back into `develop`
- `feature-`
- `bug-135-`

Created from `master` and merged back into `master`, then back into `develop`
- `hotfix-176-`
- `hotfix-`