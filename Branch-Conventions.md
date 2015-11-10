#### Permanent Branches
##### Always there, so how do you use them?

**Develop** `develop`
The base branch from which to start all work on new "features" (i.e. new projects). The `develop` branch is never tested by QA.
- Resides on: localhost and dev1.dinnerlab.com
- Points to: `dinnerlab_development` database
- "Big Red Button" points to: "development" environment


**Release** `release`
If bugs are reported on JIRA, the bugfixes that take place should be branched from the `release` branch. When work on a bugfix branch is complete, a pull request should be made to have that bugfix branch merged into `release`. The `release` branch is then tested by QA on release1.dinnerlab.com. The `release` branch is merged into master every Tuesday at 10:00 central time, and the "trickle-down effect" then occurs.
- Resides on: localhost and release1.dinnerlab.com
- Points to: `dinnerlab_development` database
- "Big Red Button" points to: "development" environment

**Master** `master`
branched off of develop and merged into master every Tuesday at 10:00 central time. If bugfixes that are reported on the `release-` branch take place, they're branched from `release-` and merged back into `release-`. `release-` is then merged into master, and back into develop.
- Resides on: localhost and dinnerlab.com
- Points to: `dinnerlab_production` database
- "Big Red Button" points to: "production" environment


---

#### Temporary Branches
##### Prefixes to use when starting new work.

**Feature** `feature-`
Used for specific feature (i.e. new project) work. Branches from `develop` and pull requests should be made to merge the `feature-` branch back into `develop`.

**Bugfix** `bug-`
Used for fixing bugs found on the `release` branch. Branches from `release` and pull requests should be made to merge the `bug-` branch back into `release`.

**Hotfix** `hotfix-`
Used only in extreme circumstances (i.e. the production site is unreachable or a portion of the production site is broken enough to cause data-loss to a widespread number of users) for hotfixes found on the `master` branch. Branches from `master` and pull requests should be made to merge the `hotfix-` branch back into `master`.

---

Created from `develop` and merged back into `develop`
- `feature-`

Created from `release` and merged back into `release`
- `bug-`

Created from `master` and merged back into `master`
- `hotfix-`