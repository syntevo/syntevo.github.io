# Gerrit

SmartGit provides a **Push to Gerrit** command in the **Branches** view
if a Gerrit remote has been detected. It will push your current branch
`branch` to `refs/for/branch`.

SmartGit will detect a remote as being connected to Gerrit, if:

-   `.git/hooks/commit-msg` exists; and
-   an appropriate `remote` can be determined from `.gitconfig` for the
    selected branch:  
    -   if the branch is tracking a remote branch and its remote is
        connecting to port 29418 (default Gerrit SSH port), this remote
        is used
    -   if the branch is not tracking a remote branch:
        -   if there is a unique remote connecting to port 29418, this
            remote is used
        -   if there is no remote connecting to port 29418 but there is
            just a single remote overall, this remote is used



To have Gerrit-related commands available in context menu,
set [Low-level Property](System-Properties.md)
`ui.showPushToGerritInMainWindow`.


