# How to perform squash merges

In SmartGit, squash merges can be performed either from the main window
or from the log window. In both cases, you first have to make sure
you've checked out the branch onto which you want to apply the merge
commit.

-   **From the main window:** In the main menu, select
    **Branch\|Merge**. On the Merge dialog that shows up, first select
    the topmost commit (i.e. the newest) from the ones you want to want
    to squash merge into the current branch. Second, make sure the
    option **Branch consisting of selected commit and its ancestors** is
    selected. Then click on the **Merge** button.
-   **From the log window:** On the *Commits* view, right-click on the
    topmost commit from the ones to squash merge into the current
    branch. In the context menu, click on **Merge**. On the confirmation
    dialog that shows up, select the **Merge to Working Tree** option.

Regardless of whether you merged from the main window or the log window,
your working tree is now in a merging state. If there are any conflicts,
you'll have to resolve them before you can proceed. Resolving conflicts
is covered in another How-To: [How to resolve conflicts](How-to-resolve-conflicts.md#Howtoresolveconflicts-workflows.resolve-conflicts).

If there weren't any conflicts, or after all conflicts have been
resolved, you can perform a commit (e.g. by selecting **Local\|Commit**
in the menu) to finish the squash merge operation. On the commit dialog,
you'll get to choose whether you want to perform a normal merge or a
squash merge. Select the latter option and enter a commit message, then
click on the **Commit** button.
