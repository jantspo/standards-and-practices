# Branch Conventions for Git

### Features

* Each repo should be split up as follows:
    1. Create labels for your features
        *  Name format will be `feature-component` (think of it as overall purpose vs. piece of the whole)

    2. Create branches for your features
        *  Name format will be `feature-component` (think of it as overall purpose vs. piece of the whole)
            > Interesting Point: Every label name will have a branch name and vise-versa

    3. Create issues for specific need for each feature
        * Add the feature label to the issue
        * From the appropriate feature _branch_, you will create a branch for **each issue**
        * Each issue branch name will follow the convention: **issue-#**

    4. Create a Pull Request
        * Create a PR from your issue branch to feature branch
        * Tag your team member/s in your PRs to review

### Issues/Bugfixes

* If you have an issue that is _not_ connected to a feature (such as a bugfix on an app that is already in production) you will:
    1. Create a branch from development/dev following the issue branch naming convention above
    2. Push all work to that branch and open a PR from your issue branch to development
    3. Tag your fellow developer in your PRs to review
    > Interesting Point: when you work on issue branches, **always** run `git pull origin [feature/development]` on your issue branch before your final push before creating your Pull Request


# Git/Github Workflow Conventions

## The following are conventions to be adopted in order to streamline our repositories and workflow processes:

### At the beginning of each project:
1. Create 3 branches:
    * Production (master)
    * Staging (sandbox)
    * Development (local)


### Once your project is created:

1. Create an issue for _every_ feature, bugfix, client request/requirement
    * Stick to the naming conventions above for all branches
2. Create new Github Projects weekly or monthly to keep track of progress (refer to this in meetings to explain progress)
    * Add all issues to this project that you want to get done this week or make progress on this week
    * If you don't finish this week, you can "roll" the issue to the next week's project
3. Use Milestones for all features, and add all feature issues to these Milestone (adding feature label to the issue).
    > Interesting Point: Every feature issue will be tied to a milestone AND a project

#### Maintainance:

1. Issues:

    * Creation:
        1. Always add the proper feature label, Github Milestone, and Github Project to your issues
        2. During team meetings (TBS), team will create the issues together
        3. Throughout the week, each member will assign him/herself to issues they need to work on unless team leader has assigned you an issue already
        4. Team members will be responsible for moving their issue cards through the Github Project columns, with the exception of QA moving the issue from `Testing` to `Approved by QA`

    * Testing: Once your issue is ready for a Pull Request:
        1. Developer will create a Pull Request and tag their team member/s
        2. Once the PR is approved and merged, the developer will:
            * Mark the issue with `Ready for Testing` label
            * Move the issue card from `In Progress` to `Testing` in the Github Project
        3. If QA finds issues while testing, they will:
            * Leave the current issue open
            * Create an issue and add `feature-component` label to it
            > Developer will create a branch from feature/development and follow the merging workflow (issue to feature to development to staging)


2. Branches:

    * Administrative Time:
        1. Developers should block off 15 minutes of time (first thing) Monday or (last thing) Friday to:
            * Delete local branches that have been closed
            * Update your Projects with current work if you haven't already
            * Add Issues created throughout the previous week to their proper Github Project

    * High-level Branch Conventions
        1. Always have 3 branches:
            * Master(production)
            * Staging(sandbox)
            * Development(local)
        2. Master is always live site, **DO NOT TOUCH** until ready for launch. Only the Project Lead should touch this branch.
        3. Staging is hosted on your sandbox server, and is for QA testing and has staging-specific settings/env files, etc.
        4. Development is your local copy for work-in-progress. It should be settings-agnostic, and should be merged to staging and _separately_ merged to production.
             > Interesting Point: DO NOT `git pull origin development` from master branch in order to merge them. CREATE A PR.

    * Merging
        **Open to Suggestions:**
        1. Issue to Feature
            * Once developer has finished an issue branch, they will follow the instructions described in the Features section of this document
        
        2. Feature to Development
            * Once each week developer will open a Pull Request from feature branch to development and tag another team member _and_ the Project Lead

        3. Development to Staging
            **At least once a week, if not more often**

            * Once developer(s) have implemented a feature or fixed an issue that is ready for QA:
                1. Developer will follow the steps to merge their issue or feature branch into Development
                2. Developer will open a Pull Request between Development into Staging and tag their team member/s
                3. Team member will review the changes and approve the Pull Request
                4. Developer will close the Pull Request and deploy the code to the staging server
        
        4. Staging to Master
            > Depending on whether this is a new product or a v2

            * Once each week the Project Lead will merge the Staging branch into the Master branch to keep both updated, assuming there are changes
            * Project Lead will create the Pull Request, tag another team member to review it, and close it when they get the go-ahead


3. Proposals:
    * Change the README.md every time you create a new branch and state the purpose of the branch there (to let others know which branch has latest code)
        > Expect CONFLICT in the Pull Request for README.md OR change the readme back to original before your Pull Request
