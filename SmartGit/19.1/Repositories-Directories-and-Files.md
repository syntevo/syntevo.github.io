# Repositories, Directories and Files

The Repositories view shows all repositories known to SmartGit and, for
repositories opened in this window, the directory structure (and their
states). The Files view displays the status of your working tree (and
Index). The primary directory states are listed in [Primary Directory States](#primary-directory-states), and
possible states of submodules in [Submodule States](#submodule-states). Every
primary and submodule state may be combined with additional states,
which are listed in [Additional Directory States](#additional-directory-states). The
possible file states are listed in [File States](#file-states).

## Repository Management

To add existing or new local repositories to SmartGit, please take a
look at the section [Repository-Related](Repository-Related.md).

## File Filtering

The **Files** view of the main window can be filtered by file state and
name. The state filters can be set using the small toolbar buttons above
the table as well as the menu items in the **View** menu. By default, if
committable files (e.g. *index-only changed* or *untracked*) are hidden,
the background turns to light-red as a reminder to not forget about
them. If this annoys you because you permanently have untracked files in
your working, you should consider to mark them as ignored. If this is no
option for you, you can deactivate this coloring feature in the
Preferences (page **User Interface**, option **Use background color for
the file table to indicate certain states**).

To filter by name, use the input field (or *\<Ctrl/Cmd>+\<F>*-keystroke)
above the file table. The context menu allows to enable regular
expressions and save patterns for later usage or delete them. Even if
unchanged files are hidden, they can be found by filtering by name - the
files matching by name but not by state are shown in gray, while a
light-yellow background indicates the name-filtering state.

## Primary Directory States


<table class="wrapped confluenceTable" style="width: 100.0%;">
<tbody>
<tr class="odd">
![](attachments/31195181/31195213.png)
<td class="confluenceTd">Default</td>
<td class="confluenceTd">Directory is present in the repository (more precisely: there is at least one versioned file below this directory stored in the repository).</td>
</tr>
<tr class="even">
![](attachments/31195181/31195202.png)
<td class="confluenceTd">Unversioned</td>
<td class="confluenceTd">Directory (and contained files) are present in the working tree, but have not been added to the repository yet. Use <strong>Stage</strong> to add the files to the repository.</td>
</tr>
<tr class="odd">
![](attachments/31195181/31195207.png)
<td class="confluenceTd">Ignored</td>
<td class="confluenceTd">Directory is not present in the repository (exists only in the working tree) and is marked as to be ignored.</td>
</tr>
<tr class="even">
![](attachments/31195181/31195209.png)
<td class="confluenceTd">Missing</td>
<td class="confluenceTd">Directory is present in the repository, but does not exist in the working tree. Use <strong>Stage</strong> to remove the files from the repository or <strong>Discard</strong> to restore them in the working tree.</td>
</tr>
<tr class="odd">
![](attachments/31195181/31195212.png)
<td class="confluenceTd">Conflict</td>
<td class="confluenceTd">Repository contains conflicting files (only displayed on the root directory). Use <strong>Resolve</strong> to resolve the conflict.</td>
</tr>
<tr class="even">
![](attachments/31195181/31195208.png)
<td class="confluenceTd">Merge</td>
<td class="confluenceTd">Repository is in 'merging' or 'rebasing' state (only displayed on the root directory). Either <strong>Commit</strong> the merge/rebase or use <strong>Discard</strong> to cancel the merge/rebase.</td>
</tr>
<tr class="odd">
![](attachments/31195181/31195210.png)
<td class="confluenceTd">Root/Submodule</td>
<td class="confluenceTd">Directory is either the repository root or a submodule root, see <a href="#submodule-states">Submodule States</a>.</td>
</tr>
</tbody>
</table>


## Submodule States


<table class="wrapped confluenceTable" style="width: 100.0%;">
<tbody>
<tr class="odd">
![](attachments/31195181/31195210.png)
<td class="confluenceTd">Submodule</td>
<td class="confluenceTd">Unchanged submodule.</td>
</tr>
<tr class="even">
![](attachments/31195181/31195206.png)
<td class="confluenceTd">Modified in working tree</td>
<td class="confluenceTd">Submodule in working tree points to a different commit than the one registered in the repository. Use <strong>Stage</strong> to register the new commit in the Index, or <strong>Reset</strong> to reset the submodule to the commit registered in the repository.</td>
</tr>
<tr class="odd">
![](attachments/31195181/31195204.png)
<td class="confluenceTd">Modified in Index</td>
<td class="confluenceTd">Submodule in working tree points to a different commit than the one registered in the repository, and this changed commit has been staged to the Index. <strong>Commit</strong> this change or use <strong>Discard</strong> to revert the Index.</td>
</tr>
<tr class="even">
![](attachments/31195181/31195205.png)
<td class="confluenceTd">Modified in WT and Index</td>
<td class="confluenceTd">Submodule in working tree points to a different commit than the one in the Index, and the staged commit in the Index is different from the one in the repository. Use either <strong>Stage</strong> to register the changed commit in the Index (overwriting the Index change), <strong>Discard</strong> to revert the Index, or <strong>Reset</strong> to reset the submodule to the commit registered in the Index.</td>
</tr>
<tr class="odd">
![](attachments/31195181/31195201.png)
<td class="confluenceTd">Foreign repository</td>
<td class="confluenceTd">Nested repository is not registered in the parent repository as submodule. Use <strong>Stage</strong> to register (and add) the submodule to the parent repository.</td>
</tr>
</tbody>
</table>


## Additional Directory States


<table class="wrapped confluenceTable" style="width: 100.0%;">
<tbody>
<tr class="odd">
![](attachments/31195181/31195214.png)
<td class="confluenceTd">Direct Local Changes</td>
<td class="confluenceTd">There are local (or Index) changes within the directory itself.</td>
</tr>
<tr class="even">
![](attachments/31195181/31195211.png)
<td class="confluenceTd">Indirect Local Changes</td>
<td class="confluenceTd">There are local (or Index) changes in one of the subdirectories of this directory.</td>
</tr>
</tbody>
</table>


## File States


<table class="wrapped confluenceTable" style="width: 100.0%;">
<tbody>
<tr class="odd">
![](attachments/31195181/31195193.png)
<td class="confluenceTd">Unchanged</td>
<td class="confluenceTd">File is under version control and neither modified in working tree nor in Index.</td>
</tr>
<tr class="even">
![](attachments/31195181/31195190.png)
<td class="confluenceTd">Unversioned</td>
<td class="confluenceTd">File is not under version control, but only exists in the working tree. Use <strong>Stage</strong> to add the file or <strong>Ignore</strong> to ignore the file, or <strong>Commit</strong> to commit it right away.</td>
</tr>
<tr class="odd">
![](attachments/31195181/31195199.png)
<td class="confluenceTd">Ignored</td>
<td class="confluenceTd">File is not under version control (exists only in the working tree) and is marked to be ignored.</td>
</tr>
<tr class="even">
![](attachments/31195181/31195197.png)
<td class="confluenceTd">Modified</td>
<td class="confluenceTd">File is modified in the working tree. Use <strong>Stage</strong> to add the changes to the Index or <strong>Commit</strong> the changes immediately.</td>
</tr>
<tr class="odd">
![](attachments/31195181/31195192.png)
<td class="confluenceTd">Staged</td>
<td class="confluenceTd">File is modified and the changes have been staged to the Index. Either <strong>Commit</strong> the changes or <strong>Unstage</strong> changes to the working tree.</td>
</tr>
<tr class="even">
![](attachments/31195181/31195196.png)
<td class="confluenceTd">Staged Modified</td>
<td class="confluenceTd">File is modified in the working tree and in the Index in different ways. You may <strong>Commit</strong> either Index changes only or working tree changes plus Index changes.</td>
</tr>
<tr class="odd">
![](attachments/31195181/31195196.png)
<td class="confluenceTd">Staged, WT as HEAD</td>
<td class="confluenceTd">File is modified in the working tree and in the Index in different ways, but the working tree state is identical to the HEAD state. Using <strong>Stage</strong> will turn the file back to unchanged again.</td>
</tr>
<tr class="even">
<p>![](attachments/31195181/31195197.png)</p>
<td class="confluenceTd">Modified (File Mode)</td>
<td class="confluenceTd">The content of the file is not modified, but the executable bits are set different than in the repository. Refer to <a href="#file-states.how-to-fix-modified-file-mode">Fixing 'Modified (File Mode)' on Windows</a> on how to fix that state on Windows.</td>
</tr>
<tr class="odd">
<p>![](attachments/31195181/31195197.png)</p>
<td class="confluenceTd">Modified (EOLs only)</td>
<td class="confluenceTd">The content of the file is modified, but only differs in line endings from the Index state. This state will only be determined/show up if <a href="System_Properties">smartgit.refresh.inspectEol</a> system property is set.</td>
</tr>
<tr class="even">
<p>![](attachments/31195181/31195197.png)</p>
<td class="confluenceTd">Modified (EOLs only,<br />
not stageable)</td>
<td class="confluenceTd">The content of the file is modified, but only differs in line endings from the Index state; but, due to the Git configuration (usually <code>core.autocrlf</code>) this modification can't be staged.<br />
Usually, when trying to stage, Git will issue a warning <code>warning: LF will be replaced by CRLF in ...</code> here. This state will only be determined/show up if <a href="System_Properties">smartgit.refresh.inspectEol</a> system property is set.</td>
</tr>
<tr class="odd">
![](attachments/31195181/31195203.png)
<td class="confluenceTd">Added</td>
<td class="confluenceTd">File has been added to Index. Use <strong>Unstage</strong> to remove from the Index.</td>
</tr>
<tr class="even">
<p>![](attachments/31195181/31195191.png)</p>
<td class="confluenceTd">Removed</td>
<td class="confluenceTd">File has been removed from the Index. Use <strong>Unstage</strong> to un-schedule the removal from the Index.</td>
</tr>
<tr class="odd">
<p>![](attachments/31195181/31195189.png)</p>
<td class="confluenceTd">Renamed</td>
<td class="confluenceTd">File is scheduled for addition and has been detected as renamed, see <a href="Preferences_31195216.html#refresh">Preferences, section Refresh</a></td>
</tr>
<tr class="even">
<p>![](attachments/31195181/31195187.png)</p>
<td class="confluenceTd">Renamed (untracked)</td>
<td class="confluenceTd">File is untracked and has been detected as renamed, see <a href="Preferences_31195216.html#refresh">Preferences, section Refresh</a></td>
</tr>
<tr class="odd">
<p>![](attachments/31195181/31195182.png)</p>
<td class="confluenceTd">Renamed (modified)</td>
<td class="confluenceTd">File is scheduled for addition, has been detected as renamed (in the Index) and – on top of that – is modified in the working tree. Use will probably want to use <strong>Stage</strong> to add the working tree changes to the Index.</td>
</tr>
<tr class="even">
<p>![](attachments/31195181/31195188.png)</p>
<td class="confluenceTd">Rename Source</td>
<td class="confluenceTd">File is the added (or missing) source of a detected <strong>Renamed</strong> or <strong>Renamed (untracked)</strong> file</td>
</tr>
<tr class="odd">
<p>![](attachments/31195181/31195194.png)</p>
<td class="confluenceTd">Missing</td>
<td class="confluenceTd">File is under version control, but does not exist in the working tree. Use <strong>Stage</strong> or <strong>Remove</strong> to remove from the Index or <strong>Discard</strong> to restore in the wirking tree.</td>
</tr>
<tr class="even">
<p>![](attachments/31195181/31195195.png)</p>
<td class="confluenceTd">Added Modified</td>
<td class="confluenceTd">File has been added to the Index and there is an additional change in the working tree. Use <strong>Commit</strong> to either commit just the addition or commit addition and change.</td>
</tr>
<tr class="odd">
<p>![](attachments/31195181/31195194.png)</p>
<td class="confluenceTd">Added Missing</td>
<td class="confluenceTd">File has been added to the Index, but the file is missing in the working tree. Use <strong>Commit</strong> to either commit just the addition or <strong>Stage</strong> to undo the addition.</td>
</tr>
<tr class="even">
![](attachments/31195181/31195200.png)
<td class="confluenceTd">Intent-to-Add</td>
<td class="confluenceTd">File is planned to be added to the Index. Use <strong>Add</strong> or <strong>Stage</strong> to add actually or <strong>Discard</strong> to revert to untracked.</td>
</tr>
<tr class="odd">
<p>![](attachments/31195181/31195198.png)</p>
<td class="confluenceTd">Conflicted</td>
<td class="confluenceTd">A merge-like command resulted in conflicting changes. Use the <strong>Conflict Solver</strong> to fix the conflicts.</td>
</tr>
<tr class="even">
<p>![](attachments/31195181/31195184.png)</p>
<td class="confluenceTd">Assume-Unchanged</td>
<td class="confluenceTd">File has the <em>Assume Unchanged</em> flag set. Use <strong>Toggle 'Assume Unchanged'</strong> to clear this flag.</td>
</tr>
<tr class="odd">
<p>![](attachments/31195181/31195183.png)</p>
<td class="confluenceTd">Skipped</td>
<td class="confluenceTd">File has the <em>Skip Worktree</em> flag set. Use <strong>Toggle 'Skip Worktree'</strong> to clear this flag.</td>
</tr>
<tr class="even">
<p>![](attachments/31195181/31195186.png)</p>
<td class="confluenceTd">Inaccessible</td>
<td class="confluenceTd">File's working tree content is not accessible and hence its state can't be evaluated. This usually happens if another application has an exclusive file system lock on this file. To resolve, shutdown all applications which might possibly lock this file.</td>
</tr>
</tbody>
</table>


## File table "duplicate(!)" marker

If the file table shows a **duplicate(!)** marker after a file name,
this means that you are on Windows or on MacOS with case-insensitive
file name and your repository contains the same file, just with changed
case. Such a constellation does not work well for (Smart)Git, so you
should resolve the problem of duplicate files. The easiest way will
probably be to fix this on a case-sensitive file system.

## Fixing 'Modified (File Mode)' on Windows

On Windows, the *Modified (File Mode)* state is usually caused due to a
misconfiguration of your local repository, when not having
`core.filemode` configuration option explicitly set to `false` (the
default value is `true`).

Hence, if this option in not present in `.git/config` of your
repository, invoke `git config core.filemode false` in the root
directory of your repository to fix this problem.


