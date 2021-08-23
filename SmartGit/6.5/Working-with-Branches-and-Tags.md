# Working with Branches and Tags

<a id="WorkingwithBranchesandTags-switch"></a>

## Switching between Branches

The simplest way to switch between branches (or more precisely, between
the latest commits within branches) is to double-click on a branch in
the **Branches** view and confirm the Switch Branch dialog that comes
up. The **Branches** view can be found both on the project window and on
the [Log window](Log.md#Log-log) .

If you switch to a remote branch, you can optionally create a new local
branch (recommended) and set up branch tracking.

If you switch to a local branch that tracks a remote branch, and the
latter is ahead of the local branch by a couple of commits, you can
decide whether you just want to just switch to the latest commit of the
local branch, or to switch and let SmartGit do a fast-forward merge to
the latest commit of the remote branch. For further information on
merging, see [Merge](#WorkingwithBranchesandTags-merge).

If you have local changes in your working tree, the Switch might fail.
In this case, SmartGit offers you to stash away the local changes before
executing the actual Switch command and re-apply the changes from the
stash after executing the command. For further information on stashes,
see
[Stashes](Local-Operations-on-the-Working-Tree.md#LocalOperationsontheWorkingTree-stashes).

A more general procedure than branch switching is to check out arbitrary
commits, which is explained in [Checking Out Commits](#WorkingwithBranchesandTags-checkout).

<a id="WorkingwithBranchesandTags-checkout"></a>

## Checking Out Commits

In SmartGit, there are two ways to switch the working tree to a certain
commit:

-   **Project window** On the project window, invoke **Branch\|Check
    Out** from the menu. This will open a dialog containing a Log view,
    where you can select the commit to switch to.
-   **Log window** On the [Log window](Log.md#Log-log) ,
    select the commit to switch to and then select **Check Out** from
    its context menu.

If you select a commit where local branches point to, you will have the
option to switch to these branches. If you select a commit where remote
branches without corresponding local branches point to, you will have
the option to create a corresponding local branch.

Similar to [Switch](#WorkingwithBranchesandTags-switch), Check Out will
optionally stash away local changes, if necessary.

## Adding, Renaming and Deleting Branches and Tags

You can add, rename and delete branches and tags both from the project
window and from the [Log](Log.md#Log-log) window.

### Project Window

The **Branches** view on the project window has various context menu
entries for adding, renaming and deleting selected branches and tags.
These commands can also be invoked via the entries in the **Branch**
menu.

### Log Window

On the Log window, you can add a branch or tag on a commit by selecting
the commit in the Log graph and invoking **Add Branch** or **Add Tag**
in the commit's context menu. Similarly, you can delete a branch or tag
by selecting the commit to which the branch or tag pointer is attached
and invoking **Delete** in the commit's context menu.

Via the context menu of the Log window's **Branches** view, you can add
and delete branches and tags as well. In addition to that, the
**Branches** view also allows you to rename branches.

<a id="WorkingwithBranchesandTags-merge"></a>

## Merge

The Merge command allows you to merge changes from another branch into
the current branch. In addition to the 'normal' merge operation, there
are two variants called 'fast-forward merge ' and 'squash merge'. The
differences are as follows:

### 'Normal' Merge

In case of a normal merge, a merge commit with at least two parent
commits (i.e., the last from the current branch and the last from the
merged branch) is created. See the following figure, where `>` indicates
where the HEAD is pointing to:



``` text
                            o [> master]
                            |\
o [> master]                o \
|                  ==>      |  |
|  o [a-branch]             |  o [a-branch]
.  .                        .  .
```

<a id="WorkingwithBranchesandTags-merge.fastForward"></a>

### Fast-forward Merge

If the current branch is completely included in the branch to be merged
with (i.e. the latter is simply a couple of commits ahead), then no
extra merge commits is created. Instead, the branch pointer of the
current branch is moved forward to match the branch pointer of the other
branch, as shown below:



``` text
o [origin/master]             o [> master][origin/master]
|                     ==>     |
o [> master]                  o
.                             .
```



In SmartGit, there are several places from which you can initiate a
merge:

-   **Menu and toolbar** On the project window, select **Branch\|Merge**
    to open the **Merge** dialog, where you can select the branch to be
    merged into the current branch. Depending on your toolbar settings,
    you can also open this dialog via the **Merge** button on the
    toolbar.
-   **Branches view** In the **Branches** view (available both on the
    project window and the Log window), you can right-click on a branch
    and select **Merge** to merge the selected branch into the current
    branch.
-   **Log Graph** On the Log graph of the **Log** window, you can
    perform a merge by right-clicking on the head commit of the branch
    to be merged with and selecting **Merge** from the context-menu.

Regardless of where you invoked the Merge command, you will be given the
choice between **Create Merge-Commit** and **Merge to Working Tree**,
and optionally also **Fast-Forward** if a fast-forward merge is
possible.

If you choose **Create Merge-Commit**, SmartGit will perform the merge
and create a merge commit, assuming there are no merge conflicts. If
there are merge conflicts, or if you choose **Merge to Working Tree**,
SmartGit will perform the merge, but leave the working tree in a
*merging* state, so that you can manually resolve merge conflicts and
review the changes to be made. See [Resolving Conflicts](#WorkingwithBranchesandTags-resolve-conflicts) for further
information on how to deal with merge conflicts.

### Squash Merge

The squash merge works like a normal merge, except that it discards the
information about where the changes came from. Hence it only allows you
to create normal commits. The squash merge is useful for merging changes
from local (feature) branches where you don't want all of your feature
branch commits to be pushed into the remote repository.



``` text
                            o [> master] (changes from a-branch)
                            |
                        o [> master]                o
                        |                  ==>      |
                        |  o [a-branch]             |  o [a-branch]
                        .  .                        .  .
```



On the **Commit** dialog, you can choose between a normal merge (merge
commit) and a squash merge (simple commit). Thus, to perform a squash
merge you have to choose **Merge to Working Tree** when initiating the
merge, since otherwise you won't see the **Commit** dialog.

### Merge versus Rebase

A Git-specific alternative to merging is *rebasing* (see
[Rebase](#WorkingwithBranchesandTags-rebase)), which can be used to keep
the history linear. For example, if a user has made local commits and
performs a pull with merge, a merge commit with two parent commits - the
user's last commit and the last commit from the tracked branch - is
created. When using rebase instead of merge, Git applies the local
commits on top of the commits from the tracked branch, thus avoiding a
merge commit.

<a id="WorkingwithBranchesandTags-cherry-pick"></a>

## Cherry-Pick

The Cherry-Pick command allows you to 'apply' certain commits from
another branch to the current branch.



``` text

o                        o  C' [> master]
|                        |
o  [> master] A          o  A
|                        |
|   o  [a-branch]        |   o  [a-branch]
|   |                    |   |
o   |  B                 o   |  B
|   |                    |   |
|   o  C (selected)      |   o  C
|   |                    |   |
o   |  D       ===>      o   |  D
|  /        cherry-pick  |  /
| /                      | /
o                        o
```



In SmartGit, there are several places from which you can initiate a
cherry-pick:

-   **Menu and toolbar** On the project window, select
    **Branch\|Cherry-Pick** to open the **Cherry-Pick** dialog, where
    you can select one or more commits to cherry-pick. Depending on your
    toolbar settings, you can also open this dialog via the
    **Cherry-Pick** button on the toolbar.
-   **Log Graph** On the Log graph of the **Log** window, you can
    perform a cherry-pick by right-clicking on one or more commits and
    selecting **Cherry-Pick** from the context-menu.

## Revert

The Revert command allows you to 'undo' certain commits (from whatever
branch) in the current branch.



``` text

o                        o  reversed-C  [> master]
|                        |
o  [> master] A          o  A
|                        |
|   o  [a-branch]        |   o  [a-branch]
|   |                    |   |
o   |  B                 o   |  B
|   |                    |   |
|   o  C (selected)      |   o  C
|   |                    |   |
o   |  D         ===>    o   |  D
|  /            revert   |  /
| /                      | /
o                        o
```



In SmartGit, there are several places from which you can initiate a
Revert:

-   **Menu and toolbar** On the project window, select
    **Branch\|Revert** to open the **Revert** dialog, where you can
    select one or more commits to revert. Depending on your toolbar
    settings, you can also open this dialog via the **Revert** button on
    the toolbar.
-   **Log Graph** On the Log graph of the **Log** window, you can
    perform a revert by right-clicking on one or more commits and
    selecting **Revert** from the context-menu.

<a id="WorkingwithBranchesandTags-rebase"></a>

## Rebase

The Rebase command allows you to apply commits from one branch to
another. Rebase can be viewed as more powerful version of
[Cherry-Pick](#WorkingwithBranchesandTags-cherry-pick), which is
optimized to apply multiple commits from one branch to another. In
SmartGit, a distinction is made between **Rebase HEAD to** and **Rebase
to HEAD**:

**Rebase HEAD to** rebases ("moves") the commits below the HEAD to the
selected commit. The HEAD will be moved to the new fork.



``` text
o  [> master] A               o  [> master] A'
|                             |
o   B                         o  B'
|                             |
o   C                         o  C'
|                             |
|   o  [a-branch] D           |   o  [a-branch] D
|   |                         |  /
|   |                         | /
|   o  E (selected)   ===>    o   E
|  /                          |
| /                           |
o   F                         o   F
```



**Rebase to HEAD** duplicates commits from a separate branch to the HEAD
(similar to what [Cherry-Pick](#WorkingwithBranchesandTags-cherry-pick)
does). The HEAD moves forward on its fork.



``` text
                             o  [> master] B'
                             |
                             o  C'
                             |
                             o  D'
                             |
o  [> master] A              o  A
|                            |
|   o  [a-branch]            |   o  [a-branch]
|   |                        |   |
|   o  B (selected)          |   o  B
|   |                        |   |
|   o  C               ==>   |   o  C
|   |                        |   |
|   o  D                     |   o  D
|  /                         |  /
| /                          | /
o   E                        o   E
```



In SmartGit, there are several places from which you can initiate a
rebase:

-   **Menu and toolbar** On the project window, select **Branch\|Rebase
    HEAD to** or **Branch\|Rebase to HEAD** to open the **Rebase**
    dialog, where you can select the branch to rebase the HEAD onto, or
    the branch to rebase onto the HEAD, respectively. Depending on your
    toolbar settings, you can also open this dialog via the buttons
    **Rebase HEAD to** and **Rebase to HEAD** on the toolbar.
-   **Branches view** In the **Branches** view, you can right-click on a
    branch and select **Rebase HEAD to** to rebase your current HEAD
    onto the selected branch.
-   **Log Graph** On the Log graph of the **Log** window, you can
    perform a rebase by right-clicking on a commit and selecting
    **Rebase HEAD to** or **Rebase to HEAD** from the context-menu.

Just like a merge, a rebase may fail due to merge conflicts. If that
happens, SmartGit will leave the working tree in *rebasing* state,
allowing you to either manually resolve the conflicts or to **Abort**
the rebase. See [Resolving Conflicts](#WorkingwithBranchesandTags-resolve-conflicts) for further
information.

<a id="WorkingwithBranchesandTags-resolve-conflicts"></a>

## Resolving Conflicts

When a [merge](#WorkingwithBranchesandTags-merge), a
[cherry-pick](#WorkingwithBranchesandTags-cherry-pick) or a
[rebase](#WorkingwithBranchesandTags-rebase) fails due to conflicting
changes, SmartGit stops the operation and leaves the working tree in a
conflicted state, so that you can either abort the operation, or resolve
the conflicts and continue with the operation. This section explains how
you can do that with SmartGit. Generally, the following options are
available:

-   **Resolve dialog** If you select a file containing conflicts and
    then invoke **Local\|Resolve** in the menu of SmartGit's project
    window, the Resolve dialog will come up, where you can set the
    file's contents to either of the two conflicting versions, i.e.
    \`Ours' or \`Theirs'. Optionally, you may also choose not to stage
    the resetting of the file contents, meaning that the conflict marker
    on that file won't be removed.
-   **Conflict Solver** Selecting a file containing conflicts and
    invoking **Query\|Conflict Solver** will open the Conflict Solver, a
    three-way diff between the two conflicting versions (left and right
    editor) and a third version (center editor) that contains the
    conflicting hunks from both sides, along with conflict markers. You
    can directly edit the text in the center editor, and you can move
    changes from the left and right side into the center by clicking on
    the arrow and \`x' buttons between the editors.
-   **Discard command** To abort the merge, cherry-pick or rebase,
    select the repository in the **Repositories** view and invoke
    **Local\|Discard**.

Lastly, if all conflicts have been resolved, you can continue with the
merge, cherry-pick or rebase by selecting the repository in the
**Repositories** view and invoking **Local\|Commit**.
