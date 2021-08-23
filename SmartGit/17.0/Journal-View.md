# Journal View

The Journal shows a compact history (Log) for the current branch:

-   *orange* commits denote *ahead* commits which are just present on
    your *local* branch but not yet on the *remote* branch. These
    commits will be sent to the remote branch/repository for the next
    [Push](Synchronizing-with-Remote-Repositories.md).
-   *green* commits denote *incoming* commits which are only present in
    the *remote* branch and will be integrated into your *local* branch
    for the next [Pull](Synchronizing-with-Remote-Repositories.md).
-   *black* commits with *green* connectors denote commits which are
    currently present in the *remote* branch only, but have been present
    in your *local* branch at an earlier time. Usually, these are
    commits which have been *rewritten* using [Rebase](Rebase.md). To show
    such commits, invoke **Show Rewritten Commits** from the options
    menu.
-   *black* commits with *blue* connectors denote commits from the
    *auxiliary* branch which can be toggled using **Show Auxiliary
    Branch** from the options menu.
-   *black* commits with *gray* connectors denote commits which are
    common to more than one of the *local*, *remote* or *auxiliary*
    branch.

Depending on the type of commit(s) selected, you can invoke various
operations from the context menu, most notably, you can easily rewrite
the history:

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
>The behavior of how commit times will (or will not) be adjusted can be
>configured by system properties
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
