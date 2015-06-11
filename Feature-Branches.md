## Working with Feature Branches
### Note: this version was written before we started using pull-requests. We should move into that methodology as we progress with our GitHub skillz.

##### Creating a Feature Branch
Boop boop boop, notes here.

1. In your GitHub GUI, switch to the `develop` branch.
2. Create a new branch off of `develop`, called `your-feature-branch` (you choose!)
3. Work on that feature, and when it’s done, merge `your-feature-branch` back into `develop`
4. Sync your local `develop` branch with the origin `develop`
4. Pull `develop` onto the **dev1** server
5. Test your feature (or get your feature tested) on dev1 @ dev1.dinnerlab.com
6. If OK'd, merge your feature branch into `master`
7. Delete your feature branch

The above being said, in your GitHub GUI, you know the little area that’s a dropdown to switch branches? Immediately to the left of that is an icon that lets you create a new feature branch. For features, just make sure you're working off of `develop` branch first.

---

##### Merging a Feature Branch
So when you're ready to merge your feature branch into the develop branch:

1. In the GitHub GUI, switch to `develop` branch
2. Click on the “Branches” pill,  (Changes | History | Branches)
3, Click on “Merge View” to see the merge view
4. Drag your-feature-branch into the left side of the merge view, and `develop` branch into the right side (merging `your-feature-branch` into —> `develop`)
5. Click “Merge Branches”
6. Click on the Sync icon to sync your local `develop` with the origin `develop`
7. Pull `develop` onto dev1 @ dev1.dinnerlab.com