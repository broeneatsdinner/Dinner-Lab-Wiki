#### Permanent Branches
##### Always there, so how do you use them?

## **Develop** `develop`
The base branch from which to start all work on new "features" (i.e. new projects). The `develop` branch is never tested by QA.
- Resides on: localhost and <a href="https://dev1.dinnerlab.com" target="_blank">dev1.dinnerlab.com</a>
- Points to: `dinnerlab_development` database
- "Big Red Button" points to: "development" environment


## **Release** `release`
Updated from `develop` every Monday at 10:00 central time, pending a set of approved features that took place on `develop` the previous week.

If bugs are reported on JIRA, the bugfixes that take place should be branched from the `release` branch. When work on a bugfix branch is complete, a pull request should be made to have that bugfix branch merged into `release`. The `release` branch is then tested by QA on release1.dinnerlab.com.
- Resides on: localhost and <a href="https://release1.dinnerlab.com" target="_blank">release1.dinnerlab.com</a>
- Points to: `dinnerlab_development` database
- "Big Red Button" points to: "development" environment

## **Master** `master`
Updated from `release` every Tuesday at 10:00 central time, pending a set of QA tested & approved bugfixes that took place on `release` the previous week. When the `master` branch is updated from the `release` branch, the "trickle-down effect" occurs.
- Resides on: localhost and <a href="https://dinnerlab.com" target="_blank">dinnerlab.com</a>
- Points to: `dinnerlab_production` database
- "Big Red Button" points to: "production" environment

***

#### Temporary Branches
##### Prefixes to use when starting new work.

### **Feature** `feature-`
Used for specific feature (i.e. new project) work. Branches from `develop` and pull requests should be made to merge the `feature-` branch back into `develop`.

### **Bugfix** `bug-`
Used for fixing bugs found on the `release` branch. Branches from `release` and pull requests should be made to merge the `bug-` branch back into `release`.

### **Hotfix** `hotfix-`
Used only in extreme circumstances (i.e. the production site is unreachable or a portion of the production site is broken enough to cause data-loss to a widespread number of users) for hotfixes found on the `master` branch. Branches from `master` and pull requests should be made to merge the `hotfix-` branch back into `master`.

***

#### The "trickle-down" Effect
##### Sounds weird, but really useful!

- When bugfixes pass QA testing on the `release` branch:
 1. the `release` branch is then merged into `master` and 
 2. the `release` branch is also merged into `develop`

- When hotfixes are made on the `master` branch:
 1. the `master` branch is then merged into `release` and 
 2. the `release` branch is also merged into `develop`

The result of the above is that both bugfixes and hotfixes, once working, are applied to all "permanent" branches, and _hopefully_ won't rear their ugly heads again in the future. 

***

#### Cheatsheet
Created from `develop` and merged back into `develop`
- `feature-`

Created from `release` and merged back into `release`
- `bug-`

Created from `master` and merged back into `master`
- `hotfix-`