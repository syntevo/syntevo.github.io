# Outgoing View

This view shows 'outgoing' commits:

-   this includes all commits of the current branch which are
    *pushable*, i.e. which are not present on any other remote branch
    for the corresponding remote.
-   in case of a Git-Flow feature (or bugfix) branch *and* if the
    modification of pushed commits has been allowed in the Preferences,
    this also includes all commits of the branch, which are not present
    on `develop` (or `master`).

The view will include submodule commits as well.The *Path* column shows
the relative location of the commit's repository (usually `.` for the
currently selected repository).

To push only a subset of your local commits, select the latest commit to
be pushed and invoke **Push Commits**.

## Interactive Rebase

The Outgoing view supports certain workflows to cleanup the commits.

-   To squash adjacent commits, select them and invoke **Squash
    Commits** and provide the new commit message.
-   To reorder commits, just use drag and drop.
-   To coalesce two (not necessarily adjacent) commits *with the same
    commit message*, drag one of the commits onto the other one.
-   To change the commit message, select the commit and invoke **Edit
    Commit Message**.
-   To change the author, select the commit and invoke **Edit Author**.


#### Note
>
>
>Those operations will not work if merge commits would be affected. If
>the working copy is not clean, SmartGit asks whether to stash the
>changes and apply later. The behavior of how commit times will (or will
>not) be adjusted can be configured by system properties
>([smartgit.pushableCommits.preserveAuthorDate](System-Properties.md#smartgitrevertcommitmessagetemplatesmartgit.pushableCommits.preserveAuthorDate)).
>
>


#### Tip
>
>
>To just change the commit message of the last commit (even for a merge
>commit or if the working copy is not clean), invoke **Local\|Edit Last
>Commit Message**.
>
>
