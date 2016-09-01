#Git Readme
>An introduction to how git and github are used by the uiowa robotics team.  This is not the only possible git workflow but by working this way we can ensure a highly functional code base where every team member can contribute without the risk of damaging the overall performace of the robot.

<hr>

#Table of Contents
* [Getting Started](#getting-started)
    - [Getting Git](#getting-git)
    - [Cloning the Repository](#cloning-the-repository)
    - [Getting Push Access](#getting-push-access)
    - [Repository Structure](#repository-structure)
        + [Branch Structure](#branch-structure)
        + [Code Structure](#code-structure)
* [General Workflow](#general-workflow)
    - [Adding a New Feature](#adding-a-new-feature)
    - [Sharing Your Feature](#sharing-your-feature)
    - [Keeping Your Feature Branch Up To Date](#keeping-your-feature-branch-up-to-date)
    - [Submitting Your Feature For Review](#submitting-your-feature-for-review)
    - [Reviewing a Feature](#reviewing-a-feature)
    - [Revising Your Feature](#revising-your-feature)
    - [Merging a Feature](#merging-a-feature)
* [Appendix](#appendix)
    - [How To Make Good Commits](#how-to-make-good-commits)
    - [Merge or Rebase](#merge-or-rebase)
    - [What To Do If Something Goes Wrong](#what-to-do-if-something-goes-wrong)


<hr>
#Getting Started
##Getting Git
* **Recomended:** [link](https://desktop.github.com)
    - Installs GUI and command line tools for OSX or Windows
* **OSX:** 
    - Included in Xcode

##Cloning the Repository
Create a new directory and clone the repository into it.
```bash
$ mkdir <location>
$ cd <location>
$ git clone https://github.com/zachthenerd169/uiowa-rmc.git
```

##Getting Push Access
Ask a senior developer to add you to the list of contributers. Without this you will not be about to edit the code in the repository.

##Repository Structure
###Branch Structure
The repository is divided into a single master branch, a single development branch, and many experimental branches.
* The **master branch** contains the code that is **guaranteed** to work on the robot.  This will generally have less features that the development branch but is considered the safest code to run.
* The **development branch** contains the code that has the **most features**, but has not been sufficiantly tested as a whole system to be guaranteed to function without error.
* The **experimental branches** contain code under development, and should differ from the development branch by only a **single feature**.  

###Code Structure
(Coming Soon)

<hr>
#General Workflow
##Adding a New Feature
Update your repository
```bash
$ git fetch origin
$ get checkout development
```

Create a new feature branch
```bash
$ git checkout -b <new-feature>
```

Edit Files
```bash
$ edit <file1> <file2> <file3>...
```

Add Files to Git ([How to Make Good Commits](#how-to-make-good-commits))
```bash
$ git add <file1> <file2> <file3>...
$ git commit
```

##Sharing Your Feature
Share Changes
```bash
$ git push origin
```

##Keeping Your Feature Branch Up To Date
Update your repository
```bash
$ git fetch origin
$ git checkout <new-feature>
```

Combine changes from development branch
```bash
$ git rebase development
```

Fix possible merge conflicts
```bash
$ edit <file1> <file2> <file3>...
$ git add <file1> <file2> <file3>...
$ git rebase --continue
```

##Submitting Your Feature For Review
Make sure that your feature branch is up to date with the development branch by following [these instructions](#keeping-your-branch-up-to-date)

Share your changes by following [these instructions](#sharing-your-feature)

Create a pull request on github
```
1. Navigate to your feature branch
2. Click the button labeled "New pull request"
3. Make sure that base is "development" and that compare is "<new-feature>"
4. Enter a tile and description for your pull request
5. Click "Create pull request"
```

##Reviewing a Feature
Once the pull request is created, others can make comments or suggestions on individual lines or the whole pull request.

Possible topics for comments
```
1. Praise (thanking the author for the new feature)
2. Possible errors
3. Style fixes
4. etc.
```

##Revising Your Feature
Checkout the feature branch
```bash
$ git fetch origin
$ git checkout <new-feature>
```

Make changes
```bash
$ edit <file1> <file2> <file3>...
```

Save changes
```bash
$ git commit
```

Share changes
```bash
$ git push origin
```

##Merging a Feature
>Note: Although not requred, it is heavily encouraged that the person who creates a pull request is different from the person who merges it.

Once the feature has been deemed finished, it can be merged with the development branch.

First make sure that your feature branch is up to date with the development branch by following [these instructions](#keeping-your-branch-up-to-date) and [these instructions](#sharing-your-feature).

Navigate to the pull request and click on either "Merge pull request" or "Confirm squash and merge".

Enter a commit message or accept the default message, and click "Confirm merge"

You can now delete the feature branch since the feature has been added to the development branch.

<hr>
#Appendix
##How To Make Good Commits
Each commit message should consist of two parts: the subject, and the body.  The subject of the commit message should be the first line of the message, contain a short summary of the changes, and generally be less than 50 characters long.  The body of the commit message is seperated from the subject by a blank line and contains an expanation of why the changes where made.

The subject of the message should be written in the imperative form, or in other words: say what the commit should do, not what it is doing, or what it did. (eg. "Clean up room", not "Cleaning up room", or "Cleaned up room")

The body of the message should avoid stating *how* a change was made and instead focus on *what* and *why* changes were made.  Good questions to answer in the message body are "Why is the change necessary?", "How does this change address the issue?", and "What side effects might this change have?"

Examples of good commit messages:
```
Resolve networking freezing error

Resolve error where network would freeze when receiving a message that ended
in \r\n instead of \n by parsing the message for carriage returns and removing them.

This may conflict with messages that contain \r but I don't see any
reason why a valid message would contain \r anyways. 
```

Some commits do not need bodys to explain what they do
```
Fix typos in user guide
```

##Merge or Rebase
The general rule of thumb for our workflow is that merge is used to integrate a child branch into a parent branch, and rebase is used to keep child branches up to date with their parent.

###Merge
Merging one branch into another creates copies of all the commits that are different on the other branch and applies them to your branch.  This is useful when merging an experimental branch with the development branch because the the changes are *applied* to the development branch.

###Rebase
Rebasing one branch on another *reapplies* all of the commits from your branch onto the HEAD of the other branch without creating any new commits.  This is useful when keeping an experimental branch up to date because it does not create anything new.

Rebase can also be used to squash multiple previous commits into single commits. This can be useful to tidy up the commit history of an experimental branch before merging it with the development branch.

##What To Do If Something Goes Wrong
> Note: if you are not comfortable fixing problems on your own, ask for help from a senior developer.  DO NOT ENTER COMMANDS IF YOU DON'T KNOW WHAT THEY DO! It is shockingly easy to corrupt the git repository or even erase it by carelessly entering commands.

(Coming Soon)
