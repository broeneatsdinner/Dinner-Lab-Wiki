## Working with Bug Branches

When a bug gets reported by QA, it means something has been checked on `release1.dinnerlab.com` and it did not function as expected. QA logs that bug in JIRA, and it is assigned a bug number.

If you're up to the task at hand, and are filled with pride at earning gold stars, you can create a `bug-*` branch, come to the rescue, and show off your bug smashing skillz.

---

##### Creating a Bug Branch

1. In your GitHub GUI, switch to the `release` branch.
2. Create a new branch off of `release `, called `bug-[bug number]` (for example, if the bug is UT-380, then `bug-ut-380` works great)
3. Work on that bug, and when it's done, merge `bug-[bug number]` back into `develop`
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