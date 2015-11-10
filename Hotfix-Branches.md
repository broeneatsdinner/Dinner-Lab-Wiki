## Working with Hotfix Branches

When a hotfix gets reported, it means something has gone terribly _terribly_ wrong and all developers should stop work before the end of the world comes around and the internets crush __everyone__. As the phones ring and Slack messages get sent, __someone__ will be assigned the task of fixing this critical error. If you're that lucky someone, follow these steps.

***

##### Creating a Hotfix

1. In your GitHub GUI, switch to the `master` branch.
2. Create a new branch off of `master `, called `hotfix-[bug number]`
  - If you don't know the bug number, call your branch `hotfix-[something-descriptive]`
  - Otherwise, if the hotfix is UT-901, then a branch called `hotfix-ut-901` works great
3. Work on that hotfix
4. When work is complete:
  - Create a pull request to have `hotfix-[bug number]` merged into `master`
  - The title of the pull request should be formatted like "UT-901: Description of Hotfix"

The point of this is to get your hotfix into master and onto the dinnerlab.com server as fast as possible.

To prevent the hotfix from exposing itself in the future, and you're the Build Master for this, further steps must be taken. Please see the "Build Master" section below.

***

##### Behind the Scenes

When the bug number is present in the pull request's title, JIRA will automatically switch the status of the bug to **"Code Review"**. Thus, creating a pull request like `UT-901: Description of Bug` will cause bug number `UT-901` on JIRA to be updated. The same happens for two or more bugs listed in the title of the pull request.

***

## Build Master
If you're the assigned Build Master, the following steps should be taken to review the code available in the pull request, and decide a course of action from there.

##### Reviewing a Hotfix Branch _pull request_
- Ensure it's clean (doesn't merge other developers' unrelated commits). If it's not, ask the developer who created the pull request to update their branch and re-submit the pull request
- Ensure that unnecessary changes to the codebase aren't being made (e.g. hard-coding variable values when they already exist in the database)
- Rename pull request title to "[Bug-Number]: Description of pull request" if it's formatted incorrectly

##### Closing a Hotfix Branch _pull request_
- Close the pull request using button on github.com's pull request page
- Notify the developer that the pull request was closed, with reason, and suggestions to re-open the request
- Comment on pull request so that status in JIRA gets updated to "Failed Code Review" **(can this be automated?)**

##### Merging a Hotfix Branch _pull request_
- Merge the pull request using button on github.com's pull request page
- Comment on pull request so that the status in JIRA gets updated to "Passed Code Review" **(can this be automated?)**

##### Deploying a Hotfix Branch _pull request_
- Follow instructions in [[Deploying Branches to the Production Server]]
- Comment on pull request so that the status in JIRA gets updated to "Deployed to Master" **(can this be automated?)**
- Start the "trickle-down" effect at step "Merging `master` into `release`" found on [Command Line Mastery](#merging-master-into-release)

