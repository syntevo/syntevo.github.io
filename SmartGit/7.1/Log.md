# Log

SmartGit's Log displays the repository's history as a list of commits,
sorted by increasing age, and with a graph on the left side to show the
parent-child relationships between the commits. What is shown on the Log
depends on what was selected when the Log command was invoked:

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

-   **Branches view** In the **Branches** view (just project window),
    you can right-click on a branch and select **Log** to open the Log
    for the selected branch.
-   **Outgoing view** In the **Outgoing** view, you can right-click on a
    specific commit and invoke **Log** to open the Log for the current
    branch, with the selected commit pre-selected in the Log.

## Log Commands

In the *Log Frame*, many commands which are known from the *Project
Window* are available as well:

-   most of them are available from the main menu bar
-   the context menu on a commit provides certain commands
-   certain items in the **Graph** view, like *local refs* or the
    *HEAD*-arrow can be modified using drag-and-drop.

## Compare Commits

You can compare two commits in the **Graph** by selecting both commits
(*Ctrl*-click). The difference from the *newer* commit compared to the
*older* commit will be displayed in the **Files** view. By selecting a
file you can see detailed change in the **Changes** view.



When comparing branches you can also invoke **Reveal Commit** from the
context menu of the first branch in the **Branches** view, then invoke
**Compare with Selected Commit** on the second branch.



## Recyclable Commits

In the **Branches** view, you can toggle **Recyclable Commits** to get
back obsolete heads which are not reachable anymore from any ref.
Technically, SmartGit will include all commits which are found in the
reflogs (`.git/logs`-files).
