## Command Line Committing

##### Merging a `<merge-branch>` into `master`.
Where `<merge-branch>` is a branch that is specifically not master, and also not a feature-branch (i.e. merging `develop` into `master`). To merge feature branches, instructions are covered in [Feature Branches](https://github.com/dinnerlab/dinnerlab/wiki/Feature-Branches). Note that we first switch to the `master` branch, because all merging, by its nature, sucks the external branch _into_ the current branch.
```
git checkout master
git status
git merge --no-commit <merge-branch>
git reset HEAD _/php/globalsConfig.BIG_RED_BUTTON.php
git checkout -- _/php/globalsConfig.BIG_RED_BUTTON.php
git commit -m 'merged <merge-branch> --> master'
```

---

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

