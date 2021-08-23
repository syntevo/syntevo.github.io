# Preferences

## Commands

This page shows options which influence the executed Git (and Hg)
commands.

### Push

Only select the **Allow modifying pushed commits (e.g. forced-push)** if
you are sure you know Git well enough to understand the consequences of
forced push.

### Log

When **Contact gravatar.com to show images for the users** is selected,
a hash of the email address is generated and then gravatar.com is
contacted to request the belonging graphic which the user first has to
configure there.

## Background Commands

Options on this page define what operations SmartGit might perform
automatically when it is in background.

### Local and Remote Changes

If **Detect Remote Changes** is selected, SmartGit will poll the remote
repositories of the favorite Git repositories in regular intervals for
changes. To avoid excessive overhead, by default only the lightweight
`git ls-remote` command is invoked, so you only get a *notification*
about changes. Note that this command will not notice if, for example,
the currently checked out feature branch has been merged and removed.

If **Fetch closed 'favorite' repositories** or **Fetch open repositories
when idle** is selected, SmartGit also will perform fetch-operations
which actually will *fetch* the changes from the remote repositories,
but can be more resource-hungry.

## Tools

On this page you can define external tools which can operate on certain
selections. A couple of default tools are already preconfigured:

### Open File

This tool will invoke the system's default open command, e.g. to launch
a graphic viewer for `.png` files.

### Open in Terminal

This tool will open the selected directory in the terminal application.

### Format Patch

This tool will create a patch between either the selected commit/ref and
the working tree or the selected two commits/refs.

### Apply Patch

This tool will show a file open dialog and then apply the selected
patch.

### Fast-Forward Merge

This tool allows to right-click local, tracked branches in the
**Branches** view to perform a fast-forward merge for purely remote
changes, especially if you want to avoid having to check out the branch.

## Diff Tools

On this page you can configure different GUI diff tools. The list is
searched from top to bottom. It is also possible to configure viewer
applications, e.g. for graphic files, which then will be invoked two
times for the files to be compared.
