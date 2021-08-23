# The Index

<a id="TheIndex-index"></a>

The *Index* is an intermediate cache for preparing a commit. With
SmartGit, you can make heavy use of the Index, or ignore its presence
completely - it's all up to you.

The **Stage** command allows you to save a file's content from your
working tree in the Index. If you stage a file that was previously
version-controlled, but is now missing in the working tree, it will be
marked for removal. Explicitly using the **Remove** command has the same
effect, as you may be accustomed to from SVN. If you select a file that
has Index changes, invoking **Commit** will give you the option to
commit all staged changes.

If you have staged some file changes and later modified the working tree
file again, you can use the **Discard** command to either revert the
working tree file content to the staged changes stored in the Index, or
to the file content stored in the repository (HEAD). The **Changes**
view of the SmartGit project window can show the changes between the
HEAD and the Index, between the HEAD and the working tree, or between
the Index and the working tree state of the selected file. Individual
change hunks can be staged and unstaged there.

When *unstaging* previously staged changes, the staged changes will be
moved back to the working tree, if the latter hasn't been modified in
the meantime, otherwise the staged changes will be lost. In either case,
the Index will be reverted to the HEAD file content.
