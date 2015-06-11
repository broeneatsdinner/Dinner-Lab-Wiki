## Working with Hotfix Branches
### Note: this version was written before we started using pull-requests. We should move into that methodology as we progress with our GitHub skillz.

---

##### Creating a Hotfix
Boop boop boop, notes here.

1. In your GitHub GUI, switch to the `master` branch.
2. Create a new branch off of `master `, called `hotfix-bug-123` (If you don't know the bug#, call your branch hotfix-something-descriptive)
3. Work on that hotfix, and when it’s done, merge `hotfix-bug-123` back into `master`
4. Sync your local `master` branch with the origin `master`
4. Pull `master` onto the **dub1** server
5. Test your hotfix (or get your hotfix tested) on dub1 @ dinnerlab.com
6. If OK'd, merge your hotfix branch into `develop`
7. Delete your hotfix branch

The point of this is to get your hotfix into master and onto the dub1 server as fast as possible. To prevent the bug from exposing itself (eww) in the future, your hotfix must be merged into _both_ the `master` branch and also the `develop` branch once approved.

The above being said, in your GitHub GUI, you know the little area that’s a dropdown to switch branches? Immediately to the left of that is an icon that lets you create a new branch. For hotfixes, just make sure you're working off of `master` branch first.