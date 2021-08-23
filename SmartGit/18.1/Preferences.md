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

## Refresh

With **Detect Renames** enabled, SmartGit will detect renames of
*added*/*removed* and optionally also *untracked*/*missing* file pairs.

Select **Distinguish between content and EOL-only changes** to have
SmartGit distinguish between content and EOL-only changes, in addition
to the plain *modified* state which Git reports (in either case, files
which Git considers as *modified* will be reported). The EOL-change
information will be displayed in the **Files** table **State** If you do
not want Git to care about EOLs at all (that's usually the case if you
are on Windows), you might want to use
[core.autocrlf](.md)
or [text and eol attributes](.md).

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
selections.



The **Tools** configuration is stored in `tools.xml` file in the
[settings directory](Installation-and-Files.md) and can handed over to
other developers/machines to share the tools configuration with them.



The *working directory* set when launching the tool will be the root
directory of the corresponding repository (which may also be a
submodule). When launching a tool on a set of files which belong to
different repositories, it will be the closest common directory of all
affected repositories.

A couple of default tools are already preconfigured:

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

## Conflict Solvers

SmartGit comes with a built-in conflict solver (three-way-merge) which
will be used by default when invoking **Query\|Conflict Solver**. If you
prefer, you can configure external three-way-merge tools which should be
used instead. Following notable **Arguments** are available for
an **External Conflict Solver**:

-   `${mergeFile}` represents the resulting conflicting file, as it's
    present in the working tree
-   `${leftFile}` represents Git's "ours" version of the file
-   `${rightFile}` represents Git's "theirs" version of the file
-   `${baseFile}` represents Git's "common" version of the file

For details on how Git is managing these file versions, refer to the
[Git manual](https://git-scm.com/book/tr/v2/Git-Tools-Advanced-Merging).

## Proxy

On this page you can configure the proxy to be used by SmartGit. The
proxy will be used exactly as configured for the check for new versions.
It will also be used for Git HTTP and HTTPs under certain conditions:

-   **Use following proxy** has been selected and
-   there is no `http.proxy` and no `https.proxy` configuration found in
    your `.gitconfig` and Git's system `config` and
-   the neither of following system environment variables is
    set: `HTTP_PROXY`, `HTTPS_PROXY`, `NO_PROXY`

 
