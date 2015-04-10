Git Protocol
============

A guide for programming within version control.

Creating a Repo
---------------

* Before creating a new repo, discuss the need with the team. Decide if a new repo is necessary or the code really belongs in an existing project.
* Repo names should be lowercase and dashed, i.e. my-great-project. Prototypes, experiments, and other r&d projects should be placed in the prototypes group. We want to keep the product related groups clean; they should only contain production projects.


Maintain a Repo
---------------

* Avoid including files in source control that are specific to your
  development machine or process.
* Delete local and remote feature branches after merging.
* Perform work in a feature branch.
* Rebase frequently to incorporate upstream changes also follow ["The Golden Rule of Rebasing"](https://www.atlassian.com/git/tutorials/merging-vs-rebasing/the-golden-rule-of-rebasing) to avoid destroying history.
* Use a [pull request] for code reviews.

[pull request]: https://help.github.com/articles/using-pull-requests/

Write a Feature
---------------

Create a local feature branch based off master.

    git checkout master
    git pull
    git checkout -b <branch-name>

Prefix the branch name with your initials.

Rebase frequently to incorporate upstream changes.

    git fetch origin
    git rebase origin/master

Resolve conflicts. When feature is complete and tests pass, stage the changes.

    git add --all

When you've staged the changes, commit them.

    git status
    git commit --verbose

Write a [good commit message]. Example format:

    Present-tense summary under 50 characters

    * More information about commit (under 72 characters).
    * More information about commit (under 72 characters).

    http://project.management-system.com/ticket/123

If you've created more than one commit, use a rebase to squash them into
cohesive commits with good messages:

    git rebase -i origin/master

Share your branch.

    git push origin <branch-name>

Submit a [GitHub pull request].

Ask for a code review in the project's chat room and post the link to
the pull request.

[good commit message]: http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
[GitHub pull request]: https://help.github.com/articles/using-pull-requests/

Review Code
-----------

A team member other than the author reviews the pull request. They follow
[Code Review](code-review/README.md) guidelines to avoid
miscommunication.

They make comments and ask questions directly on lines of code in the GitHub
web interface or in the project's chat room.

For changes which they can make themselves, they check out the branch.

    git checkout <branch-name>
    ./bin/setup
    git diff staging/master..HEAD

They make small changes right in the branch, test the feature on their machine,
run tests, commit, and push.

When satisfied, they comment on the pull request `Ready to merge.`

Merge
-----

Rebase interactively. Squash commits like "Fix whitespace" into one or a
small number of valuable commit(s). Edit commit messages to reveal intent. Run
tests.

    git fetch origin
    git rebase -i origin/master

It also makes it possible to [find the pull request] that brought in your changes. View a list of new commits. View changed files. Merge branch into master.

    git log origin/master..<branch-name>
    git diff --stat origin/master
    git checkout master
    git merge <branch-name> --ff-only
    git push

Delete your remote feature branch.

    git push origin --delete <branch-name>

Delete your local feature branch.

    git branch --delete <branch-name>

[find the pull request]: http://stackoverflow.com/a/17819027
