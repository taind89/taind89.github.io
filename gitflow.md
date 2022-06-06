# Gitflow

## I. Overview
[![gitflow](https://wac-cdn.atlassian.com/dam/jcr:cc0b526e-adb7-4d45-874e-9bcea9898b4a/04%20Hotfix%20branches.svg?cdnVersion=372 "gitflow")](https://wac-cdn.atlassian.com/dam/jcr:cc0b526e-adb7-4d45-874e-9bcea9898b4a/04%20Hotfix%20branches.svg?cdnVersion=372 "gitflow")

**5 branch types of Gitflow**
* `master`
* `develop`
* `feature`
* `release`
* `hotfix`

## II. Branches
### 1. Master Branch
The `master` branch stores the official release history. It's also convenient to tag all commits in the `master` branch with a version number.

### 2. Develop Branch
The `develop` branch serves as an integration branch for features.

### 3. Feature Branches
To be created from the `develop` branch.

When a feature is completed, it gets merged back into `develop`. Features should never interact directly with `master`.

`feature` branches are generally created off to the latest `develop` branch.

### 4. Release Branches
To be created from the `develop` branch.

No new features can be added after this point—only bug fixes, documentation generation, and other release-oriented tasks should go in this branch.

Once it's ready to ship, the `release` branch will be:

* merged into `master`
* tagged with a version number (the Client does this)
* merged back into `develop`

### 5. Hotfix Branches
To be created from the `master` branch.

As soon as the fix is complete, it should be merged into both `master` and `develop`, and `master` should be tagged with an updated version number.

## III. Naming Conventions
**Main Branches**
* Master Branch: `master`
* Develop Branch: `develop`

**Supporting Branches**
* Feature Branches: `feature/branch_name (e.g. feature/facebook_login)`
* Release Branches: `release/x.y.z` (x is the `major` version; y is `sprint` number; z is the patch` version)
* Hotfix Branches: `hotfix/branch_name (e.g. hotfix/change_color_button)`

**Rules**
* Use `snake_case`
* Use `/` as a delimiter after the prefix
* Version numbers must follow [Semantic Versioning](https://semver.org/)

## IV. Pull Requests
All features, hotfixes, releases must be reviewed and merged to main branches by pull requests.

After merging, those branches will be deleted by the reviewer.

## V. Deployment and Environments
* Once a `feature` branch is merged into `develop` -> deploy the code onto DEV Environment (Trigger)
* Whenever a `release` branch is created OR any new commit is put into `release` -> deploy the code onto STG Environment (Trigger)
* Only `master` branch is used for deploying onto PRD Environment. The commit MUST be tagged version before deploying. Only CM or the Client is in charge.

## VI. Summary
The overall flow of Gitflow is:

1. A `develop` branch is created from `master`
1. A `release` branch is created from `develop`
1. `feature` branches are created from `develop`
1. When a `feature` is complete it is merged into the `develop` branch
1. When the `release` branch is done it is merged into `develop` and `master`
1. If an issue in `master` is detected a `hotfix` branch is created from `master`
1. Once the `hotfix` is complete it is merged to both `develop` and `master`

## VII. References
* [Tutorials Gitflow Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)
* [A successful Git branching model » nvie.com](http://nvie.com/posts/a-successful-git-branching-model/)
* [Using git-flow to automate your git branching workflow](https://jeffkreeftmeijer.com/git-flow/)
