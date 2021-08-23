# Log

<a id="Log-log"></a>

SmartGit's Log displays the repository's history as a list of commits,
sorted by increasing age, and with a graph on the left side to show the
parent-child relationships between the commits. What is shown on the Log
depends on what was selected when the Log command was invoked:

-   To view the history of the entire repository (*root* Log), select
    the repository in the **Repositories** view before invoking the Log
    command.
-   To view the history of a directory within the repository, select the
    directory in the **Repositories** view before invoking the Log
    command.
-   To view the history of a single file within the repository, select
    the file in the **Files** view before invoking the Log command. If
    the file is not visible in the **Files** view, either adjust the
    file table's filter settings (on its top right), or enter the name
    of the file in the search field above the file table.

A *root* Log can be invoked from other places in SmartGit as well:

-   **Branches view** In the **Branches** view (just project window),
    you can right-click on a branch and select **Log** to open the Log
    for the selected branch.
-   **Outgoing view** In the **Outgoing** view, you can right-click on a
    specific commit and invoke **Log** to open the Log for the current
    branch, with the selected commit pre-selected in the Log.

## Log Commands

In the *Log Frame*, many commands which are known from the *Project
Window* are available as well:

-   most of them are available from the main menu bar
-   the context menu on a commit provides certain commands
-   certain items in the **Graph** view, like *local refs* or the
    *HEAD*-arrow can be modified using drag-and-drop.

## Links to issue trackers

If you have set up a so called *Bugtraq Configuration*, SmartGit will
detect issue IDs in commit messages and display links to the issue
tracker in this case. The Bugtraq configuration is stored either in the
`.gitbugtraq` file in your repository root (for all users of the
repository) or in your repositories' `.git/config` (just for you). It
consists of a named `bugtraq` section which basically defines a regular
expression to match issue IDs in your commit message and an URL template
to open when clicking at such an issue link.



#### Example
>
>
>
>An example configuration for the *JIRA* issue tracker at host 'host' for
>a project called 'SG' looks like the following.
>
>
>
>``` text
>[bugtraq "jira"]
>  url = https://host/jira/browse/SG-%BUGID%
>  logRegex = SG-(\\d+)
>                        
>```
>
>
>
>Another example configuration (e.g. for a trouble ticketing system)
>where IDs like '#213' should be matched only at the beginning of a
>commit message. Note that the logregex needs to be put in quotes,
>because '#' serves as a comment character in Git configuration files.
>
>
>
>``` text
>[bugtraq "otrs"]
>  url = "https://otrs/index.pl?Action=AgentTicketZoom;TicketID=%BUGID%"
>  logregex = "^#[0-9]{1,5}"
>                        
>```
>
>
>
>

The `logRegex` must contain only one matching group '()' matching the
issue ID. You can use additional non-matching groups '(?:)' for other
parts of your regex (or '(?i)' for case insensitive matching). For more
details refer to the complete specification at
<https://github.com/mstrap/bugtraq>.
