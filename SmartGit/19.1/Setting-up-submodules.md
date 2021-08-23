# Setting up submodules

Git's submodules allow you to embed one Git repository within another.
This page explains how to set up submodules using SmartGit.

## Adding Submodules

New submodules can be added to an existing Git repository as follows: In
the *Repositories* view of the main window, select the folder into which
the new submodule should be inserted. Then, from the program menu select
**Remote\|Submodule\|Add**. In the wizard that shows up, specify a
folder name for the new submodule and a URL pointing to the submodule's
repository. On pressing the Finish button on the wizard's last page,
SmartGit will start checking out the submodule's contents from its
repository.

## Initializing and Updating Submodules

If you perform a Pull operation, e.g. by clicking on the Pull button in
the main toolbar, a Pull dialog will be opened. On this dialog, you can
find two submodule-related options:

-   Update registered submodules
-   And initialize new submodules

As indicated by their names, if these two options are enabled, SmartGit
will automatically update and initialize submodules, respectively, when
a Pull operation is performed. See the Git documentation on the commands
`git submodule update` and `git submodule init` for more information
about these two operations.
