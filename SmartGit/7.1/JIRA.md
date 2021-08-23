# JIRA

The JIRA integration allows to select a commit message (including JIRA
key) directly from (open) JIRA issues and to optionally mark issues as
resolved on **Push**.

## Prerequisites

The JIRA integration will only be present, if the [Bugtraq configuration](Bugtraq-links-to-issue-trackers-.md) has been set up
properly for your JIRA server and a commercial license is registered in
SmartGit.

## Commit Message Selection

The commit message selection is available in the Commit and Edit Last
Commit Message commands as well in some interactive rebase commands of
the **Outgoing** view.

![](attachments/2719880/2719881.png)

## Resolving on Push

For all **Push** operations (except of **Push To**), SmartGit checks the
pushed commits for *affected* JIRA issues and offers to mark them as
resolved in one or more JIRA versions. A JIRA issue is considered as
*affected*, if

1.  It's mentioned in at least one commit message of the *local* branch
    commits which are pushed; and
2.  It's not mentioned in any commit message of the *remote* branch
    commits which are going to be replaced; and
3.  when using Git-Flow, you are not pushing into a *feature* branch or
    a *hotfix* branch (SmartGit will ask you whether to resolve such
    commits when **Finishing** the feature or hotfix, i.e. integrating
    the commits into `develop` or `master`).



This functionality can be disabled using [system properties](System-Properties.md#smartgitrevertcommitmessagetemplatejira).



## Support for 'commit.template'

The JIRA integration will honor the Git `commit.template` configuration.
Following keywords are substituted by the according JIRA issue
attributes:

-   `%BUGID%`
-   `%BUGSUMMARY%`
-   `%BUGDESCRIPTION%`


