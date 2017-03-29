# Git Flow

## Overview
![GitFlow Diagram](/images/git-flow.png)
Format: ![Alt Text](url)
Git flow is a work pattern designed around maintaining code integrity on larger projects. Stable code is kept separate
from development code until bugs and issues are worked out. 

A project will typically have 1 development branch that will contain all stable, if not yet fully bug tested features.
As developers add new features or fix bugs they will create a new branch from the development base and work on feature 
the branch was created for. Once that feature is finished the branch is pushed up to the repo and a pull request is created.
After being code reviewed and tested that branch can be merged into development. If there are any conflicts with development
then the conflicts are resolved.
 
From there other members of the development team can merge the development changes into their own working branches to prevent 
possible future conflicts or to have access to the new feature if needed.

## Branches

Git flow is based around using repo branches to create a separation of concern for code sets. Branches could generally be
grouped as stable releases, hotfixes, new features, and bugs fixes. 

### Stable Releases
#### Master
The master branch should be the least changed branch and most stable branch in a repo. Changes should be merged into master
only have extensive testing nad before deployment to production.  

#### Staging
A staging branch can be used for when a new release is still being worked on but currently implemented changes need to be tested
or showcased on a sandbox website. This branch should, in most cases be ready or very close to ready, for merging into master 
for production deployment.

#### Development
The development branch is the "base" from which all feature branches are branched off of.
It should be stable, relatively bug free, and demo ready.

#### Features
Features branches are where the vast majority of coding happens. Feature branches should be focused specifically on a single feature, 
ie, user login, and when it is completed and tested the branch should be pushed up and a pull request created with the development branch as
the target. Another member of the team should then review the code and test that it works correctly before merging into development.


#### Bug Fixes/ Hotfixes
Branches created to fix specific bugs. Bug fixes are typical bugs found during development cycles and fall into the normal work 
patterns.

Hotfixes are issues and bugs affecting live/production code that require immediate attention and after testing are pushed directly
as soon as they are fixed.

## Branch Naming - TBD
