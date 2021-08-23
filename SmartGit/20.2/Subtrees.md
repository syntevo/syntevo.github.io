# Subtrees

Subtrees allow to integrate contents from other repositories into
sub-folders of your main repository. They are an alternative to
[Submodules](Submodules.md).

## Subtrees in the UI

Refs belonging to subtrees will be denoted in the **Branches** view by a
*folder*-symbol. The root commits of a subtree will be denoted the same
way in the Log **Graph**.

## Subtree operations

To add a new subtree, select the root directory of the repository in the
**Repositories** view and invoke **Remote\|Subtree\|Add**.

To merge (or cherry-pick) a subtree use the **Merge**
(or **Cherry-Pick**) command. SmartGit will understand whether the
source commit is a subtree and in this case perform a subtree merge (or
cherry-pick).

To split changes from your main repository back to a subtree, first
**Check Out** the branch which should be split back. Then, in the
**Branches** view, select the subtree branch to which the changes should
be split back and invoke **Subtree\|Split** from the context menu. Note
that SmartGit will not actually split changes back to this particular
branch but the branch selection serves primarily to identify to which
subtree the changes should be split back. The underlying Git command
will then detect the appropriate subtree commits onto which the new
commits will be split back.

To reset your main repository to a certain subtree, first **Check Out**
the branch which should be reset. Then, in the **Branches** view, select
the subtree branch to which your main repository should be reset to and
invoke **Subtree\|Reset** from the context menu.

  


