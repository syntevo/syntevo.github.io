# System Properties

The vast majority of SmartGit's system properties can be configured by
editing the file `smartgit.properties` in the settings directory.


#### Note
>
>
>The file `smartgit.properties` contains only settings for SmartGit
>itself. If you want to configure your Git repositories, have a look at
>the various Git configuration files instead, such as `.git/config` for
>the configuration of individual Git repositories, and `~\.gitconfig` (in
>your HOME directory) for global configuration options.
>
>

First, open the settings directory. Its default location is described in
[Default Location of SmartGit's Settings Directory](Installation-and-Files.md#default-location-of-smartgits-settings-directory).
In the settings directory, you will find the `smartgit.properties` file.
Open it with a text editor, such as Windows Notepad.

Each of the settings in `smartgit.properties` is specified on a separate
line, according to the following syntax: `key=value`. If a line starts
with`#`, the entire line is treated as a comment and ignored by the
program.

The following list shows the available system property keys:

## Interaction with Git

### smartgit.executable.home

By default, Git will search for user configuration files (primarily
`.gitconfig`) in the directory specified by the `$HOME` environment
variable.

Sometimes `$HOME` passed to SmartGit might not be identical to `$HOME`
available from command line due to specific system configurations. To
make SmartGit use the same configuration anyway, specify this property.

Sometimes `$HOME` might point to a network location which may result in
performance problems. In this case, you should create a local *HOME*
directory to use for SmartGit, replicate your `.gitconfig` into this
directory and finally point SmartGit to this directory using
`smartgit.executable.home`.



#### Example
>
>
>
>This specifies a different *HOME*-directory on Linux/Mac:
>
>
>
>``` text
>smartgit.executable.home=/path/to/home
>                        
>```
>
>
>
>This specifies a different *HOME*-directory on Windows (make sure to use
>forward slashes):
>
>
>
>``` text
>smartgit.executable.home=c:/Documents and Settings/user/App Data/syntevo/SmartGit/home
>                        
>```
>
>
>
>

### smartgit.executable.language

By default, SmartGit will invoke Git with environment variable `LANG=C`
set. Use this system property to change the language passed to Git, for
example: `smartgit.executable.language=en_EN.UTF-8`. To skip the `LANG`
environment variable, set `smartgit.executable.language=`.

### smartgit.core.jgit.streamFileThreshold

This option roughly specifies the maximum Git object size (in MB) to be
loaded directly into memory. This helps to avoid out-of-memory-errors,
but on the other hand certain operations may become extremely slow. This
value may be used to tune performance, but it should be chosen with
care!

### smartgit.core.merge.shortCommitMessage

When merging, Git's verbose default messages are used. If you prefer
shorter, easier readable messages (as default until SmartGit 5), set
this value to `true`.

### smartgit.core.push.recurseSubmodulesCheck

By default, SmartGit invokes "git push" using the
"--recurse-submodules=check" option (Git 1.7.7 and above).

-   To always push required submodules instead of warning, set this
    option to `on-demand`.
-   To disable the check for not yet pushed submodule commits which are
    referenced in the parent repository, set this option to `false`.

### smartgit.core.push.onlyToFirstMatchingTarget

By default, SmartGit will push to all branches which have been declared
by (multiple) `remote.<name>.push` declarations (like command line Git
does). To make SmartGit stop after pushing to the first branch, set this
option to `true`.

### smartgit.core.shortShaLength

This option specifies the *short* SHA length, to be used by SmartGit
(mainly for displaying). Valid values are in the range between `4` to
`40`.

### smartgit.projectState.enabled

By default, SmartGit will scan for outgoing commits. This may slow down
the program for large repositories. To disable the scan, set the value
to `false`.

### smartgit.refresh.scanIntoSubmodules

Set to `false` to make the Refresh skip scanning submodule folders.

### smartgit.refresh.checkAssumeUnchangedFiles

By default, SmartGit will check whether 'assume-unchanged' files are
really unchanged or not. To disable this check, set the option to
`false`.

### smartgit.refresh.inspectEol

Set to `true` to have SmartGit distinguish between content and EOL-only
changes, in addition to the plain *modified* state which Git reports (in
either case, files which Git considers as *modified* will be reported).
If you do not want Git to care about EOLs at all (that's usually the
case if you are on Windows), you might want to use
core.autocrlf or text and eol attributes.

### smartgit.storeProjectPathRelativeToApplicationRoot

If set to `true`, repository paths are stored relative to the SmartGit
install location (useful for portable bundles).

### smartgit.core.jgit.similarityFileSizeLimit

The detection of renamed files is by default disabled for very large
files. Use this option to adjust when a file is considered 'large'. The
value should be given in bytes, like `1000000`.

### smartgit.renameDetection.similarityThreshold

Specifies the minimum required score for two files being considered as
renamed. The score value must be an integer between `0` and `100`.



#### Example
>
>
>
>Following configuration specifies to detect only *exact* renames:
>
>
>
>``` text
>smartgit.renameDetection.similarityThreshold=100
>                        
>```
>
>
>
>

### smartgit.submoduleUpdate.useGit

By default, SmartGit is rather conservative when updating submodules:
for instance modified submodules won't be touched, even if the
registered commit in the parent repository has changed. Sometimes it may
be convenient to still 'update' these submodules, e.g. by merging local
commits with the changed, registered commit. This is what 'git submodule
update' will do, if key 'submodule.$name.update' is properly configured
in .git/config of the parent repository. To invoke 'git submodule
update' for modified submodules, set this value to `true`.

### smartgit.core.clone.noHardLinks

If you are encountering problems when cloning a local repository to/from
a mapped network drive, it may be necessary to add '--no-hardlinks' for
'git clone'. To achieve that, set this option to `true`. Do not forget
to reset the option, once you have cloned successfully.

### smartgit.ssh.defaultUser

If an SSH-URL does not contain 'user@', SmartGit will by default use the
system user name to authenticate at the SSH server. Use this property to
change to a custom default user name.

### smartgit.branch.otherRefs

Use this option to configure additional other refs to be displayed in
the Branches view; the default value is `notes`. To include e.g.
*archive*-refs, set to `notes;archive`.

### smartgit.branch.tagExcludeRegEx

To exclude certain tags from being processed by SmartGit, specify a
regular expression matching the corresponding tag names (not including
`refs/tags/`). This can be useful if you have a large amount of
auto-generated tags which may slow down various SmartGit operations,
especially related to the Log.



#### Example
>
>
>
>To exclude all tags starting with the prefix `autotag-`, specify:
>
>
>
>``` text
>smartgit.branch.tagExcludeRegEx=autotag-.*
>                        
>```
>
>
>
>

### smartgit.branch.remoteBranchExcludeRegEx

To exclude certain remote branches from being processed by SmartGit,
specify a regular expression matching the corresponding remote branch
names (not including `refs/remotes/<remote>`). For details,
see `smartgit.branch.tagExcludeRegEx`.

### smartgit.revert.commitMessageTemplate

Use this option to customize the commit message used by the **Revert**
command: `${message}` will be substituted by the commit's message,
`${sha}` will be substituted by the commit's SHA and `\\n` will be
substituted by a newline character.



#### Example
>
>
>
>To get the same commit message as set by command line Git, use:
>
>
>
>``` text
>                          smartgit.revert.commitMessageTemplate=revert "${message}"\n\nThis reverts commit ${sha}.
>                        
>```
>
>
>
>

### smartgit.gitflow.finishFeature.message

Use this option to customize the default commit message used by the
**Finish Feature** command. `{0}` will be substituted with the feature
name.



Example:



``` java
smartgit.gitflow.finishFeature.message=Finished feature {0}.
```





 

### smartgit.gitflow.tagLastReleaseCommitInsteadOfMaster, smartgit.gitflow.tagLastHotfixCommitInsteadOfMaster

Set the appropriate option to `true` to make SmartGit tag the last
release/hotfix commit instead of the subsequent merge commit on `master`
when [finishing a Git-Flow release or hotfix](Git-Flow.md).

### smartgit.rebase.disablePreserveMerges

Set this option to `true` to skip `--preserve-merges` option even if
SmartGit has detected that one of the commits to rebase is a merge
commit.

## SVN integration

### smartgit.clone.svnAllowed

Set to false to disable the possibility to clone SVN repositories.

### smartgit.defaultConnectionLogging

Set to `true` to have SVN connection logging enabled. This will create a
connection.log in SmartGit's settings directory which will be helpful
for error diagnosis.

### smartgit.svn.gitAttributesSizeThreshold

For certain SVN repositories, the .gitattributes file may become very
large, which would slow down various (Smart)Git operations. For that
reason, the mapping of svn:eol-style and svn:mime-type will be disabled
if the size of the .gitattributes file exceeds the threshold specified
by the specified value (in bytes). For more information, see
http://www.syntevo.com/smartgit/documentation.html?page=concepts-svn To
have the .gitattributes mapping always enabled, you may set the
threshold to a large value.

### smartgit.submoduleRecurseInUnchangedSvn

Set to `true` to enable recursion into unchanged SVN submodules when a
submodule update is performed. This may be useful if you always want to
fetch the latest revisions from an SVN repository even if the
svn:external which is mapped to .gitsvnextmodules does require fetching
these revisions.

### smartgit.svn.glueFeature

Set to `false` to prevent glueing of multiple revisions together when
performing an SVN clone. Glueing revisions together improves performance
and usually has no negative side-effects. Sometimes, for large
repositories, it may result in out-of-memory errors, though.

### smartgit.svn.scanSubmodulesForNonSvnParents

Set to `true` to scan (refresh) SVN sub-modules for non-SVN parent
repositories.

### smartgit.svn.defaultCommitMessage

Use this option to change the default SVN "commit message" when e.g.
pushing a tag. There are a couple of variables, which will be replaced
by proper strings:` {Action}, {Actiond}`, `{action}`, `{actiond}`,
`{target}`, `{source}`, `{sourceRevision}`.

     



#### Example
>
>
>
>Some example definitions:
>
>
>
>``` java
>{Actiond} {target}{ from {source}{:{sourceRevision}}}
>{target} {action} { from {source}{:{sourceRevision}}}
>```
>
>
>
>

## Processes

### smartgit.filemonitor.enabled

Set to `false` to disable the file monitor (which watches for file
system changes).

### smartgit.filemonitor.excludeIgnoredDirectories

On Linux, SmartGit will by default not monitor files which are located
in ignored directories. Usually this does not cause any problems but
improves Refreshing performance and reduces required *inotify* handles.
Sometimes ignored directories are containing tracked files in which case
changes to these files might not show up automatically. If this is the
case for you, you should disable this optimization by setting this
system property to `false`.

### smartgit.filemonitor.watchNonFixedDrives

On Windows, set this option to `false` to disable file monitoring for
folders that lie on removable drives.

### smartgit.filemonitor.watchUncPaths

On Windows, set this option to `true` to enable file monitoring for UNC
paths. Depending on the network drive type, this may slow down file
monitoring and/or may not work reliably.

### smartgit.process.timeout

This setting specifies the number of seconds to wait for a response from
a hanging external process before suggesting to kill it. Among other
things, this helps to avoid hanging Git processes when trying to access
a repository.

### smartgit.disableCheckForNewVersion

Set to `true` to disable the automatic checking for new program
versions. You should only turn this check off for network installations
where SmartGit users may not be able to perform the update themselves.

Note that this will also disable notifications of new bugfix releases
which you can upgrade to for free and which improve the reliability of
SmartGit.

### smartgit.updater.directory

Use this property to customize the [program updater](Installation-and-Files.md)'s temporary directory, which is by
default located in your home directory/profile. This should only be
necessary if updating is not possible due to (file system) restrictions
in this default directory, e.g. if execution of files is prevented by
the system. On Windows, paths have to be specified using
forward-slashes, like `c:/temp`.

## Networking

### java.net.preferIPv4Stack

By default, SmartGit prefers to connect via IPv4. To connect via IPv6
instead, set this option to `false`.

### http.nonProxyHosts

Use these properties to specify servers to connect directly to,
bypassing the configured proxy, for example: `*.foo.com|localhost`.
Note, that only internal code of SmartGit is honoring
`http.nonProxyHosts`. *This does not include Git itself*.

### smartgit.proxy.configureForGit

Set this property to `false` if you have configured your http(s) proxy
in SmartGit for accessing URLs outside your network, but your
https-authenticated repositories are located inside your network and
should not be tunneled through your proxy.

### smartgit.proxy.timeout.connect and smartgit.proxy.timeout.read

These two settings specify the timeout in milliseconds for connecting to
and for reading from a proxy, respectively. Proxies may be used e.g. by
"SmartGit Updates".

## User Interface

### smartgit.accelerators.tabCtrlI

By default Ctrl+I enters a tab character. SmartGit contains code to
prevent this. To use the default behavior (disable SmartGit Ctrl+I
code), select this option to `true`.

### smartgit.browserCommand

By default the system browser is used on Windows and Mac. On Linux
common browsers are tried to find. If you want to use a certain browser,
you may set its path using this option.

### smartgit.gui.dpiFactor

By default SmartGit tries to use the right scaling factor depending on
the DPI setting of the operating system. On some systems (e.g. Linux),
though, this does not work or needs tweaking. With this option you can
set the dpiFactor to either 1 (= 100%) or 2 (200%).

### smartgit.repository.showPath

Set to `true` to show the path behind closed repositories in the
Repositories view.

### smartgit.repository.favoriteSuffix

The Repositories view indicates favorite repositories with a trailing \*
behind the repository name. With this option you can define the used
indicator, e.g. \\u2605 for a filled 5-star, \\u2606 for an outlined
5-star or \\u2665 for a heart sign.

### smartgit.branch.infoPrefix

The Branches view indicates pull requests with a leading (!) before the
branch name. With this option you can define the used indicator, e.g.
\\u21b3 for a \|\_\> arrow, \\u2709 for an envelope or \\u275e for bold
double-quotes.

### smartgit.branches.priority. \<category>=\<value>

The Branches view sorts groups in a certain order. By using these
category constants you can set different values to change the order:
plugin, flowFeatures, flowHotfixes, flowReleases, flowSupports,
localBranches, remotes, tags, stashes, metaRefs, otherRefs,
insignificantMerges, lostHeads.

### smartgit.branches.head=\<value>

The Branches view uses a unicode character to indicate the checked out
branch. If you like to change that, set this property. To add a trailing
line space, e.g., use the value `"> "`.

### smartgit.branches.head.branch=\<value>

This is similar as for smartgit.branches.head, but for the current
checked out Hg branch while a bookmark is checked out.

### smartgit.setupFinishedUrl

This setting specifies the URL to open after SmartGit has been started
for the first time and the setup wizard was completed.

### smartgit.ui.splashscreen

To hide the splash screen, set this option to `false`.

### smartgit.ui.verboseDate

By default, times from today and yesterday are shown in a short form. To
always show the date in the full form, set this option to `false`.

### smartgit.ui.verboseDate.showOnlyTimeForToday

To show only the time (i.e. without "Today") for times from today, set
this option to `false`.

### smartgit.ui.systemtray.linux.enabled

On Linux, the system tray is disabled by default due to problems with
Unity desktops. To enable the system tray, set this option to `true`.

### smartgit.ui.toolbar.textRightBesideImage

Defines where the text in toolbar buttons is shown relative to the
image.

### smartgit.pull.update-submodule-default

By default, for new Git repositories the "Update registered submodules"
option is enabled. To disable by default, set this option to `false`.

### smartgit.pull.initialize-submodule-default

By default, for new Git repositories the "And initialize new submodules"
option is enabled. To disable by default, set this option to `false`.

### smartgit.pull.defaultToFetchOnly

Set this otpion to `true` to default the Pull dialog to the Fetch
option.

### smartgit.pull.defaultToRebase and smartgit.pull.defaultToRememberDefault

Set both options to `true` to have the Pull dialog always default to
"Rebase" and remember this as default. This will be helpful to fix Merge
vs. Rebase settings after upgrading to SmartGit 4.

### smartgit.annotate.maxToolTipWidth

In the Annotate window, if the mouse hovers over the yellow line detail
column, a tooltip with additional information is shown. With this
property you can specify a maximum width in pixels for this tooltip. The
specified value must lie in the range \[10; 1000\]. If the value is not
specified or out of range, the default value of 400 pixels is used.

### smartgit.annotate.maxComboboxMessageLength

In the Annotate window, commit messages are displayed in the combobox in
the upper part of the window. This property limits the length of the
displayed commit messages, i.e. all commit messages that are longer than
this property's value will be truncated.

### smartgit.tree.forceFullSelection

Defines whether the tree views throughout the program should use "full
selection" style. "Full selection" means that when an item on a tree is
selected, the selection box will fill the entire width of the tree,
rather than only the item's width.

### smartgit.ui.useColorsIfSelected

Defines whether tree or table views are allowed to use colors other than
the system's default background and foreground color to display selected
items. Depending on the current platform, the usage of additional colors
is disabled by default to improve the readability of selected items.

### smartgit.pushableCommits.limit

The number of entries in the Outgoing view is limited for performance
reasons. Use this option to change the limit.

### smartgit.pushableCommits.includeMirrorRemotes

Usually, secondary remotes which have "mirror" set to "true" in the
.git/config are not interesting from the perspective of which commits
are pushable and hence are ignored. Set this option to `true` to also
have these remotes honored as well.

### smartgit.pushableCommits.preserveAuthorDate

Set this option to `false` to let SmartGit adjust the author dates when
rearranging commits.

### smartgit.reveal.commandLine

"Reveal in File Manager" by default uses hard-coded, platform-specific
file managers (Windows: Explorer, OS X: Finder, Linux: Nautilus).
Depending on your file manager, you may use the placeholder ${filePath}
or ${fileUri}.

### smartgit.repository.makeNameUnique

When creating a new repository, e.g. by dropping a directory onto the
*Repositories* view, SmartGit will use the directory name as name for
the repository. This could lead to equally named repositories. When
setting this option to `true`, SmartGit will append number suffixes to
ensure that the new repository names don't collide with already existing
ones.

### smartgit.forceActive, smartgit.forceActive.dialog and smartgit.forceActive.window

Set one of these options to `true` to forcibly make new windows/dialogs
active.

### smartgit.flatLook

Set this option to `true` to use a lighter color for the border of view
controls.

## Text editors / File Comparison

### smartgit.compare.skipBinaryComparison

To disable the comparison of binary files set this option to `true`.
This may be useful if you usually have large binary files in your
repository. When read, these files may slow down certain views, e.g. the
"Changes" view.

### smartgit.compare.maximumFileSize

By default, the file comparison is disabled for very large files. Use
this setting to adjust at what size (in bytes) a file is considered 'too
large'.

### smartgit.compare.text.maxLineLength

By default, the file comparison treats files with very long lines as
binary files for performance reasons. Use this option to configure the
maximum characters per line (default: 10000) which should be treated as
text files.

### smartgit.compare.innerLine.maximumLineLength and smartgit.compare.innerLine.maximumLongLineCount

The file comparison algorithm consists of two phases. In the first
phase, changed lines are detected, and in the second phase, the
algorithm will search for changes within corresponding lines. The second
phase becomes slower if there are too many long lines, so it is skipped
when that happens. These settings allow you to adjust the detection of
long lines: The second phase is skipped if the two files contain more
than 'maximumLongLineCount' lines that are longer than
'maximumLineLength' characters in length.

### smartgit.textEditors.syntaxHighlighting

Set this option to `false` to switch syntax highlighting off
permanently, regardless of Preferences settings.

## Log

### smartgit.log.detectRenames

Set to `false` to disable the detection of renamed files in the Log. In
rare cases (large commits with many additions and removals and large
files), rename detection may slow down the Log significantly.

### smartgit.log.showAllRefsForOnBranches

Set to `true` line if you want to include all refs for the "On Branches"
display in the Log Details view.

### smartgit.log.showStashes

By default, the Log shows stashes. To change this, set to `false`.

### smartgit.log.branchPriorities

Use this option to change the priorities of Git-Flow branch types in the
Log. The priorities are affecting the order in which these branches will
be displayed in the Log graph. The order is specified using a
comma-separated list of following branch categories where every category
must occur exactly once in the list: `develop`, `feature`, `release`,
`master`, `hotfix`, `support`.



#### Example
>
>
>
>To layout in the inverse default order, specify:
>
>
>
>``` text
>smartgit.log.branchPriorities=support,hotfix,master,release,feature,develop                       
>```
>
>
>
>

### smartgit.log.commitMessage.shortLimit

SmartGit uses a shortened commit message in various places, e.g. in the
commit message column of the Log table. Shortening means the full commit
message is cut off after the number of characters specified by this
setting.

### smartgit.commit.message.useSystemEncoding

By default, commit messages are UTF-8 encoded. To use the default
encoding for your platform instead, set to `true`.

### smartgit.log.onlyHead

Set this system property to `true` if you are having performance- or
memory-related problems when showing a *File* or *Sub-Directory* Log for
a *huge* repository: by default, SmartGit will run the log for all
branches and tags. This is necessary to e.g. properly assign
branches/tags to the File or Sub-Directory commits. Also, by default,
you will be able to toggle Log roots in the **Branches** view. When
setting this option, SmartGit will only log the current *HEAD* commit
and the **Branches** view will remain empty.

### smartgit.log.stopAtAdditions

Set this system property to `false` to not stop logging a file once
SmartGit has encountered an addition of the file. This will make
SmartGit report additional commits for which a file with the same name
has been changed. Note however, that these files are usually not
related.

### smartgit.log.graph.layoutActions

When setting this system property to `true`, you will get additional
layouting actions in the context menu of the [Log](Log.md) graph. **Max.
Connector Length** specifies the maximum length a continuous connector
may have; if the length would exceed this limit, SmartGit will use
*arrows*. **Rectilinearity** affects how straight connectors will be
(degree of "bending"). Once you have a set of parameters which works
fine for you, you can skip the system property again. The configuration
is stored in the `settings.xml` configuration file and can be edited
there directly, too.

### System property "smartgit.log.branchPriorities" to specify order of Git-Flow refs in Log

### smartgit.cherryPick.shaPrefix

Git's cherry-pick command has an -x option that tells Git to
automatically append a "cherry picked from commit ..." message to the
created commits, in order to indicate where the latter came from.
SmartGit does not do this by default, but you can enable it by setting
this propery to `cherry picked from commit`.

### smartgit.avatar.size

To change the size of the avatar image, change this option.

### smartgit.avatar.serverUrl=http://www.gravatar.com/avatar/{0}.jpg?s={1}

If you want to use a different server than gravatar.com to provide the
avatars shown in the log, you may configure it in the next line.

-   {0} will be replaced by the MD5-hash of the lowercase email
-   {1} will be replaced by the avatar size (see above)

### smartgit.log.graph.\[type\].\[component\]

The colors of the graphical [Log](Log.md#Log-log)-elements can
be configured using this property. Valid `type`s are: `tag`,
`branchLocal`, `branchRemote`, `branchOther` and `headArrow`. Valid
`component`s are `red`, `green` and `blue`. Valid values are `0..255`.
Example: `smartgit.log.graph.branch.red=128`

## Journal

Following system properties can be used to customize the layout of the
[Journal](Journal-View.md) view.

### smartgit.journal.layout.maxAheadCommits, smartgit.journal.layout.maxBehindCommits, smartgit.journal.layout.maxAuxiliaryCommits, smartgit.journal.layout.maxCommonCommits

Use these system properties to increase (or lower) the maximum number of
commits displayed per type. Be careful to not use unnecessarily large
values because this may affect SmartGit's performance significantly.



#### Example
>
>
>
>To show up to 50 local commits use
>
>
>
>``` text
>smartgit.journal.layout.maxAheadCommits=50
>```
>
>
>
>

## Background operations

### smartgit.backgroundTasks.idleDelaySeconds 

When SmartGit is idle for a certain amount of time, it will start
executing various background tasks. With this option you may set the
number of seconds to wait until the 'idle' state is reached.

### smartgit.repositories.background.poll.delay 

The delay/frequency in seconds for which SmartGit will *poll*
(`git ls-remote`) remote repositories, if enabled in the
**Preferences**, section **Background Commands**.

### smartgit.repositories.background.fetch.delay 

The delay/frequency in seconds for which SmartGit will *fetch* remote
repositories, if enabled in the **Preferences**, section **Background
Commands**.

### smartgit.repositories.background.fetch.initialDelay 

The initial delay in seconds after application startup after which
SmartGit will start *fetching* remote repositories, if enabled in the
**Preferences**, section **Background Commands**. The purpose of this
delay is to alleviate the application immediately after startup, where
you will usually want to have processing power to be focused on opened
repositories (refreshing status, populating **Branches** view and
**Journal**).

### smartgit.repositories.defaultFavoriteLimit

A couple of [background commands](Preferences.md#background-commands) are
working only on repositories which have been **Marked as Favorite**. If
the amount of known repositories (listed in the **Repositories** view)
is equal or below the threshold specified by this property, all
repositories will be considered as *favorite*.



#### Example
>
>
>
>To disable automatic favorite repositories, use:
>
>
>
>``` text
>smartgit.repositories.defaultFavoriteLimit=0
>```
>
>
>
>

### smartgit.cleanup.maxAllowedLooseObjects

The maximum number of objects which are allowed before SmartGit will
suggest to **Clean Up** the repository (i.e. run `git gc`). If you are
frequently seeing the **Clean up** notification this may be caused by
high activity in your local repository. To get rid of the notifications
in this case, you may increase this system property. **Note**: you
shouldn't set this value too high, otherwise the clean up won't be
triggered anymore by SmartGit.

## GitHub integration

### smartgit.github.pullRequestPageLimit

The number of pull requests to fetch from GitHub is limited by "pages"
(one page contains a couple of pull requests). The default page limit is
3.

### smartgit.github.commentPageLimit

The number of comments to fetch from GitHub is limited by "pages" (one
page contains a couple of comments). The default page limit is 3.

### smartgit.github.perPageLimit

The number of objects per page retrieved from the server (default: 100).

## BitBucket integration

### smartgit.bitbucket.useHttps

Set to `true` to force SmartGit to connect to repositories using
*HTTPS*, instead of *SSH*.

## JIRA integration

### smartgit.jira.resolveOnPush

Set to `false` to disable optional resolving of [JIRA](JIRA.md) issues on
[Push](Synchronizing-with-Remote-Repositories.md).

### smartgit.jira.closedStates

Specifies the name of the JIRA states which are considered as *closed*:
SmartGit will only offer to resolve an issue, if the issue is not yet in
a *closed* state and there is at least one *transition* available for
the issue which puts into a *closed* state.



#### Example
>
>
>
>Default closed states are `resolved,closed,done`.
>
>

## Update Check

### smartgit.updateCheck

Set to `false` to disable the check for new versions on a global level
which can be convenient e.g. for network installations. To disable the
check for an individual installation/user, better do that in
the **Preferences**, section **SmartGit Updates**.

### smartgit.updateCheck.force

Set to `true` to force the check for new versions more often than the
specified interval in the **Preferences**, section **SmartGit Updates**.

### smartgit.updateCheck.alwaysUpgradeToLatestBuild

Set to `true` to make SmartGit check for the availability of a
new *latest build* on start up. *Latest Builds* are the "bleeding edge"
builds between subsequent (minor) *release* builds, like between version
8.0.1 and 8.0.2 or 8.1 preview 3 and 8.1 preview 4. They will contain
the latest improvements and bugfixes. Usually we will ask you to
manually fetch the latest build using **Help\|Check for Latest Builds**.

## License seat tracking

For licenses with a large number of seats, it can be helpful to track
the number of monthly used seats. For this purpose, SmartGit can
optionally ping a customizable URL which can be used to collect these
seat statistics on the server side. A simple implementation on the
server-side would just be a virtual host logging to a separate access
log file. The resulting log files can be analyzed using e.g. `grep` on a
monthly basis.

### smartgit.license.serverPing.url

Enables the license seat tracking feature and specifies the URL
(template) which SmartGit will connect to on startup and once per day.
The template is basically a URL for which following keywords will be
replaced:

-   `${email}` will be replaced by the user's email found in
    the `~/.gitconfig` file.
-   `${prop.x}` will be replaced by the Java system property `x`. For
    instance, `${prop.user.name}` will be replaced by the Java system
    property `user.name`.
-   `${env.X}` will be replaced by the environment variable `X`. For
    instance, `${env.USERID}` will be replaced by the environment
    variable `USERID`.

### smartgit.license.serverPing.method

Specifies the HTTP request method to be used, either `GET` or `HTTP`
(defaults to `GET`).



#### Example
>
>
>
>Following configuration will track seats on (including a custom `USERID`
>environment variable) at `syntevo.com`.
>
>
>
>``` text
>smartgit.license.serverPing.method=get
>smartgit.license.serverPing.url=http://www.syntevo.com/smartgit/server-ping?email=${email}&name=${prop.user.name}&id=${env.USERID}                  
>```
>
>
>
>

## Debug Properties

### log4j.\[category\]

Use this property to enable debug logging for certain SmartGit modules;
`[category]` has to be replaced by the appropriate module identifier.



#### Example
>
>
>
>To enable debug logging for the Refreshing modules, set following
>properties:
>
>
>
>``` text
>log4j.smartgit.refresh=DEBUG
>log4j.sc.vcs.model.refresh=DEBUG
>                    
>```
>
>
>
>

 

### smartgit.repositories.background.fetch.delay 

The delay/frequency in minutes for which SmartGit will fetch remote
repositories, if enabled in the **Preferences**, section **Background
Commands**

 
