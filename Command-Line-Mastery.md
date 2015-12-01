## Command Line Committing

##### Merging `release` into `master`.
Where `release` is a branch that is specifically not master, and also not a feature-branch (i.e. merging `feature-` into `master`). Note that we first switch to the `master` branch, because all merging, by its nature, sucks the external branch _into_ the current branch.

Notes on http://stackoverflow.com/questions/5350278/git-undo-auto-merging-on-a-specific-file-only-not-the-whole-branch

```
git checkout master
git status
git merge --no-commit release
git reset HEAD~1 _/php/globalsConfig.BIG_RED_BUTTON.php # Don't know if we need both
git checkout HEAD~1 -- _/php/globalsConfig.BIG_RED_BUTTON.php
git commit -m 'merged release --> master'
git push
```

***

##### Tagging a version number onto `master`.

###### Listing Tags
Listing the available tags in Git is straightforward. Just type `git tag`:
```
git checkout master
git tag
```
This command lists the tags in alphabetical order; the order in which they appear has no real importance.

###### Creating Tags
In the following example, the version number is `2.2` and the codename is `New Durham Tadpole`
```
git tag -a v2.2 -m 'New Durham Tadpole'
```

###### Pushing Tags
By default, the git push command doesn't transfer tags to remote servers. You will have to explicitly push tags to a shared server after you have created them. This process is just like sharing remote branches – you can run git push origin [tagname].
```
git push origin v2.2
```

***

##### Merging `master` into `release`.
Once `master` has been updated and tagged with the latest release version. Start the "trickle-down" effect by merging `master` into `release`.
```
git checkout release
git status
git merge --no-commit master
git reset HEAD _/php/globalsConfig.BIG_RED_BUTTON.php
git checkout -- _/php/globalsConfig.BIG_RED_BUTTON.php
git commit -m 'merged master --> release'
git push
```

***

##### Merging `release` into `develop`.
Once `release` has been updated and tagged with the latest release version. Continue the "trickle-down" effect by merging `release` into `develop`.
```
git checkout develop
git status
git merge --no-commit release
git reset HEAD _/php/globalsConfig.BIG_RED_BUTTON.php
git checkout -- _/php/globalsConfig.BIG_RED_BUTTON.php
git commit -m 'merged release --> develop'
git push
```

***