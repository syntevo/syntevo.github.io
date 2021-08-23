# Synchronizing with Remote Repositories

Synchronizing the states of local and remote repositories consists of
pulling from and pushing to the remote repositories. SmartGit also has a
Synchronize command that combines pulling and pushing.

<a id="SynchronizingwithRemoteRepositories-pull"></a>

## Pull

The Pull command fetches commits from a remote repository, stores them
in the remote branches, and optionally 'integrates' (i.e. merges or
rebases) them into the local branch.

Use **Remote\|Pull** (or the corresponding toolbar button) to invoke the
Pull command. This will open the Pull dialog, where you can specify what
SmartGit will do after the commits have been fetched: Merge the local
commits with the fetched commits or rebase the local commits onto the
fetched commits. In the latter case, you can merge or rebase by hand, as
explained in
[Merge](Working-with-Branches-and-Tags.md#WorkingwithBranchesandTags-merge)
and
[Rebase](Working-with-Branches-and-Tags.md#WorkingwithBranchesandTags-rebase),
respectively. These options are meaningless, if you select to **Fetch
Only**.

The Pull dialog allows you to set your choice as default for the current
branch. To change the default choice for new branches, go to
**Repository\|Settings**.

If a merge or rebase is performed after pulling, it may fail due to
conflicting changes. In that case SmartGit will leave the repository in
a *merging* or *rebasing* state so you can either resolve the conflicts
and proceed, or abort the operation. See
[Merge](Working-with-Branches-and-Tags.md#WorkingwithBranchesandTags-merge)
and
[Rebase](Working-with-Branches-and-Tags.md#WorkingwithBranchesandTags-rebase)
for details.

### Pulling tags

By default, Git (and hence SmartGit) will only pull new tags, but don't
update possibly changed tags from the remote repository. To have tags
updated as well, you have to configure `--tags` as `tagopt` for your
remote.



#### Example
>
>
>
>To update tags when pulling from `origin`, your `.git/config` file
>should look like the following ('... ' represents your already currently
>set values):
>
>
>
>``` text
>[remote "origin"]
>  fetch = ...
>  url = ...
>  tagopt = --tags
>                        
>```
>
>
>
>

<a id="SynchronizingwithRemoteRepositories-push"></a>

## Push

The various Push commands allow you to push (i.e. send) your local
commits to one or more remote repositories. SmartGit distinguishes
between the following Push commands:

-   **Push** Pushes all commits in one or more local branches to their
    matching remote branches. More precisely, on the Push dialog you can
    choose between pushing the commits in the current branch to its
    matching remote branch, and pushing the commits in all local
    branches with matching remote branches to said remote branches. A
    local branch \`matches' a remote branch if the branch names match,
    e.g. \`master' and \`origin/master'. With this Push command you can
    push to multiple repositories in a single invocation. SmartGit will
    detect automatically whether a *forced push* will be necessary.
-   **Push To** Pushes all commits in the current branch either to its
    matching branch, or to a *ref* specified by name. With the Push To
    command you can only push to one remote repository at a time. If
    multiple repositories have been set up, the Push To dialog will
    allow you to select the remote repository to push to. Also, the Push
    To command always allows to do a *forced* push, what can be
    convenient. This is necessary when pushing to a *secondary* remote
    repository for which forcing the push may be necessary while it is
    not when pushing to the primary remote repository (i.e. the one
    which is considered by SmartGit's *forced push* detection). You can
    also invoke Push To on a remote to push (or *synchronize*) all
    branches from the selected remote to another remote.
-   **Push Commits** Pushes the selected range of commits from the
    **Outgoing** view, rather than all commits, in the current branch to
    its tracked remote branch.

If you try to push commits from a new local branch, you will be asked
whether to set up tracking for the newly created remote branch. In most
cases it is recommended to set up tracking, as it will allow you to
receive changes from the remote repository and make use of Git's branch
synchronization mechanism (see
[Branches](Branches.md#Branches-branches)).

The Push commands listed above can be invoked from several places in
SmartGit's project window:

-   **Menu and toolbar** In the menu, you can invoke the various Pull
    commands with **Remote\|Push**, **Remote\|Push To** and
    **Remote\|Push Commits**. The first two may also be available as
    toolbar buttons, depending on your toolbar configuration. The third
    command is only enabled if the **Outgoing** view is focused.
-   **Repositories view** You can invoke **Push** in the
    **Repositories** view by selecting the open repository and choosing
    **Push** from the context menu.
-   **Branches view** In the context menu of the **Branches** view, you
    can invoke **Push** and **Push To** on local branches. Additionally,
    you can invoke **Push** on tags.
-   **Outgoing view** To push a range of commits up to a certain commit,
    select that commit in the **Outgoing** view and invoke **Push
    Commits** from the context menu.

## Synchronize

With the Synchronize command, you can push local commits to a remote
repository and pull commits from that repository at the same time. This
simplifies the common workflow of separately invoking
[Push](#SynchronizingwithRemoteRepositories-push) and
[Pull](#SynchronizingwithRemoteRepositories-pull) to keep your
repository synchronized with the remote repository.

If the Synchronize command is invoked and there are both local and
remote commits, the invoked push operation fails. The pull operation on
the other hand is performed even in case of failure, so that the commits
from the remote repository are available in the tracked branch, ready to
be merged or rebased. After the remote changes have been applied to the
local branch, you may invoke the Synchronize command again.

In SmartGit's project window, the Synchronize command can be invoked as
follows:

-   from the menu via **Remote\|Synchronize**,
-   with the Synchronize toolbar button,
-   and in the **Repositories** view via **Synchronize** in the
    repository's context menu.


#### Note
>
>
>*Why does SmartGit first Push, then Pull?*
>
>SmartGit first tries to Push, then Pulls. If the Push failed because of
>remote changes, you will have the remote changes already locally
>available and can test the local changes before pushing them by invoking
>Push or Synchronize a second time.
>
>If SmartGit would first Pull and then Push, local changes either would
>be rebased on top of the pulled remote changes or remote changes
>silently merged to local changes. This would mean to push untested
>changes.
>
>
