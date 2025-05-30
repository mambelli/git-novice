---
title: Instructor Notes
---

Using a software tool to handle the versions of your project files
lets you focus on the more interesting/innovative aspects of your project.

- Version control's advantages
  - It's easy to set up
  - Every copy of a Git repository is a full backup of a project and its history
  - A few easy-to-remember commands are all you need for most day-to-day version control tasks
  - The [GitHub][github] hosting service provides a web-based collaboration service
- Two main concepts
  - *commit*: a recorded set of changes in your project's files
  - *repository*: the history of all your project's commits
- Why use GitHub?
  - No need for a server: easy to set up
  - GitHub's strong community: your colleagues are probably already there

## Overall

Version control might be the most important topic we teach, but Git is
definitely the most complicated tool.  However, GitHub presently dominates the
open software repository landscape, so the time and effort required to teach
fundamental Git is justified and worthwhile.

Because of this complexity, we don't teach novice learners about many
interesting topics, such as branching, hashes, and commit objects.

Instead we try to convince them that version control is useful for researchers
working in teams or not, because it is

- a better way to "undo" changes,
- a better way to collaborate than mailing files back and forth, and
- a better way to share your code and other scientific work with the world.

## Teaching Notes

- You can "split" your shell so that recent commands remain in view using [this](https://github.com/rgaiacs/swc-shell-split-window) script.

- Make sure the network is working *before* starting this lesson.

- Drawings are particularly useful in this lesson: if you have a whiteboard,
  [use it][drawings]!

- Version control is usually not the first subject in a workshop,
  so get learners to create a GitHub account after the session before.
  Remind learners that the username and email they use for GitHub (and setup
  during Git configuration) will be viewable to the public by default.
  However, there are many reasons why a learner may not want their personal
  information viewable, and GitHub has [resources for keeping an email address
  private][github-privacy].

- If some learners are using Windows, there will inevitably be issues
  merging files with different line endings.  (Even if everyone's on
  some flavor of Unix, different editors may or may not add a
  newline to the last line of a file.) Take a moment to explain
  these issues, since learners will almost certainly trip over them
  again.  If learners are running into line ending problems, GitHub
  has a [page][github-line-endings] that helps with troubleshooting.
  Specifically, the [section on refreshing a repository][github-line-endings-refresh]
  may be helpful if learners need to change the `core.autocrlf` setting
  after already having made one or more commits.

- We don't use a Git GUI in these notes because we haven't found one that
  installs easily and runs reliably on the three major operating systems, and
  because we want learners to understand what commands are being run.  That
  said, instructors should demo a GUI on their desktop at some point during
  this lesson and point learners at [this page][github-gui].

- Instructors should show learners graphical diff/merge tools like
  [DiffMerge][diffmerge].

- When appropriate, explain that we teach Git rather than CVS, Subversion, or
  Mercurial primarily because of GitHub's growing popularity: CVS and
  Subversion are now seen as legacy systems, and Mercurial isn't nearly as
  widely used in the sciences right now.

- Further resources:
  
  - [git-it] is a self-paced command-line Git demo,
    with [git-it-electron] its GitHub Desktop successor.
  - [Code School][code-school] has a free interactive course, [Try Git][try-git].
  - for instructors, [the Git parable][git-parable] is useful background reading

## [Automated Version Control](../episodes/01-basics.md)

- Ask, "Who uses 'undo' in their editor?" All say "Me". 'Undo' is the simplest
  form of version control.

- Give learners a five-minute overview of what version control does for them
  before diving into the watch-and-do practicals.  Most of them will have
  tried to co-author papers by emailing files back and forth, or will have
  biked into the office only to realize that the USB key with last night's
  work is still on the kitchen table.  Instructors can also make jokes about
  directories with names like "final version", "final version revised",
  "final version with reviewer three's corrections", "really final version",
  and, "come on this really has to be the last version" to motivate version
  control as a better way to collaborate and as a better way to back work up.

## [Setting Up Git](../episodes/02-setup.md)

- We suggest instructors and students use `nano` as the text editor for this
  lessons because
  
  - it runs in all three major operating systems,
  - it runs inside the shell (switching windows can be confusing to students), and
  - it has shortcut help at the bottom of the window.
  
  Please point out to students during setup that they can and should use
  another text editor if they're already familiar with it.

- When setting up Git, be very clear what learners have to enter: it is
  common for them to edit the instructor's details (e.g. email).  Check at
  the end using `git config --list`.

- When setting up the default branch name, if learners have a Git version
  older than 2.28, the default branch name can be changed for the lesson
  using `git branch -M main` if there are currently commits in the repository,
  or `git checkout -b main` if there are no commits/the repository is completely empty.

## [Creating a Repository](../episodes/03-create.md)

- When you do `git status`, Mac users may see a `.DS_Store` file showing as
  untracked. This a file that Mac OS creates in each directory.

- The challenge "Places to create repositories" tries to reinforce the idea
  that the `.git` folder contains the whole Git repo and deleting this folder
  undoes a `git init`. It also gives the learner the way to fix the common
  mistake of putting unwanted folders (like `Desktop`) under version control.
  
  Instead of removing the `.git` folder directly, you can choose to move it
  first to a safer directory and remove it from there:
  
  ```bash
  $ mv .git temp_git
  $ rm -rf  temp_git
  ```
  
  The challenge suggests that it is a bad idea to create a Git repo inside another repo.
  For more discussion on this topic, please see [this issue][repos-in-repos].

## [Tracking Changes](../episodes/04-changes.md)

- It's important that learners do a full commit cycle by themselves (make
  changes, `git diff`, `git add`, and `git commit`). The "`bio` repository"
  challenge does that.

