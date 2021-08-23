# Submodules


#### Note
>
>
>This section only applies to submodules of *native* Git repositories,
>but not of *SVN clones*. For SVN repositories, refer to [Externals (Normal Mode Only)](SVN-Integration.md#externals-normal-mode-only).
>
>

Often, software projects are not completely self-contained, but share
common parts with other software projects. Git offers a feature called
*submodules*, which allows you to embed one Git repository into another.
This is similar to SVN's *externals* feature.

A submodule is a nested repository that is embedded in a dedicated
subdirectory of the working tree (which belongs to the parent
repository). The submodule is always pointing at a particular commit of
the embedded repository. The definition of the submodule is stored as a
separate entry in the parent repository's git object database.

The link between working tree entry and foreign repository is stored in
the `.gitmodules` file of the parent repository. The `.gitmodules` file
is usually versioned, so it can be maintained by all users and/or
changes are propagated to all users.

Setting submodule repositories involves an initialization process, in
which the required entries are added to the `.git/config` file. The user
may later adjust it, for example to fix SSH login names.

## Cloning Repositories with Submodules

If you clone an existing repository containing one or more submodules
via **Repository\|Clone**, make sure the option **Include Submodules**
is selected, so that all first-level submodules are automatically
initialized and updated. Without this option, you may initialize the
submodules later by hand via **Remote\|Submodule\|Initialize**. Only
performing the initialization will leave the submodule directory empty.
For a fully functional submodule, you'll also need to do a pull on it,
as described in [Updating Submodules](#updating-submodules).

## Adding, Removing and Synchronizing Submodules


#### Note
>
>
>Submodules are showing up in the **Repositories** as well as the
>**Files** view. Submodule operations (from the parent repository
>perspective) will be performed in the **Files** view. 'Normal' Git
>operations on the submodule repository itself will be performed in the
>**Repositories** view.
>
>

To "ignore" a not-yet initialized submodule which you are not interested
in, invoke **Remote\|Submodule\|Deactivate**. This will make the
submodule vanish from the **Files** view unless **View\|Show Ignored
Files** is selected. Technically, `submodule.<name>.active=false` will
be set in the parent repository `.git/config`.

To remove a submodule from the working tree, select the submodule in the
**Files** view, invoke **Remote\|Submodule\|Deinit**. After *deiniting*
you will probably want to **Deactivate** it, too.

To add a new submodule to a repository, invoke
**Remote\|Submodule\|Add** on the repository in the **Repositories**
view and follow the dialog instructions.

To remove a submodule from the repository, select the submodule in the
**Files** view, invoke **Remote\|Submodule\|Unregister**, and then
commit your changes. After the submodule is unregistered, you may delete
the submodule directory.

If the URL of a submodule's remote repository has changed, you need to
modify the URL in the `.gitmodules` file and then *synchronize* the
submodule, via **Remote\|Submodule\|Synchronize**, so that the new URL
is written into Git's configuration.

## Updating Submodules

After a submodule has been set up, the usual workflow is that some files
in the submodule repository are modified externally, and you perform an
*update* on the submodule, i.e. you pull the new changes into your local
submodule repository. You can perform an update either by doing a pull
on the submodule itself, or, if the outer repository is connected to a
remote repository, by configuring SmartGit to automatically update all
submodules when you do a pull on the outer repository. These two cases
will be described in the following subsections. Note that in either
case, pulling will fetch new commits without changing the submodule if
it has a *detached HEAD*. See [Working within Submodules](#working-within-submodules) for more information on the
latter.

### Pulling on the Submodule

Select the submodule in the **Repositories** view and invoke
**Remote\|Pull**. After the pull, the submodule will have a different
appearance in the **Repositories** view if new commits have been fetched
and a rebase or merge has been performed. This different appearance
indicates that the submodule has changed and that you need to
[commit](Local-Operations-on-the-Working-Tree.md#commit)
the change in the outer repository.

### Pulling on the Outer Repository

Open the repository settings via **Repository\|Settings**, and in the
**Pull** section, enable **Update registered submodules**, so that
SmartGit automatically updates all registered submodules when pulling on
the outer repository. Additionally, you may also enable **And initialize
new submodules**; with this, SmartGit will update not only registered
submodules when pulling, but also uninitialized submodules, after having
initialized them. The aforementioned **Update** option will only fetch
commits as needed, i.e. when a commit is referenced by the outer
repository as the current state of the submodule. If you want to fetch
all new commits instead, enable the option **Always fetch new commits,
tags and branches from submodule**. Note that when you do a pull on the
outer repository, you need to pull with subsequent rebase or merge,
otherwise new submodule commits will only be fetched, without changing
the submodule state (i.e. the commit the submodule is currently pointing
at).

## Working within Submodules

You can view the history of a submodule repository by opening its
[Log](Log.md#Log-log). To do so, select the submodule in the
**Repositories** view and invoke **Log** from the submodule's context
menu. You can also restrict the Log to a certain branch within the
submodule: Select the submodule in the **Repositories** view, then
select the submodule branch in the **Branches** view, and then invoke
**Log** from the context menu of the branch.

In the submodule Log, you can switch the submodule to another commit by
selecting the commit in the Log graph and invoking **Check Out** from
the commit's context menu. If you want to switch to the tip of a certain
branch, you can also just double-click on the branch in the **Branches**
view.

After switching the submodule to another commit, the submodule will be
shown as 'changed' in the **Files** view. That means you can either
commit the change in the outer repository or roll back the change. For
the latter, select the submodule in the **Files** view and invoke
**Reset** from its context menu.

If you modify and commit files within the submodule (as part of the
outer repository, not externally), the submodule will also show up as
'changed'. Then, after committing the changes, you can push them back to
the remote submodule repository via **Push** from the context menu of
the **Branches** view. Note that you may lose your work in the submodule
if you make changes on a *detached HEAD*. To avoid this, check out a
submodule branch before making the changes.

## Submodule States and Transitions


<table class="wrapped confluenceTable">
<tbody>
<tr class="header">
<th class="confluenceTh">Icon</th>
<th class="confluenceTh">State</th>
<th class="confluenceTh">Description</th>
</tr>

<tr class="odd">
<p>![](attachments/16547868/16547872.png)</p>
<td class="confluenceTd">Uninitialized</td>
<td class="confluenceTd"><p>The submodule has not yet been initialized.</p>
<ul>
<li>Use <strong>Initialize</strong> or <strong>Pull</strong> to initialize/fetch this submodule.</li>
<li>Use <strong>Deactivate</strong> to get the submodule rid from the <strong>Files</strong> view. It will only show up if <strong>View|Show Ignored Files</strong> is selected.</li>
<li>Use <strong>Unregister</strong> to remove the submodule from the repository.</li>
</ul></td>
</tr>
<tr class="even">
<p>![](attachments/16547868/16547871.png)</p>
<td class="confluenceTd">Inactive</td>
<td class="confluenceTd"><p>The submodule has been <strong>Deactivated</strong>.</p>
<ul>
<li>Use <strong>Initialize</strong> or <strong>Pull</strong> to initialize/fetch this submodule.</li>
</ul></td>
</tr>
<tr class="odd">
<p>![](attachments/16547868/16547884.png)</p>
<td class="confluenceTd">Empty</td>
<td class="confluenceTd"><p>The submodule has been initialized, but contents have not been fetched yet.</p>
<ul>
<li>Use <strong>Pull</strong> to fetch this submodule.</li>
</ul></td>
</tr>
<tr class="even">
<p>![](attachments/16547868/16547871.png)</p>
<td class="confluenceTd">As Index</td>
<td class="confluenceTd">The submodule is correctly initialized and pointing to the same commit as registered in the parent repository's HEAD and Index.</td>
</tr>
<tr class="odd">
![](attachments/16547868/16547881.png)
<td class="confluenceTd">Added</td>
<td class="confluenceTd"><p>The submodule has been scheduled for addition in the parent repository.</p>
<ul>
<li>Use <strong>Commit</strong> to confirm the addition.</li>
<li>Use <strong>Discard</strong> to unscheduled the addition.</li>
</ul></td>
</tr>
<tr class="even">
![](attachments/16547868/16547880.png)
<td class="confluenceTd">Removed</td>
<td class="confluenceTd"><p>The submodule has been scheduled for removal in the parent repository.</p>
<ul>
<li>Use <strong>Commit</strong> to confirm the removal.</li>
<li>Use <strong>Discard</strong> to unscheduled the removal and (if necessary) reset to the submodule commit registered in the parent repository.</li>
</ul></td>
</tr>
<tr class="odd">
![](attachments/16547868/16547876.png)<img src="attachments/16547868/16547878.png" data-image-src="attachments/16547868/16547878.png" data-unresolved-comment-count="0" data-linked-resource-id="16547878" data-linked-resource-version="1" data-linked-resource-type="attachment" data-linked-resource-default-alias="submodule-modified-staged.png" data-base-url="https://www.syntevo.com/doc" data-linked-resource-content-type="image/png" data-linked-resource-container-id="16547868" data-linked-resource-container-version="1" /><img src="attachments/16547868/16547877.png" data-image-src="attachments/16547868/16547877.png" data-unresolved-comment-count="0" data-linked-resource-id="16547877" data-linked-resource-version="1" data-linked-resource-type="attachment" data-linked-resource-default-alias="submodule-modified-added.png" data-base-url="https://www.syntevo.com/doc" data-linked-resource-content-type="image/png" data-linked-resource-container-id="16547868" data-linked-resource-container-version="1" />
<td class="confluenceTd">Modified</td>
<td class="confluenceTd"><p>The submodule points to a different commit than registered in the parent repository's Index. This is usually the result after e.g. you've done a commit in the submodule repository.</p>
<ul>
<li>Use <strong>Stage</strong> to stage the change in the parent repository's Index.</li>
<li>Use <strong>Commit</strong> to update the submodule link in the parent repository.</li>
<li>Use <strong>Discard</strong> to reset the submodule to the commit recorded in the parent repository's Index.</li>
<li>Use <strong>Reset</strong> to reset the submodule to the commit recorded in the parent repository's HEAD.</li>
</ul></td>
</tr>
<tr class="even">
![](attachments/16547868/16547883.png)
<td class="confluenceTd">Conflict</td>
<p>The submodule is in conflicting state where it's unclear to which commit it should point.</p>
<ul>
<li>Check the <strong>Log</strong> and make sure to <strong>Check Out</strong> the appropriate commit in the submodule repository, then confirm with <strong>Stage</strong>.</li>
<li>Use <strong>Discard</strong> to reset the submodule to the commit recorded in the parent repository's Index.</li>
<li>Use <strong>Reset</strong> to reset the submodule to the commit recorded in the parent repository's HEAD.</li>
</ul>
<p>Submodule conflicts are usually complex to resolve and may require additional commits in the submodule itself. Hence, if you are unsure, better contact the other authors of the conflicting submodule conflicts.</p>
</tr>
<tr class="odd">
![](attachments/16547868/16547879.png)
<td class="confluenceTd">Nested root</td>
<td class="confluenceTd"><p>The <em>nested Git repository</em> is not properly linked as submodule.</p>
<ul>
<li>Use <strong>Stage</strong> to scheduled the Git repository as submodule in the parent repository</li>
<li>Otherwise, if this Git repository should not be a submodule, use <strong>Ignore</strong> or completely get rid of the sub-directory.</li>
</ul></td>
</tr>
<tr class="even">
![](attachments/16547868/16547875.png)
<td class="confluenceTd">Missing</td>
<td class="confluenceTd">Might happen if initializing a submodule has failed, e.g. after cancelling the credentials dialog. Use <strong>Initialize</strong> to initialize/fetch again.</td>
</tr>
</tbody>
</table>



