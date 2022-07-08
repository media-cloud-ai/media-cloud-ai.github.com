---
layout: default
---

# Open source

The Media-Cloud AI source code is hosted on a Gitlab group: [https://gitlab.com/media-cloud-ai](https://gitlab.com/media-cloud-ai)

# Developer contribution rules

This document aims to define some rules that must be followed as strictly as possible by anyone wishing to contribute to the Media-Cloud AI project.

## Git & Gitlab

As the main tool for sharing Media-Cloud AI code, the use of Git and the Gitlab environment must be given special attention.

The organization of the different Git projects of Media-Cloud AI is based on the [git-flow](https://git-flow.readthedocs.io/en/latest/presentation.html) philosophy. This is mainly involves that each contribution (feature, fix, hotfix or release) has its own branch, based on a main branch (`main` (formerly `master`) or `develop`, or both).

### Main contribution process:

 - Before you start writing code, __ensure a related issue exists__ on the Gitlab repository
 - Starting from the main branch, create a new branch with a name following this pattern:

    `<topic>/<issue_title_or_description>`

   with `fix`, `feature`, `hotfix`, `release`, `ci`... as possible `<topic>` values.

 - __Write descriptive and meaningful commit messages__. No, "change" "wip" or "update" don't belong to this category!
 - __Commit only related work__: the least amount of lines that make sense together, and related to the branch purpose.
 - When your development is complete, push your branch on the remote Gitlab repository, and create a Merge Request, assign yourself and request a review from the issuer, or from a competent* developer.

   _\* someone that will be able to understand the purpose of your Merge Request_

 - Once the Merge Request is approved (and the CI pipeline has succeeded), you can merge thre branch into the target branch, and close the related issue.

### Good practices to apply:

 - Don't commit changes that break the code: projects should be compiling at any commit level.
 - Rebase your working branch as frequently as you can before publishing it on the remote repository.
 - Don't push directly on main branches (master, main, develop...)
 - Never `push --force` onto a main branch (master, main, develop), other developers are basing there work on it!
 - You may rewrite the history (`push --force`) in specific cases:
     - After you rebased your branch
     - To amend the last commit of your branch

    __Always make sure to explicit the target branch when using `push --force`!__

 - Avoid changing a published history: if you want to change your branch history, create a new branch, re-commit your changes properly (`cherry-pick` can be helpful) on the new branch, and then remove the first branch.