- This is a good moment to show a diff with a graphical diff tool. If you
  skip it because you're short on time, show it once in GitHub.

- One thing may cause confusion is recovering old versions.  If, instead of
  doing `$ git checkout f22b25e guacamole.md`, someone does `$ git checkout f22b25e`, they wind up in the "detached HEAD" state and confusion abounds.
  It's then possible to keep on committing, but things like `git push origin main` a bit later will not give easily comprehensible results.  It also
  makes it look like commits can be lost.  To "re-attach" HEAD, use
  `git checkout main`.

- This is a good moment to show a log within a Git GUI. If you skip it
  because you're short on time, show it once in GitHub.

## [Ignoring Things](../episodes/06-ignore.md)

Just remember that you can use wildcards and regular expressions to ignore a
particular set of files in `.gitignore`.

## [Remotes in GitHub](../episodes/07-github.md)

- Make it clear that Git and GitHub are not the same thing: Git is an open
  source version control tool, GitHub is a company that hosts Git
  repositories in the web and provides a web interface to interact with repos
  they host.

- It is very useful to draw a diagram showing the different repositories
  involved.

- When pushing to a remote, the output from Git can vary slightly depending on
  what leaners execute. The lesson displays the output from git if a learner
  executes `git push origin main`. However, some learners might use syntax
  suggested by GitHub for pushing to a remote with an existing repository,
  which is `git push -u origin main`. Learners using syntax from GitHub,
  `git push -u origin main`, will have slightly different output, including
  the line `Branch main set up to track remote branch main from origin by rebasing.`

## [Collaborating](../episodes/08-collab.md)

- Decide in advance whether all the learners will work in one shared
  repository, or whether they will work in pairs (or other small groups) in
  separate repositories.  The former is easier to set up; the latter runs
  more smoothly.

- Role playing between two instructors can be effective when teaching the
  collaboration and conflict sections of the lesson.  One instructor can play
  the role of the repository owner, while the second instructor can play the
  role of the collaborator.  If it is possible, try to use two projectors so
  that the computer screens of both instructors can be seen.  This makes for
  a very clear illustration to the students as to who does what.

- It is also effective to pair up students during this lesson and assign one
  member of the pair to take the role of the owner and the other the role of
  the collaborator.  In this setup, challenges can include asking the
  collaborator to make a change, commit it, and push the change to the remote
  repository so that the owner can then retrieve it, and vice-versa.  The
  role playing between the instructors can get a bit "dramatic" in the
  conflicts part of the lesson if the instructors want to inject some humor
  into the room.

