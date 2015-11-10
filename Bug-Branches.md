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

When the bug number is present in the pull request's title, JIRA will automatically switch the status of the bug to **"Code Review"**. Thus, creating a pull request like `UT-380: Description of Bug` will cause bug number `UT-380` on JIRA to be updated. The same happens for two or more bugs listed in the title of the pull request.

***

##### Resuming work on a Bug Branch

If your pull request was closed (not merged), you should be notified by the Build Master with a reason why your pull request was closed, and suggestions on how to fix it. When you're ready to resume work on the bug branch, follow these steps:

1. In your GitHub GUI, switch to your existing `bug-[bug number]` branch
2. Make the necessary modifications
3. When work is complete:
 1. Create a pull request to have `bug-[bug number]` merged into `release`
 2. The title of the pull request should be formatted like "UT-380: Description of Bug"
 3. If the pull request fixes two or more bugs at once, the title of the pull request should be formatted like "UT-380 UT-385: Description of the Bug"

***

## Build Master
If you're the assigned Build Master, the following steps should be taken to review the code available in the pull request, and decide a course of action from there.

##### Reviewing a Bug Branch _pull request_
- Ensure it's clean (doesn't merge other developers' unrelated commits). If it's not, ask the developer who created the pull request to update their branch and re-submit the pull request
- Ensure that unnecessary changes to the codebase aren't being made (e.g. hard-coding variable values when they already exist in the database)
- Rename pull request title to "[Bug-Number]: Description of pull request" if it's formatted incorrectly

##### Closing a Bug Branch _pull request_
- Close the pull request using button on github.com's pull request page
- Notify the developer that the pull request was closed, with reason, and suggestions to re-open the request
- Comment on pull request so that status in JIRA gets updated to "Failed Code Review" **(can this be automated?)**

##### Merging a Bug Branch _pull request_
- Merge the pull request using button on github.com's pull request page
- Comment on pull request so that the status in JIRA gets updated to "Passed Code Review" **(can this be automated?)**

##### Deploying a Bug Branch _pull request_
- Follow instructions in [[Deploying Branches to the Development Server]]
- Comment on pull request so that the status in JIRA gets updated to "Release1 QA Ready" **(can this be automated?)**