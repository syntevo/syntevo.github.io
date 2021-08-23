# Repository-Related

SmartGit remembers opened repositories and a (primarily) GUI-related
settings, too. To open a repository, double-click it. If it already is
open when double-clicking, the window with the opened repository will
become visible. The repository will open in a new window if the current
window is currently executing commands or **Open in New Window** from
the repository's context menu has been selected. To open multiple
repositories at once, use multiple selection (e.g. Ctrl/Cmd+click) and
**Open** from the context menu.

Repositories can be arranged in groups. To create a new group, use
**Repository\|Add Group**. To move repositories to another group or out
of any group, either use drag-and-drop (either on the target group or a
repository inside the target group) or **Move Into or Out of Group**
context menu item.

Repositories can be marked as favorite using the **Mark as Favorite**
(**Unmark as Favorite**). Favorite repositories are indicated with an
asterisk after the name and are sorted before groups which are sorted
before non-favorite repositories. Beside that a couple of background
refresh operations are performed on favorite repositories.

## Opening a Repository

Use **Repository\|Add or Create** to either open an existing local
repository (e.g. initialized or cloned with the Git or Hg command line
client) or to initialize a new repository.

You need to specify which local directory you want to open. If the
specified directory is not a Git or Mercurial repository yet, you have
the option to initialize it.

## Cloning a Repository

Use **Repository\|Clone** to create a clone of another Git, Mercurial or
SVN repository.

Specify the repository to clone either as a remote URL (e.g.
ssh://user@server:port/path), or, if the repository is locally available
on your file system, as a file path. In the **Selection** step you can
configure whether submodules should be fetched as well: usually you will
have this option selected, because submodules are an integral part of
the main repository you are cloning. You should deselect this option
only, if you do not wish to receive certain submodules. For details,
refer to [Submodules](Submodules.md#Submodules-submodules).
Similarly, you will want to fetch the entire repository usually,
including all heads and tags. If you are only interested in a specific
head (branch) or tag, you may restrict the clone here. Note that a few
Git commands do not work properly for such partial repositories (e.g.
Pull with Rebase). In the subsequent steps you have to provide the path
to the local directory where the clone should be created and the project
to which the repository should be assigned.

## Settings

Use **Repository\|Settings** to configure certain repository-specific
settings.

On the first page you find options related to the [Pull command](Synchronizing-with-Remote-Repositories.md#pull)
.

On the second page you can configure your name and email address that
will be used when
[committing](Local-Operations-on-the-Working-Tree.md#commit)
for this repository. To change the global settings (for all
repositories, in your `.gitconfig`), select **Remember as default**.

On the third page you can configure which text encoding SmartGit should
assume when showing text files in the **Changes** view or **Compare**
window. A lot of UTF-8 encoded text files, with or without byte order
mark (BOM), can be detected automatically.