- If you don't have two projectors, have two instructors at the front of the
  room.  Each instructor does their piece of the collaboration demonstration
  on their own computer and then passes the projector cord back and forth
  with the other instructor when it's time for them to do the other part of
  the collaborative workflow.  It takes less than 10 seconds for each
  switchover, so it doesn't interrupt the flow of the lesson.
  And of course it helps to give each of the instructors a different-colored
  hat, or put different-colored sticky notes on their foreheads.

- If you're the only instructor, the best way to create is clone the two
  repos in your Desktop, but under different names, e.g., pretend one is your
  computer at work:
  
  ```bash
  $ git clone https://github.com/alflin/recipes.git recipes-at-work
  ```

- It's very common that learners mistype the remote alias or the remote URL
  when adding a remote, so they cannot `push`. You can diagnose this with
  `git remote -v` and checking carefully for typos.
  
  - To fix a wrong alias, you can do `git remote rename <old> <new>`.
  - To fix a wrong URL, you can do `git remote set-url <alias> <newurl> `.

- Before cloning the repo, be sure that nobody is inside another repo. The
  best way to achieve this is moving to the `Desktop` before cloning: `cd && cd Desktop`.

- If both repos are in the `Desktop`, have them to clone their collaborator
  repo under a given directory using a second argument:
  
  ```bash
  $ git clone https://github.com/alflin/recipes.git alflin-recipes
  ```

- The most common mistake is that learners `push` before `pull`ing. If they
  `pull` afterward, they may get a conflict.

- Conflicts, sometimes weird, will start to arise. Stay tight: conflicts are
  next.

- Learners may have slightly different output from `git push` and `git pull`
  depending on the version of git, and if upstream (`-u`) is used.

## [Conflicts](../episodes/09-conflict.md)

- Expect the learners to make mistakes. Expect *yourself* to make mistakes.
  This happens because it is late in the lesson and everyone is tired.

- If you're the only instructor, the best way to create a conflict is:
  
  - Clone your repo in a different directory, pretending is your computer at
    work: `git clone https://github.com/alflin/recipes.git recipes-at-work`.
  - At the office, you make a change, commit and push.
  - At your laptop repo, you (forget to pull and) make a change, commit and
    try to push.
  - `git pull` now and show the conflict.

- Learners usually forget to `git add` the file after fixing the conflict and
  just (try to) commit. You can diagnose this with `git status`.

- Remember that you can discard one of the two parents of the merge:
  
  - discard the remote file, `git checkout --ours conflicted_file.txt`
  - discard the local file, `git checkout --theirs conflicted_file.txt`
  
  You still have to `git add` and `git commit` after this. This is
  particularly useful when working with binary files.

- Keep in mind that depending on the Git version used, the outputs for
  `git push` and `git pull` can vary slightly.

## [Open Science](../episodes/10-open.md)

## [Licensing](../episodes/11-licensing.md)

We teach about licensing because questions about who owns what, or can use
what, arise naturally once we start talking about using public services like
GitHub to store files. Also, the discussion gives learners a chance to catch
their breath after what is often a frustrating couple of hours.

The Creative Commons family of licenses is recommended for many types of
works (including software documentation and images used in software) but not
software itself. Creative Commons [recommends][cc-faq-software] a
software-specific license instead.

## [Citation](../episodes/12-citation.md)

## [Hosting](../episodes/13-hosting.md)

A common concern for learners is having their work publicly available on
GitHub.  While we encourage open science, sometimes private repos are the
only choice. It's always interesting to mention the options to have
web-hosted private repositories.


## [Supplemental: Using Git from RStudio](../episodes/14-supplemental-rstudio.md)

## [Setting up a Python Project](../episodes/15-python-project-and-testing.md)

