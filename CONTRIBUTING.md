# Contributor's Guide

We welcome pull requests from anyone in the world. Follow these steps to contribute:

1. Find an issue that needs assistance by searching for the [Help Wanted](https://github.com/DemocracyEarth/sovereign/labels/help%20wanted) tag.

2. Let us know you are working on it by posting a comment on the issue.

3. Follow the [Contribution Guidelines](#contribution-guidelines) to start working on the issue.

Remember to feel free to ask for help in our [Sovereign](https://gitter.im/DemocracyEarth/sovereign) Gitter room.

###### If you've found a bug that is not on the board, [follow these steps](#found-a-bug).

--------------------------------------------------------------------------------

## Contribution Guidelines

- [Prerequisites](#prerequisites)
- [Forking The Project](#forking-the-project)
- [Create A Branch](#create-a-branch)
- [Setup Linting](#setup-linting)
- [Setup Sovereign](#setup-sovereign)
- [Make Changes](#make-changes)
- [Run The Test Suite](#run-the-test-suite)
- [Squash Your Commits](#squash-your-commits)
- [Creating A Pull Request](#creating-a-pull-request)
- [Common Steps](#common-steps)
- [How We Review and Merge Pull Requests](#how-we-review-and-merge-pull-requests)
- [How We Close Stale Issues](#how-we-close-stale-issues)
- [Next Steps](#next-steps)
- [Other resources](#other-resources)

### Prerequisites

On Linux & MacOS, load a terminal and type:

```sh
$ curl https://install.meteor.com/ | sh
```

This will setup [Meteor](http://github.com/meteor/meteor) (including [Node](https://github.com/nodejs/node) and [Mongo](https://github.com/mongodb/mongo) if necessary).

> _Note:_ Windows users must [download installer](https://www.meteor.com/install).


### Forking The Project

#### Setting Up Your System

1. Install [Git](https://git-scm.com/) or your favorite Git client.
2. (Optional) [Setup an SSH Key](https://help.github.com/articles/generating-an-ssh-key/) for GitHub.
3. Create a parent projects directory on your system. For this guide, it will be assumed that it is `/mean/`

#### Forking Sovereign

1. Go to the top level Sovereign repository: <https://github.com/DemocracyEarth/sovereign>
2. Click the "Fork" Button in the upper right hand corner of the interface ([More Details Here](https://help.github.com/articles/fork-a-repo/))
3. After the repository has been forked, you will be taken to your copy of the sovereign repo at `yourUsername/sovereign`

#### Cloning Your Fork

1. Open a Terminal / Command Line / Bash Shell in your projects directory (_i.e.: `/yourprojectdirectory/`_)
2. Clone your fork of sovereign

```shell
$ git clone https://github.com/yourUsername/sovereign.git
```

##### (make sure to replace `yourUsername` with your GitHub Username)

This will download the entire sovereign repo to your projects directory.

#### Setup Your Upstream

1. Change directory to the new sovereign directory (`cd sovereign`)
2. Add a remote to the official sovereign repo:

```shell
$ git remote add upstream https://github.com/DemocracyEarth/sovereign.git
```

Congratulations, you now have a local copy of the sovereign repo!

#### Maintaining Your Fork

Now that you have a copy of your fork, there is work you will need to do to keep it current.

##### **Rebasing from Upstream**

Do this prior to every time you create a branch for a PR:

1. Make sure you are on the `staging` branch

  > ```shell
  > $ git status
  > On branch staging
  > Your branch is up-to-date with 'origin/staging'.
  > ```

  > If your aren't on `staging`, resolve outstanding files / commits and checkout the `staging` branch

  > ```shell
  > $ git checkout staging
  > ```

2. Do A Pull with Rebase Against `upstream`

  > ```shell
  > $ git pull --rebase upstream staging
  > ```

  > This will pull down all of the changes to the official staging branch, without making an additional commit in your local repo.

3. (_Optional_) Force push your updated staging branch to your GitHub fork

  > ```shell
  > $ git push origin staging --force
  > ```

  > This will overwrite the staging branch of your fork.

### Create A Branch

Before you start working, you will need to create a separate branch specific to the issue / feature / project you're working on. You will push your work to this branch.

#### Naming Your Branch

Name the branch something like `fix-#-desc` where `#` is the issue number and `desc` is a short description of the issue that you are attempting to fix, no more than 20 chars.

If you are working base on [project topics](https://github.com/DemocracyEarth/sovereign/projects), Name the branch something like `feat-#-desc`, `impr-#-desc`, `prj-#-desc` where `#` is the issue number and `desc` is a short description of the issue that you are attempting to fix, no more than 20 chars.

For example `feat-5-edit-proposals` would be a branch where I will add a feature to edit proposals.

#### Adding Your Branch

To create a branch on your local machine (and switch to this branch):

```shell
$ git checkout -b [name_of_your_new_branch]
```

and to push to GitHub:

```shell
$ git push origin [name_of_your_new_branch]
```

##### If you need more help with branching, take a look at _[this](https://github.com/Kunena/Kunena-Forum/wiki/Create-a-new-branch-with-git-and-manage-branches)_.

### Setup Linting

You should have [ESLint running in your editor](https://guide.meteor.com/code-style.html#eslint-editor), and install all the dependencies with `meteor npm install` in sovereign folder.
It will highlight anything doesn't conform to [Airbnb styleguide](https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb).

For more information, read the [meteor style guide](https://guide.meteor.com/code-style.html#eslint) that also includes a link to [ESlint](http://eslint.org/docs/user-guide/getting-started).

> Please do not ignore any linting errors, as they are meant to **help** you and to ensure a clean and simple code base.

### Setup Sovereign
Once you have Sovereign cloned, before you start the application, you need to install all of the dependencies:

```bash
# Install NPM dependencies
meteor npm install
```

```bash
# Run the program
meteor npm run start:dev
```


Now navigate to your browser and open <http://localhost:3000>. If the app loads, congratulations – you're all set. Otherwise, let us know by asking in the [Sovereign Room](https://gitter.im/DemocracyEarth/sovereign) on Gitter. There also might be an error in the console of your browser or in Bash / Terminal / Command Line that will help identify the problem.

### Make Changes
This bit is up to you!

### Run The Test Suite
When your are ready to share your code, run the test suite:

```shell
$ meteor npm run test
$ meteor npm run test-app
```

and ensure all tests pass.

### Squash Your Commits
When you make a pull request, all of your changes need to be in one commit.

If you have made more then one commit, then you will need to _squash_ your commits.

To do this, see [Squashing Your Commits](http://forum.freecodecamp.com/t/how-to-squash-multiple-commits-into-one-with-git/13231).

### Creating A Pull Request

#### What is a Pull Request?

A pull request (PR) is a method of submitting proposed changes to the Sovereign Repo (or any Repo, for that matter). You will make changes to copies of the files which make up Sovereign in a personal fork, then apply to have them accepted by Sovereign proper.

#### Need Help?

Sovereign Issue Mods and staff are on hand to assist with Pull Request related issues on our Chat Room.

#### How to find the code in the Sovereign codebase to fix/edit?

The best way to find out any code you wish to change/add or remove is using
the GitHub search bar at the top of the repository page. For example, you could
search for a challenge name and the results will display all the files along
with line numbers. Then you can proceed to the files and verify this is the area
that you were looking forward to edit. Always feel free to reach out to the chat
room when you are not certain of any thing specific in the code.

#### Important: ALWAYS EDIT ON A BRANCH

Take away only one thing from this document, it should be this: Never, **EVER**
make edits to the `staging` branch. ALWAYS make a new branch BEFORE you edit
files. This is critical, because if your PR is not accepted, your copy of
staging will be forever sullied and the only way to fix it is to delete your
fork and re-fork.

#### Methods

There are two methods of creating a pull request for Sovereign:

-   Editing files via the GitHub Interface
-   Editing files on a local clone

##### Method 1: Editing via your Local Fork _(Recommended)_

This is the recommended method. Read about [How to Setup and Maintain a Local
Instance of Sovereign](#maintaining-your-fork).

1.  Perform the maintenance step of rebasing `staging`.
2.  Ensure you are on the `staging` branch using `git status`:

```bash
$ git status
On branch staging
Your branch is up-to-date with 'origin/staging'.

nothing to commit, working directory clean
```

1.  If you are not on staging or your working directory is not clean, resolve
    any outstanding files/commits and checkout staging `git checkout staging`

2.  Create a branch off of `staging` with git: `git checkout -B
    branch/name-here` **Note:** Branch naming is important. Use a name like
    `fix-#-short-fix-description` or `feat-#-short-feature-description`. Review
     the [Contribution Guidelines](#contribution-guidelines) for more detail.

3.  Edit your file(s) locally with the editor of your choice

4.  Check your `git status` to see unstaged files.

5.  Add your edited files: `git add path/to/filename.ext` You can also do: `git
    add .` to add all unstaged files. Take care, though, because you can
    accidentally add files you don't want added. Review your `git status` first.

6.  Commit your edits: `git commit -m "Brief Description of Commit"`

7.  Squash your commits, if there are more than one.

8.  Push your commits to your GitHub Fork: `git push -u origin branch/name-here`

9.  Go to [Common Steps](#common-steps)

##### Method 2: Editing via the GitHub Interface

Note: Editing via the GitHub Interface is not recommended, since it is not
possible to update your fork via GitHub's interface without deleting and
recreating your fork.

Read the [Wiki
article](http://forum.freecodecamp.com/t/how-to-make-a-pull-request-on-free-code-camp/19114)
for further information

### Common Steps

1.  Once the edits have been committed, you will be prompted to create a pull
    request on your fork's GitHub Page.

2.  By default, all pull requests should be against the Sovereign main repo, `staging`
    branch.

3.  Submit a [pull
    request](http://forum.freecodecamp.com/t/how-to-contribute-via-a-pull-request/19368)
    from your branch to Sovereign's `staging` branch.

4.  The title (also called the subject) of your PR should be descriptive of your
    changes and succinctly indicates what is being fixed.

    -   **Do not add the issue number in the PR title**.

    -   Examples: `Add Test Cases to Bonfire Drop It` `Correct typo in Waypoint
        Size Your Images`

5.  In the body of your PR include a more detailed summary of the changes you
    made and why.

    -   If the PR is meant to fix an existing bug/issue, then, at the end of
        your PR's description, append the keyword `closes` and #xxxx (where xxxx
        is the issue number). Example: `closes #1337`. This tells GitHub to
        close the existing issue, if the PR is merged.

6.  Indicate if you have tested on a local copy of the site or not.


### How We Review and Merge Pull Requests

Sovereign has a team of volunteer Issue Moderators. These Issue Moderators routinely go through open pull requests in a process called [Quality Assurance](https://en.wikipedia.org/wiki/Quality_assurance) (QA).

1. If an Issue Moderator QA's a pull request and confirms that the new code does what it is supposed without seeming to introduce any new bugs, they will comment "LGTM" which means "Looks good to me."

2. Another Issue Moderator will QA the same pull request. Once they have also confirmed that the new code does what it is supposed to without seeming to introduce any new bugs, they will merge the pull request.

If you would like to apply to join our Issue Moderator team - which is a Core Team position - message [@LucasIsasmendi](https://gitter.im/LucasIsasmendi) with links to 5 of your pull requests that have been accepted and 5 issues where you have helped someone else through commenting or QA'ing.


### How We Close Stale Issues

We will close any issues or pull requests that have been inactive for more than 30 days, except those that match the following criteria:
- bugs that are confirmed
- pull requests that are waiting on other pull requests to be merged
- features that are a part of a GitHub project

### Next Steps

#### If your PR is accepted

Once your PR is accepted, you may delete the branch you created to submit it.
This keeps your working fork clean.

You can do this with a press of a button on the GitHub PR interface. You can
delete the local copy of the branch with: `git branch -D branch/to-delete-name`

#### If your PR is rejected

Don't despair! You should receive solid feedback from the Issue Moderators as to
why it was rejected and what changes are needed.

Many Pull Requests, especially first Pull Requests, require correction or
updating. If you have used the GitHub interface to create your PR, you will need
to close your PR, create a new branch, and re-submit.

If you have a local copy of the repo, you can make the requested changes and
amend your commit with: `git commit --amend` This will update your existing
commit. When you push it to your fork you will need to do a force push to
overwrite your old commit: `git push --force`

Be sure to post in the PR conversation that you have made the requested changes.

### Other resources
