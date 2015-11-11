##### How to get a file from another branch.
It's possible to take a single file it its current state from another branch and smack it onto your branch.

```
git checkout develop              # first get back to develop
git checkout experiment -- app.js # then copy the version of app.js 
                                  # from branch "experiment"
```

See also [how to undo changes of one file](http://stackoverflow.com/questions/692246/undo-working-copy-modifications-of-one-file-in-git)?

***

##### Renaming branches

```
git checkout oldbranch				
git pull				
git branch -m oldbranch newbranch        # Rename branch locally
git push origin :oldbranch               # Delete the old branch
git push --set-upstream origin newbranch # push the new branch, set local branch to track the new remote
```

***

##### How to `cherry-pick`
Even though it has a cool name, it's best practice to not cherry-pick. This is because a proper merge of a feature branch preserves the HEAD history. With that, we can see where in time a feature branch merge took place, inspect it, roll it back, and ask for a pull request in the first place.

But, sometimes the world isn't perfect, and we gotta pick the cherries.

[Ariejan: Cherry Pick](https://ariejan.net/2010/06/10/cherry-picking-specific-commits-from-another-branch/)

[Stack Overflow: Cherry Pick](http://stackoverflow.com/questions/881092/how-to-merge-a-specific-commit-in-git)

###### With great power, comes great responsibility.

Cherry picking is: taking a single commit from the middle of one branch and adding it to another:
```
A-----B-----C-----D
 \
  \
   E
```
becomes
```
A-----B-----C-----D
 \
  \
   E-----C'
```
This, of course, can be done with the git cherry-pick command.

The problem with these commits is that git considers commits to include all history before them - thus, if you have three commits like so:
```
A-----B-----C
```
And try to get rid of B, you have to create an entirely new commit like so:
```
A-----------C'
```
Where C' has a different SHA-1 ID than its counterpart C. Likewise, cherry picking a commit from one branch to another basically involves generating a patch, then applying it, thus losing history that way as well.

This changing of commit IDs breaks git's merging functionality among other things (though if used sparingly there are heuristics that will paper over this). More importantly though, it ignores functional dependencies - if C actually used a function defined in B, you'll never know.

Perhaps a better way to handle this would be to have more fine grained branches. That is, instead of just having a `master`, have `featureA`, `bugfixB`, etc. Perform code review on an entire branch at a time - where each branch is very focused on doing only one thing - and then merge that one branch when you're done. This is the workflow that git is designed for, and what it's good at :)

If you insist on dealing with things at the level of patches, you may want to look at darcs - it considers a repository to be a set of patches, and thus cherry picking becomes the fundamental operation. However this has its own set of problems, such as being very slow :)