Python is a very common language.
This episode gives an example and it is functional to see some additional
capabilities of Git and GitHub like the ability to run pre-commit scripts,
an example of Git hooks, and GitHub actions and workflows.
It is functional also to the next episode, since the workflows will be
used to test Pull Requests before proceeding with merges.

## [Collaborating - Branching and Pull Requests](../episodes/16-collab-branch-and-pr.md)

This is the most common way of collaborating on GitHub and for big projects on Git.
It gives more control to the project owners and allos to review and discuss changes.

This episode uses the original recipes project but could be using also the
unitconversion repository.
The first would make it more similar to the earlier episodes but would loose the
ability to see the code testing workflows used to validate the Python code 
in action. 

Before starting prepare your own origin repository, a copy of the
https://github.com/mambelli/recipes or 
https://github.com/mambelli/unitconverter repository done either via fork
or by cloning and saving as a new repository.
This will be the repository that others in the class will fork from, 
the URL you'll have to communicate to the class (instead of Alfredo's one).

The other teaching observations are similar to the Collaborating episode. 
Instead of a "shared repository" think of a "shared fork".

- Decide in advance whether all the learners will work forking the same
  repository, or whether they will work in pairs (or other small groups)
  forking separate repositories.  The former is easier to set up; the
  latter runs more smoothly.

- Role playing between two instructors can be effective when teaching the
  collaboration and conflict sections of the lesson.  One instructor can play
  the role of the original repository owner, while the second instructor can 
  play the role of the collaborator owning the fork.  If it is possible, try 
  to use two projectors so that the computer screens of both instructors can
  be seen.  This makes for a very clear illustration to the students as to who 
  does what.

- It is also effective to pair up students during this lesson and assign one
  member of the pair to take the role of the original owner and the other 
  the role of the collaborator.  In this setup, challenges can include asking
  the collaborator to make a change, commit it, and push the change to the remote
  repository so that the owner can then retrieve it, and vice-versa.  The
  role playing between the instructors can get a bit "dramatic" in the
  conflicts part of the lesson if the instructors want to inject some humor
  into the room.

- If you don't have two projectors, have two instructors at the front of the
  room.  Each instructor does their piece of the collaboration demonstration
  on their own computer and then passes the projector cord (or screen share)
  back and forth
  with the other instructor when it's time for them to do the other part of
  the collaborative workflow.  It takes less than 10 seconds for each
  switchover, so it doesn't interrupt the flow of the lesson.
  And of course it helps to give each of the instructors a different-colored
  hat, or put different-colored sticky notes on their foreheads.

- If you're the only instructor, the best way to create is to create a second 
  GitHub account, e.g. an organization, and to fork the repository there.  Then
  clone the two repos in your Desktop, but under different names, e.g., pretend
  one is your collaboration, the other your private copy:

  ```bash
  $ git clone https://github.com/alflin/unitconverter.git unitconverter-collaboration
  ```

- An interesting role play is sending on purpose a PR with something wrong and
  use the conversation thread and the code review to request fixes and to 
  show also how the PR recipient can edit the files in GitHub.

[github]: https://github.com/
[drawings]: https://marklodato.github.io/visual-git-guide/index-en.html
[github-privacy]: https://help.github.com/articles/keeping-your-email-address-private/
[github-line-endings]: https://docs.github.com/en/github/using-git/configuring-git-to-handle-line-endings
[github-line-endings-refresh]: https://docs.github.com/en/github/using-git/configuring-git-to-handle-line-endings#refreshing-a-repository-after-changing-line-endings
[github-gui]: https://git-scm.com/downloads/guis
[diffmerge]: https://sourcegear.com/diffmerge/
[git-it]: https://github.com/jlord/git-it
[git-it-electron]: https://github.com/jlord/git-it-electron
[code-school]: https://www.codeschool.com/
[try-git]: https://try.github.io
[git-parable]: https://tom.preston-werner.com/2009/05/19/the-git-parable.html
[repos-in-repos]: https://github.com/swcarpentry/git-novice/issues/272
[cc-faq-software]: https://creativecommons.org/faq/#can-i-apply-a-creative-commons-license-to-software



