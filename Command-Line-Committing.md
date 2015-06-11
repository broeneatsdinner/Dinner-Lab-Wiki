## Command Line Committing

To merge <merge-branch> into master. Note that we first switch to the `master` branch, because all merging, by its nature, sucks the external branch _into_ the current branch.
```
git checkout master
git status
git merge --no-commit <merge-branch>
git reset HEAD _/php/globalsConfig.BIG_RED_BUTTON.php
git checkout -- _/php/globalsConfig.BIG_RED_BUTTON.php
git commit -m "merged <merge-branch> --> master"
```