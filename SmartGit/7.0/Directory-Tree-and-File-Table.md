# Directory Tree and File Table

The directory tree and the file table display the status of your working
tree (and Index). The primary directory states are listed in [Primary Directory States](#primary-directory-states), and
possible states of submodules in [Submodule States](#submodule-states). Every primary and
submodule state may be combined with additional states, which are listed
in [Additional Directory States](#additional-directory-states). The possible file
states are listed in [File States](#file-states).

## File Filtering

The **Files** table of the project window can be filtered by file state
and name. The state filters can be set using the small toolbar buttons
above the table as well as the menu items in the **View** menu. By
default, if committable files (e.g. *index-only changed* or *untracked*)
are hidden, the background turns to light-red as a reminder to not
forget about them. If this annoys you because you permanently have
untracked files in your working, you should consider to mark them as
ignored. If this is no option for you, you can deactivate this coloring
feature in the Preferences (page **User Interface**, option **Use
background color for the file table to indicate certain states**).

To filter by name, use the input field (or *\<Ctrl/Cmd>+\<F>*-keystroke)
above the file table. The context menu allows to enable regular
expressions and save patterns for later usage or delete them. Even if
unchanged files are hidden, they can be found by filtering by name - the
files matching by name but not by state are shown in gray, while a
light-yellow background indicates the name-filtering state.

## Primary Directory States


|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |                |                                                                                                                                                                                           |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![](attachments/1704493/1704497.png)     | Default        | Directory is present in the repository (more precisely: there is at least one versioned file below this directory stored in the repository).                                              |
| ![](attachments/1704493/1704507.png) | Unversioned    | Directory (and contained files) are present in the working tree, but have not been added to the repository yet. Use **Stage** to add the files to the repository.                         |
| ![](attachments/1704493/1704499.png)     | Ignored        | Directory is not present in the repository (exists only in the working tree) and is marked as to be ignored.                                                                              |
| ![](attachments/1704493/1704501.png)     | Missing        | Directory is present in the repository, but does not exist in the working tree. Use **Stage** to remove the files from the repository or **Discard** to restore them in the working tree. |
| ![](attachments/1704493/1704496.png)    | Conflict       | Repository contains conflicting files (only displayed on the root directory). Use **Resolve** to resolve the conflict.                                                                    |
| ![](attachments/1704493/1704500.png)       | Merge          | Repository is in 'merging' or 'rebasing' state (only displayed on the root directory). Either **Commit** the merge/rebase or use **Discard** to cancel the merge/rebase.                  |
| ![](attachments/1704493/1704502.png)        | Root/Submodule | Directory is either the project root or a submodule root, see [Submodule States](#submodule-states).                                                            |


## Submodule States


|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |                          |                                                                                                                                                                                                                                                                                                                                                                                |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![](attachments/1704493/1704502.png)                        | Submodule                | Unchanged submodule.                                                                                                                                                                                                                                                                                                                                                           |
| ![](attachments/1704493/1704505.png)       | Modified in working tree | Submodule in working tree points to a different commit than the one registered in the repository. Use **Stage** to register the new commit in the Index, or **Reset** to reset the submodule to the commit registered in the repository.                                                                                                                                       |
| ![](attachments/1704493/1704503.png)    | Modified in Index        | Submodule in working tree points to a different commit than the one registered in the repository, and this changed commit has been staged to the Index. **Commit** this change or use **Discard** to revert the Index.                                                                                                                                                         |
| ![](attachments/1704493/1704504.png) | Modified in WT and Index | Submodule in working tree points to a different commit than the one in the Index, and the staged commit in the Index is different from the one in the repository. Use either **Stage** to register the changed commit in the Index (overwriting the Index change), **Discard** to revert the Index, or **Reset** to reset the submodule to the commit registered in the Index. |
| ![](attachments/1704493/1704506.png)         | Foreign repository       | Nested repository is not registered in the parent repository as submodule. Use **Stage** to register (and add) the submodule to the parent repository.                                                                                                                                                                                                                         |


## Additional Directory States


|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                        |                                                                                    |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------|------------------------------------------------------------------------------------|
| ![](attachments/1704493/1704494.png)   | Direct Local Changes   | There are local (or Index) changes within the directory itself.                    |
| ![](attachments/1704493/1704495.png) | Indirect Local Changes | There are local (or Index) changes in one of the subdirectories of this directory. |


## File States


|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                         |                                                                                                                                                                                                                                                                           |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![](attachments/1704493/1704518.png)       | Unchanged               | File is under version control and neither modified in working tree nor in Index.                                                                                                                                                                                          |
| ![](attachments/1704493/1704519.png)     | Unversioned             | File is not under version control, but only exists in the working tree. Use **Stage** to add the file or **Ignore** to ignore the file.                                                                                                                                   |
| ![](attachments/1704493/1704510.png)         | Ignored                 | File is not under version control (exists only in the working tree) and is marked to be ignored.                                                                                                                                                                          |
| ![](attachments/1704493/1704515.png)        | Modified                | File is modified in the working tree. Use **Stage** to add the changes to the Index or **Commit** the changes immediately.                                                                                                                                                |
| ![](attachments/1704493/1704517.png)          | Modified (Index)        | File is modified and the changes have been staged to the Index. Either **Commit** the changes or **Unstage** changes to the working tree.                                                                                                                                 |
| ![](attachments/1704493/1704514.png) | Modified (WT and Index) | File is modified in the working tree and in the Index in different ways. You may **Commit** either Index changes or working tree changes.                                                                                                                                 |
| ![](attachments/1704493/1704515.png)        | Modified (File Mode)    | The content of the file is not modified, but the executable bits are set different than in the repository. Refer to [Fixing 'Modified (File Mode)' on Windows](#file-states.how-to-fix-modified-file-mode) on how to fix that state on Windows. |
| ![](attachments/1704493/1704508.png)           | Added                   | File has been added to Index. Use **Unstage** to remove from the Index.                                                                                                                                                                                                   |
| ![](attachments/1704493/1704516.png)         | Removed                 | File has been removed from the Index. Use **Unstage** to un-schedule the removal from the Index.                                                                                                                                                                          |
| ![](attachments/1704493/1704512.png)         | Missing                 | File is under version control, but does not exist in the working tree. Use **Stage** or **Remove** to remove from the Index or **Discard** to restore in the wirking tree.                                                                                                |
| ![](attachments/1704493/1704513.png)  | Modified (Added)        | File has been added to the Index and there is an additional change in the working tree. Use **Commit** to either commit just the addition or commit addition and change.                                                                                                  |
| ![](attachments/1704493/1704511.png)   | Intent-to-Add           | File is planned to be added to the Index. Use **Add** or **Stage** to add actually or **Discard** to revert to unversioned.                                                                                                                                               |
| ![](attachments/1704493/1704509.png)        | Conflict                | A merge-like command resulted in conflicting changes. Use the **Conflict Solver** to fix the conflicts.                                                                                                                                                                   |


## Fixing 'Modified (File Mode)' on Windows

On Windows, the *Modified (File Mode)* state is usually caused due to a
misconfiguration of your local repository, when not having
`core.filemode` configuration option explicitly set to `false` (the
default value is `true`).

Hence, if this option in not present in `.git/config` of your
repository, invoke `git config core.filemode false` in the root
directory of your repository to fix this problem.


