# Gerrit

SmartGit provides a **Push to Gerrit** command in the **Branches** view
if a Gerrit remote has been detected. It will push your current branch
`branch` to `refs/for/branch`.

SmartGit will detect a remote as being connected to Gerrit, if:

-   `.git/hooks/commit-msg` exists; and
-   there is only one remote overall or it's the only remote connecting
    to port 29418 (default Gerrit SSH port)
