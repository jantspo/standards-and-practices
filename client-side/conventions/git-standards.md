# Branch Conventions for Git

### Features 

* Each repo should be split up as follows: 
    1. Create labels for your features 
        *  Name format will be `feature-component` (think of it as overall purpose vs. piece of the whole)

    2. Create branches for your features
        *  Name format will be `feature-component` (think of it as overall purpose vs. piece of the whole)
            > Interesting Point: Every label name will have a branch name and vise-versa

    3. Create issues for specific needs for each feature
        * Add the feature label to the issue
        * From the appropriate feature/label _branch_, you will create a branch for each issue 
        * Each issue branch name will follow the convention: **issue-#**

 ### Issues/Bugfixes

* If you have an issue that is _not_ connected to a feature (such as a bugfix on an app that is already in production) you will:
    1. Create a branch from development/dev following the issue branch naming convention above
    2. Push all work to that branch and open a PR from your issue branch to development
    3. Tag your senior developer in your PRs to review


# Git/Github Workflow Conventions

## The following are conventions to be adopted in order to streamline our repositories and workflow processes:

### At the beginning of each project:
1. Create 3 branches:
    * Production (master)
    * Staging (sandbox) 
    * Development (local)
2. Create your .gitignore file and add `.env` to it
3. Create a .env file for each of your environments (production, staging, and local) when appropriate on each respective server
    > Interesting Point: when you work on issue branches, **always** run `git pull origin [feature/development]` on your issue branch before your final push before creating your Pull Request


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
        3. Throughout the week, each member will assign his/herself to issues they need to work on unless team leader has assigned you an issue already
        4. Team members will be responsible for moving thier issue cards through the Github Project columns, with the exception of QA moving the issue from `Testing` to `Approved by QA`

    * Testing: Once your issue is ready for a Pull Request:
        1. Developer will create a Pull Request and tag their Project Lead
        2. Once the Project Lead approves the changes, the developer will:
            * Close the issue
            * Move the issue card from `testing` to `done` in the Github Project
            * Close the PR
            * Delete the Github branch
                
                
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
        4. Development is your local copy for work-in-progress. It should be settings-agnostic, and should be merged to staging and _separately_ merged to production (so as to keep the envs separate).
             > Interesting Point: DO NOT `git pull origin development` from master in order to merge them. CREATE A PR.

    * Merging 
        **Open to Suggestions:** 
        1. Staging to Master
            > Depending on whether this is a new product or a v2
                
            * Once each week the Project Lead will merge the Staging branch into the Master branch to keep both updated, assuming there are changes
            * Project Lead will create the Pull Request, tag another team member to review it, and close it when they get the go-ahead

        2. Development to Staging
            **At least once a week, if not more often**

            * Once developer(s) have implemented a feature or fixed an issue that is ready for QA:
                1. Developer will follow the steps to merge their issue or feature branch into Development
                2. Developer will open a Pull Request between Development into Staging and tag their Project Lead
                3. Project Lead will review the changes and approve the Pull Request
                4. Developer will close the Pull Request and deploy the code to the staging server
        
        3. Feature to Development
            
            * Developer will open a Pull Request and tag another team member _and_ the Project Lead
            * Once the Pull Request is approved, the developer will close the issue and delete the Github branch

        4. Issue to Feature
            * Once developer has finished an issue branch, they will follow the instructions described in the Issues section of this document
            * The developer will be responsible for deploying the approved code to the staging server

        5. Issue to Staging
            * If QA has opened a bugfix issue, developers may branch directly off of staging in order to address it. 
            * Once the developer has implmented all bugfixes and is ready for testing, developer will open a Pull Request between their issue branch and the staging branch and tag another developer or Project Lead for review.
            * After review, close the Pull Request and let QA know the fix is ready for testing. 
            * After QA approves the fix, QA will close the issue and delete the Github branch associated with it.

      

    3. Proposals: 
        * Change the README.md every time you create a new branch and state the purpose of the branch there.
            > Expect CONFLICT in the Pull Request for README.md OR change the readme back to original before your Pull Request
