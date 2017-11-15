# Contributor's Guide

The following is a set of guidelines for contributing to the project. Use your best judgment, and feel free to propose changes to this document in a pull request. 

- [Code of Conduct](./CODE_OF_CONDUCT.md)
- [Things You Can Work On](#things-you-can-work-on)
- [How Team Members Can Contribute?](#how-team-members-can-contribute)
- [How Non-Team Members Can Contribute?](#how-non-team-members-can-contribute)
- [Create a New Branch To Work On](#create-a-new-branch-to-work-on)
- [How To Commit Messages](#how-to-commit-messages)
- [Creating A Pull Request](#creating-a-pull-request)


## Things you can work on 
There is no specific restriction as such but the below pointers might help: 

1. first, you can look for any open issue labelled with '**help wanted**'. If you find one & would like to contribute, post a comment there declaring your intent to work on the solution.

2. second, if you would like to work on something that you think would add value to the product, create an issue for it. So you can get people into a discussion, get their feedback & get team's approval to work on this stuff.

In either case, make sure that you are not duplicating efforts. i.e. two people working on the same stuff.


## How team members can contribute?

### Clone The Project Repo

1. Open a Terminal / Command Line / Bash Shell in your projects directory (_i.e.: `/yourprojectdirectory/`_)
2. Clone expertonlive/expertonlive.com

```shell
$ git clone https://github.com/expertonlive/expertonlive.com.git
```

This will download the entire repo to your projects directory.

### Setup Your Origin

1. Change directory to the new expertonlive directory (`cd expertonlive`)
2. Add a remote to the official expertonlive repo:

```shell
$ git remote add origin https://github.com/expertonlive/expertonlive.git
```

Congratulations, you now have a local copy of the repo!

### Before you can start coding...

```bash
# 1. always go into the staging branch 
$ git checkout -b staging

# 2. update your local staging branch with that of remote,
$ git pull --rebase origin staging

```

## How non-team members can contribute?

If you don't have access to create branches in the project repo., you can use the Fork & Pull workflow to contribute.

### Fork The Project

1. Go to prject repo: <https://github.com/expertonlive/expertonlive.com>
2. Click the "Fork" Button in the upper right hand corner of the interface ([More Details Here](https://help.github.com/articles/fork-a-repo/))
3. After the repository has been forked, you will be taken to your copy of the repo at `yourUsername/expertonlive.com`

### Clone Your Fork

1. Open a Terminal / Command Line / Bash Shell in your projects directory (_i.e.: `/yourprojectdirectory/`_)
2. Clone your fork of expertonlive.com

```shell
$ git clone https://github.com/yourUsername/expertonlive.com.git
```

#### (make sure to replace `yourUsername` with your GitHub Username)

This will download the entire repo to your projects directory.

### Setup Your Upstream

1. Change directory to the new expertonlive directory (`cd expertonlive`)
2. Add a remote to the official expertonlive repo:

```shell
$ git remote add upstream https://github.com/expertonlive/expertonlive.git
```

Congratulations, you now have a local copy of the repo!

### Maintaining Your Fork

Now that you have a copy of your fork, there is work you will need to do to keep it current.

#### **Rebasing from Upstream**

Do this prior to every time you create a branch for a PR:

1. Make sure you are on the `staging` branch

   ```shell
   $ git status
   On branch staging
   Your branch is up-to-date with 'origin/staging'.
   ```  
   If your aren't on `staging`, resolve outstanding files / commits and checkout the `staging` branch

   ```shell
   $ git checkout staging
   ```

2. Do a pull with rebase against `upstream`

   ```shell
   $ git pull --rebase upstream staging
   ```

   This will pull down all of the changes (in the official staging branch), without making an additional commit in your local repo.

3. (_Optional_) Force push your updated staging branch to your GitHub fork

   ```shell
   $ git push origin staging --force
   ```

   This will overwrite the staging branch of your fork.


## Create a New Branch To work On

Before you start working, you will need to create a separate branch specific to the issue / feature you're working on. You will push your work to this branch.

### Naming Your Branch

Name the branch something like `fix/xxx` or `feature/xxx` where `xxx` is a short description of the changes or feature you are attempting to add. For example `fix/email-login` would be a branch where you fix something specific to email login.

### Adding Your Branch

To create a branch on your local machine (and switch to this branch).:

```shell
# do this from staging branch 
$ git checkout -b [name_of_your_new_branch]
```

and to push to GitHub:

```shell
$ git push origin [name_of_your_new_branch]
```

#### If you need more help with branching, take a look at _[this](https://github.com/Kunena/Kunena-Forum/wiki/Create-a-new-branch-with-git-and-manage-branches)_.


## How To Commit Messages

Commit messages should follow the [commit message convention](./COMMIT_CONVENTION.md) so that changelogs can be automatically generated. If git hooks have been properly linked, commit messages will be automatically validated upon commit. It is recommended to use `npm run commit` instead of `git commit`, and the ([Commitizen](https://github.com/commitizen/cz-cli)) CLI tool will assist you in generating proper commit messages. Adhering to this convention also leads to **more readable messages** that are easy to follow when looking through the **project history**.

## Creating A Pull Request

A pull request (PR) is a method of submitting proposed changes to any Repo to be merged in the main branch (for which you don't have write access to).

- Do not submit PRs against the `master branch`. The master branch is basically just a snapshot of the latest stable release. All development should be done in dedicated feature branches & PRs should be submitted against `staging branch`.

- make sure `npm test` passes locally before requesting a PR.

### If your PR is accepted

Once your PR is accepted, you may delete the branch you created to submit it.

You can do this with a press of a button on the GitHub PR interface. You can
delete the local copy of the branch with: `git branch -D branch/to-delete-name`

### If your PR is rejected

Don't despair! You should receive solid feedback from the team members as to
why it was rejected and what changes are needed.

If you have a local copy of the repo, you can make the requested changes and
amend your commit with: `git commit --amend` This will update your existing
commit. When you push it to your fork you will need to do a force push to
overwrite your old commit: `git push --force`

Be sure to post in the PR conversation that you have made the requested changes.
