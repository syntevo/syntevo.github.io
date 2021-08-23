# Outgoing View

This view shows 'outgoing' commits. This usually means unpushed commits,
but in the case of a Git-Flow feature or bugfix branch, it also means
already pushed commits of this specific branch. In case of submodules
commits, they will also be shown. The *Path* column shows the relative
location of the commit's repository (usually `.` for the currently
selected repository).

To push only a subset of your local commits, select the latest commit to
be pushed and invoke **Push Commits**.

## Interactive Rebase

The Outgoing view supports certain workflows to cleanup the commits. To
join adjacent commits, select them and invoke **Join Commits** and
provide the new commit message. To reorder commits, just use drag and
drop. To change the commit message, select the commit and invoke **Edit
Commit Message**.


#### Note
>
>
>All those operations need a clean working tree and will not work if
>merge commits would be affected.
>
>


#### Tip
>
>
>To just change the commit message of the last commit (even for a merge
>commit), a clean working tree is not required if you invoke
>**Local\|Edit Last Commit Message**.
>
>
