## Working with Bug Branches

When a bug gets reported by QA, it means something has been checked on `release1.dinnerlab.com` and it did not function as expected. QA logs that bug in JIRA, and it is assigned a bug number.

If you're up to the task at hand, and are filled with pride at earning gold stars, you can create a `bug-*` branch, come to the rescue, and show off your bug smashing skillz.

***

##### Creating a Bug Branch

1. In your GitHub GUI, switch to the `release` branch
2. Create a new branch off of `release `, called `bug-[bug number]`
  - For example, if the bug is UT-380, then a branch called `bug-ut-380` works great
3. Work on that bug
4. When you feel that work is complete:
  - Create a pull request to have `bug-[bug number]` merged into `release`
  - The title of the pull request should be formatted like "UT-380: Description of Bug"
  - If the pull request fixes two or more bugs at once, the title of the pull request should be formatted like "UT-380 UT-385: Description of the Bug"

The above being said, in your GitHub GUI, you know the little area that’s a dropdown to switch branches? Immediately to the left of that is an icon that lets you create a new branch off of the current branch. For bug fixes, just make sure you're working off of `release` branch first.

***

##### Behind the Scenes

When the bug number is present in the pull request's title, JIRA will automatically switch the status of the bug to **"Under Code Review"**. Thus, creating a pull request like `UT-380: Description of Bug` will cause bug number `UT-380` on JIRA to be updated. The same happens for two or more bugs listed in the title of the pull request.

***

##### Resuming work on a Bug Branch

1. In your GitHub GUI, switch to the `release` branch
2. Create a new branch off of `release `, called `bug-[bug number]`
  - For example, if the bug is UT-380, then a branch called `bug-ut-380` works great
3. Work on that bug
4. When you feel that work is complete:
  - Create a pull request to have `bug-[bug number]` merged into `release`
  - The title of the pull request should be formatted like "UT-380: Description of Bug"
  - If the pull request fixes two or more bugs at once, the title of the pull request should be formatted like "UT-380 UT-385: Description of the Bug"

The above being said, in your GitHub GUI, you know the little area that’s a dropdown to switch branches? Immediately to the left of that is an icon that lets you create a new branch off of the current branch. For bug fixes, just make sure you're working off of `release` branch first.

***

##### Merging a Bug Branch
So when you're ready to merge your feature branch into the develop branch:

1. In the GitHub GUI, switch to `develop` branch
2. Click on the “Branches” pill,  (Changes | History | Branches)
3, Click on “Merge View” to see the merge view
4. Drag your-feature-branch into the left side of the merge view, and `develop` branch into the right side (merging `your-feature-branch` into —> `develop`)
5. Click “Merge Branches”
6. Click on the Sync icon to sync your local `develop` with the origin `develop`
7. Pull `develop` onto dev1 @ dev1.dinnerlab.com