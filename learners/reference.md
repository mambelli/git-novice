---
title: 'Git Cheatsheets for Quick Reference'
---

## Git Cheatsheets for Quick Reference

- Printable Git cheatsheets in several languages are [available here](https://github.github.com/training-kit/) ([English version](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf)). More material is available from the [GitHub training website](https://try.github.io/).
- An [interactive one-page visualisation](https://ndpsoftware.com/git-cheatsheet.html)
  about the relationships between workspace, staging area, local repository, upstream repository, and the commands associated with each (with explanations).
- Both resources are also available in other languages (e.g. Spanish, French, and more).
- "[Happy Git and GitHub for the useR](https://happygitwithr.com)" is an accessible, free online book by Jenny Bryan on how to setup and use Git and GitHub with specific references on the integration of Git with RStudio and working with Git in R.
- [Open Scientific Code using Git and GitHub](https://open-source-for-researchers.github.io/open-source-workshop/) - A collection of explanations and short practical exercises to help researchers learn more about version control and open source software.
- [Learn Git Branching](https://learngitbranching.js.org/) is an interesting play based Git learning site to understand better many Git concepts like branching, merging and cherry pocking.

## Glossary

[changeset]{#changeset}
:   A group of changes to one or more files that are or will be added
to a single [commit](#commit) in a [version control](#version-control)
[repository](#repository).

[commit]{#commit}
:   To record the current state of a set of files (a [changeset](#changeset))
in a [version control](#version-control) [repository](#repository). As a noun,
the result of committing, i.e. a recorded changeset in a repository.
If a commit contains changes to multiple files,
all of the changes are recorded together.

[conflict]{#conflict}
:   A change made by one user of a [version control system](#version-control)
that is incompatible with changes made by other users.
Helping users [resolve](#resolve) conflicts
is one of version control's major tasks.

[HTTP]{#http}
:   The Hypertext Transfer [Protocol](#protocol) used for sharing web pages and other data
on the World Wide Web.

[merge]{#merge}
:   (a repository): To reconcile two sets of changes to a
[repository](#repository).

[protocol]{#protocol}
:   A set of rules that define how one computer communicates with another.
Common protocols on the Internet include [HTTP](#http) and [SSH](#ssh).

[remote]{#remote}
:   (of a repository) A version control [repository](#repository) connected to another,
in such way that both can be kept in sync exchanging [commits](#commit).

[repository]{#repository}
:   A storage area where a [version control](#version-control) system
stores the full history of [commits](#commit) of a project and information
about who changed what, when.

[resolve]{#resolve}
:   To eliminate the [conflicts](#conflict) between two or more incompatible changes to a file or set of files
being managed by a [version control](#version-control) system.

[revision]{#revision}
:   A synonym for [commit](#commit).

[SHA-1]{#sha-1}
:   [SHA-1 hashes](https://en.wikipedia.org/wiki/SHA-1) is what Git uses to compute identifiers, including for commits.
To compute these, Git uses not only the actual change of a commit, but also its metadata (such as date, author,
message), including the identifiers of all commits of preceding changes. This makes Git commit IDs virtually unique.
I.e., the likelihood that two commits made independently, even of the same change, receive the same ID is exceedingly
small.

[SSH]{#ssh}
:   The Secure Shell [protocol](#protocol) used for secure communication between computers.

[timestamp]{#timestamp}
:   A record of when a particular event occurred.

[version control]{#version-control}
:   A tool for managing changes to a set of files.
Each set of changes creates a new [commit](#commit) of the files;
the version control system allows users to recover old commits reliably,
and helps manage conflicting changes made by different users.


