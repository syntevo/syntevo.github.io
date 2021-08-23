# Log

SmartGit's Log displays the working tree state and the repository's
history as a list of commits, sorted by increasing age, and with a graph
on the left side to show the parent-child relationships between the
commits. What is shown on the Log depends on what was selected when the
Log command was invoked:

-   To view the history of the entire repository (*root* Log), select
    the repository in the **Repositories** view before invoking the Log
    command.
-   To view the history of a directory within the repository, select the
    directory in the **Repositories** view before invoking the Log
    command.
-   To view the history of a single file within the repository, select
    the file in the **Files** view before invoking the Log command. If
    the file is not visible in the **Files** view, either adjust the
    file table's filter settings (on its top right), or enter the name
    of the file in the search field above the file table.

A *root* Log can be invoked from other places in SmartGit as well:

-   **Branches view** In the **Branches** view (just main window), you
    can right-click on a branch and select **Log** to open the Log for
    the selected branch.
-   **Journal view** In the **Journal** view, you can right-click on a
    specific commit and invoke **Log** to open the Log for the current
    branch, with the selected commit pre-selected in the Log.

## Graph view

The **Graph** displays the log graph ("history") starting from the
selected **Branches** anchors. Branches/tags and other *refs* will show
up at the "appropriate" commits. In case of File (or Subtree) Logs or
filtered Logs (see **Filter** input field, below), every *ref* will be
mapped to the most recent commit of the graph which is still part of the
ref's history. In case of File (or Subtree) Logs, the file (or subtree)
content of the mapped ref commit will be identical to the content of the
actual commit to which the refs points. For filtered Logs, there is no
such relation between the mapped commit and the actual commit, still you
will be able to see which of your filtered commits are part of which
ref's history.

The **Graph** consists of different columns which can be configured from
the *Options*-menu (≡):

-   The main column shows the *commit graph* including the commit
    messages. Merge-commits will displayed with pale color for less
    visual distraction.
-   The **Author** column shows the *author* of the commit. If
    the *author* is different from the *committer*, the name will be
    highlighted with different color. You can see more details on the
    *committer* in the **Details** view.

## Graph filter

Using the **Filter** field above the **Graph**, you can restrict the
displayed commits to those matching a certain filter criterion. On
change of the **Filter** field, SmartGit will restart the search from
the select **Branches** and report matching commits bit by bit. The
search will be performed directly in the repository, so eventually
SmartGit will find all matching commits in the entire repository.

## Details view

The **Details** view shows details on the selected commit:

-   **branches** and **tags** shows all branch/tag-refs which are
    displayed in the **Graph** for the selected commit. When the Log is
    filtered, **branches** and **tags** will show the *mapped* refs by
    default. You may set **Low-level
    Property** `log.details.onlyShowActualCommitRefsWhenFiltered` in the
    Preferences to only show those refs which are actually located at
    the commit.
-   **on branches** shows all branch-refs for which the selected commit
    is an ancestor reachable by following only "primary" parents, i.e.
    is part of the branch's "natural" history
-   **merged to branches** shows all branch-refs for which the selected
    commit is an ancestor, but only reachable by following at least one
    merge parent (2nd or higher parent of a commit)



Git does not remember the (current) branch as part of a commit. However,
when creating merge commits, Git always uses the currently checked out
(branch that points to a) commit as first parent and the merged one as
second parent. That way it's possible to find out which commits belong
to the same branch (first parent) and which were merged (second parent).



  

## Log Commands

In the *Log Frame*, many commands which are known from the *Project
Window* are available as well:

-   most of them are available from the main menu bar
-   the context menu on a commit provides certain commands
-   certain items in the **Graph** view, like *local refs* or the
    *HEAD*-arrow can be modified using drag-and-drop.
    -   for commit-rewriting commands, refer to the [Journal View](Journal-View.md)

## Compare Commits

You can compare two commits in the **Graph** by selecting both commits
(*Ctrl*-click). The difference from the *newer* commit compared to the
*older* commit will be displayed in the **Files** view. By selecting a
file you can see detailed change in the **Changes** view. In a similar
way, you can compare the Index against a specific commit.



When comparing branches you can also invoke **Reveal Commit** from the
context menu of the first branch in the **Branches** view, then invoke
**Compare with Selected Commit** on the second branch.



## Recyclable Commits

In the **Branches** view, you can toggle **Recyclable Commits** to get
back obsolete heads which are not reachable anymore from any ref.
Technically, SmartGit will include all commits which are found in the
reflogs (`.git/logs`-files).
