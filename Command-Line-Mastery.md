## Command Line Committing

##### Merging a `<merge-branch>` into `master`.
Where `<merge-branch>` is a branch that is specifically not master, and also not a feature-branch (i.e. merging `develop` into `master`). To merge feature branches, that will be covered later in this wiki. Note that we first switch to the `master` branch, because all merging, by its nature, sucks the external branch _into_ the current branch.
```
git checkout master
git status
git merge --no-commit <merge-branch>
git reset HEAD _/php/globalsConfig.BIG_RED_BUTTON.php
git checkout -- _/php/globalsConfig.BIG_RED_BUTTON.php
git commit -m 'merged <merge-branch> --> master'
```

---

##### How to `cherry-pick`
Even though it has a cool fucking name, it's best practice to not cherry-pick. This is because a proper merge of a feature branch preserves the HEAD history. With that, we can see where in time a feature branch merge took place, inspect it, roll it back, and ask for a pull request in the first place.

But, sometimes the world isn't perfect, and we gotta pick the cherries.

[Stack Overflow: Cherry Pick](http://stackoverflow.com/questions/881092/how-to-merge-a-specific-commit-in-git)