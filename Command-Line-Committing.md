## Command Line Committing

##### Merging a `<merge-branch>` into `master`.
Where `<merge-branch>` is a branch that is specifically not master, and also not a feature-branch (i.e. merging `develop` into `master`). To merge feature branches, that will be covered later in this wiki. Note that we first switch to the `master` branch, because all merging, by its nature, sucks the external branch _into_ the current branch.
```
git checkout master
git status
git merge --no-commit <merge-branch>
git reset HEAD _/php/globalsConfig.BIG_RED_BUTTON.php
git checkout -- _/php/globalsConfig.BIG_RED_BUTTON.php
git commit -m "merged <merge-branch> --> master"
```