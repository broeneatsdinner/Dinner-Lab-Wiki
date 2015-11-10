## Working with Feature Branches

When a new project is ready to be kicked off, it all begins with a branch — a branch off of `develop`, that is!

***

##### Creating a Feature Branch

1. In your GitHub GUI, switch to the `develop` branch.
2. Create a new branch off of `develop`, called `feature-awesome` (you choose!)
3. Work on that feature
4. When you feel that work is complete: 
  - Create a pull request to have `feature-awesome` merged into `develop`
  - The title of the pull request should be formatted like "Feature: Description of your awesome feature"

The above being said, in your GitHub GUI, you know the little area that’s a dropdown to switch branches? Immediately to the left of that is an icon that lets you create a new branch off of the current branch. For features, just make sure you're working off of `develop` branch first.

***

## Build Master
If you're the assigned Build Master, the following steps should be taken to review the code available in the pull request, and decide a course of action from there.

##### Reviewing a Feature Branch _pull request_
- Ensure it's clean (doesn't merge other developers' unrelated commits). If it's not, ask the developer who created the pull request to update their branch and re-submit the pull request
- Ensure that unnecessary changes to the codebase aren't being made (e.g. hard-coding variable values when they already exist in the database)
- Rename pull request title to "[Bug-Number]: Description of pull request" if it's formatted incorrectly

##### Closing a Feature Branch _pull request_
- Close the pull request using button on github.com's pull request page
- Notify the developer that the pull request was closed, with reason, and suggestions to re-open the request
- Comment on pull request so that status in JIRA gets updated to "Failed Code Review" **(can this be automated?)**

##### Merging a Feature Branch _pull request_
- Merge the pull request using button on github.com's pull request page
- Comment on pull request so that the status in JIRA gets updated to "Passed Code Review" **(can this be automated?)**

##### Deploying a Feature Branch _pull request_
- Follow instructions in [[Deploying Branches to the Development Server]]
- Comment on pull request so that the status in JIRA gets updated to "Release1 QA Ready" **(can this be automated?)**