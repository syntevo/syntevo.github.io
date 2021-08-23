<a id="InstallationandFiles-installation"></a>

# Installation and Files

SmartGit stores its settings files per-user. Each major SmartGit version
has its own default settings directory, so you can use multiple major
versions independent of each other. The location of the settings
directory depends on the operating system.

<a id="InstallationandFiles-settings-dir.default-location"></a>

## Default Location of SmartGit's Settings Directory

-   **Windows** `%APPDATA%\syntevo\SmartGit\<major-smartgit-hg-version>`
    (`%APPDATA%` is the path defined in the environment variable
    `APPDATA`)
-   **Mac OS**
    `~/Library/Preferences/SmartGit/<major-smartgit-hg-version>`
-   **Linux/Unix** `~/.smartgit/<major-smartgit-hg-version>`


#### Tip
>
>
>You can change the directory where the settings files are stored by
>changing the property
>[smartgit.settings](VM-options.md#VMoptions-settings-dir.change-location).
>
>

## Notable Files in the Settings Directory

-   `license` stores your SmartGit *license key*.
-   `log.txt` contains debug log information. It can be configured via
    `log4j.properties`. You may remove this file: afterwards, SmartGit
    will return to its default logging settings.
-   `passwords` is an encrypted file and stores the *passwords* used
    throughout SmartGit. You may remove this file: afterwards, all
    passwords are lost.
-   `accelerators.xml` stores the *accelerators* configuration. You may
    remove this file: afterwards, all accelerators will be reset to
    their defaults.
-   `credentials.xml` stores authentication information (not including
    the corresponding passwords). You probably do not want to remove
    this file: afterwards, all credentials (user names, private keys,
    certificates) will be lost.
-   `hostingProviders.xml` stores information about configured hosting
    provider accounts (not including the corresponding passwords). You
    probably do not want to remove this file: afterwards, all connect
    details for all hosting provides will be lost.
-   `notifications.xml` stores information about the state of
    notifications which show up in the status bar in various cases. You
    may remove this file: afterwards, various notifications may show up
    again.
-   `projects.xml` stored all former *SmartGit projects* (up to
    SmartGit 5) including their settings. Beside that it contains all
    repository root specific settings.
-   `repositories.xml` stores the information about known repositories,
    their names and repository groups.
-   `repository-cache.xml` stores all cached information about
    repository states, e.g. what local branch is checked out, whether
    there are incoming or outgoing changes.
-   `settings.xml` stores the application-wide settings (e.g. the
    preferences) of SmartGit. You should not remove this file, unless
    you want to completely reset SmartGit.
-   `tools.xml` stores *external* tools which have been configured in
    the Preferences. You probably do not want to remove this file:
    afterwards, all you external tools configurations will be lost.
-   `ui-config.xml` stores UI related, more stable settings, e.g. the
    toolbar configurations. You may remove this file: afterwards,
    various aspects of the UI will be reset to defaults.
-   `ui-settings.xml` stores UI related, volatile settings, e.g. window
    sizes or column widths. You may remove this file: afterwards,
    various aspects of the UI will be reset to defaults.

## Program Updates

SmartGit stores program updates which have been downloaded automatically
through SmartGit itself by default in the subdirectory `updates` of the
*Settings* root directory (see [Default Location of SmartGit's Settings Directory](#InstallationandFiles-settings-dir.default-location)). This
allows quick, *patch-like* updates which do not require write access to
the actual SmartGit installation. As a consequence, your SmartGit
installation is usually not up-to-date, if you are missing the `updates`
directory.


#### Tip
>
>
>If you prefer to keep your SmartGit installation always up-to-date, you
>can select **Force upgrading installation directory** in the
>Preferences, section **SmartGit Updates**.
>
>

The root directory of the *Updates* directory contains sub-directories
for every major version. Such a *major version* directory contains a
`control` file for the latest downloaded build and a `current`-file
which points to the currently used build. Usually, this will be the
highest build which shows up in this directory. The `control`-file only
*configures* which binaries are part of the build by linking to the
actual binaries which are stored in the `repo`-subdirectory and which
are shared among all builds.


#### Warning
>
>
>By modifying the `control` file or any other contents within the
>*Updates* directory, you may easily screw up your SmartGit installation.
>Hence, do not touch these files unless you have good reasons to do so.
>
>

## Company-wide Installation

For company-wide installations, the administrator may install SmartGit
on a read-only location or network share. To ease deployment and initial
configuration for the users, certain settings files can be prepared and
put into a directory named `default`. For Mac OS X this `default`
directory must be located in `SmartGit.app/Contents/Resources/`
(parallel to the `Java` directory), for other operating systems within
SmartGit's installation directory (parallel to the `lib` and `bin`
directories).

When a user starts SmartGit for the first time, the following files will
be copied from the `default` directory (on the network share) to the
user's personal SmartGit settings directory (refer to [Default Location of SmartGit's Settings Directory](#InstallationandFiles-settings-dir.default-location)):

-   `accelerators.xml`
-   `credentials.xml`
-   `hostingProviders.xml`
-   `repository.xml`
-   `settings.xml`
-   `tools.xml`
-   `ui-config.xml`
-   `ui-settings.xml`

The `license` file (only for *Enterprise* licenses and 10+ users
*Professional* licenses) can also be placed into the `default`
directory. In the latter case, SmartGit will prefill the **License**
field in the **Set Up** wizard when a user starts SmartGit for the first
time. When upgrading SmartGit, this `license` file will also be used, so
users won't be prompted with a 'license expired' message, but can
continue working seamlessly.


#### Note
>
>
>Typically, you will receive license files from us wrapped into a *ZIP*
>archive. In this case you have to unzip the contained `license` file
>into the `default` directory.
>
>

## JRE Search Order (Windows)

On Windows, the `smartgit.exe` launcher will search for a suitable JRE
in the following order (from top to bottom):

-   Environment variable SMARTGIT_JAVA_HOME
-   Subdirectory `jre` within SmartGit's installation directory
-   Environment variable JAVA_HOME
-   Environment variable JDK_HOME
-   Registry key HKEY_LOCAL_MACHINE\\SOFTWARE\\JavaSoft\\Java Runtime
    Environment
