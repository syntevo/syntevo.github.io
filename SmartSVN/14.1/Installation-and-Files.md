# Installation and Files

SmartSVN stores its configuration files per-user. The root directory of
SmartSVN's configuration area contains subdirectories for every major
SmartSVN version, so you can use multiple versions concurrently. The
location of the configuration root directory depends on the operating
system.

## Location of SmartSVN's settings directory

-   **Windows:** The configuration files are located below
    `%APPDATA%\syntevo\SmartSVN\<major-version>`\\. Note: Before
    SmartSVN 5, configurations files have been stored below
    `%USERPROFILE%\.smartsvn\`.
-   **Mac OS:** The configuration files are located below
    `~/Library/Preferences/SmartSVN/<major-version>/`.
-   **Unix/Other:** The configuration files are located below
    `~/.smartsvn`/`<major-version>`/.


#### Tip
>
>
>You can change the directory where the settings files are stored by
>changing the property
>[smartsvn.settings](VM-Options.md#location-of-the-settings-directory).
>
>

## Notable configuration files

-   `accelerators.xml` stores the accelerators configuration.
-   `license` stores your SmartSVN's *license key*.
-   `log.txt` contains debug log information. It's configured via
    `log4j.xml`.
-   `passwords` is an encrypted file and stores the passwords used
    throughout SmartSVN.
-   `project-defaults.xml` stores the [default project settings](Project-Settings.md#default-settings).
-   `projects.xml` stores all configured
    [projects](Projects.md#Projects-project), including their
    settings.
-   `repositories.xml` stores the repository credentials, except the
    corresponding passwords.
-   `settings.xml` stores the application-wide
    [Preferences](Preferences.md#Preferences-preferences) of
    SmartSVN.
-   `tag-branch-layouts.xml` stores the configured Tag-Branch-Layouts .
-   `tools.xml` stores *external* tools which have been configured in
    the Preferences. You probably do not want to remove this file:
    afterwards, all you external tools configurations will be lost.
-   `transactionsFrame.xml` stores the configuration of the
    [Transactions frame](Transactions-Frame.md#TransactionsFrame-transactions-frame)
    .
-   `ui-config.xml` stores UI related, more stable settings, e.g. the
    toolbar configurations. You may remove this file: afterwards,
    various aspects of the UI will be reset to defaults.
-   `ui-settings.xml` stores UI related, volatile settings, e.g. window
    sizes or column widths. You may remove this file: afterwards,
    various aspects of the UI will be reset to defaults.

## Program Updates

SmartSVN stores program updates which have been downloaded automatically
through SmartSVN itself by default in the subdirectory `updates` of the
*Settings* root directory). This allows light-weight, *patch-like*
updates which do not require write access to the actual SmartSVN
installation directory. As a consequence, your SmartSVN installation
directory is usually not up-to-date, but it will launch the downloaded
updates from the `updates` directory.

### Technical Details

The root directory of the *Updates* directory contains sub-directories
for every major version. Such a *major version* directory contains a
`control` file for the latest downloaded build and a `current`-file
which points to the currently used build. Usually, this will be the
highest build which shows up in this directory. The `control`-file only
*configures* which binaries are part of the build by linking to the
actual binaries which are stored in the `repo`-subdirectory and which
are shared among all builds.

Each new build has a corresponding, digitally-signed control file which
contains information about all required application files with their
download location and the expected file content hash. To reduce
band-width, application files only will be downloaded if they are not
yet locally available. After download, the content will be verified with
the hash from the control file.

When starting SmartSVN, the `bootloader.jar` from the installation
directory is launched. This uses the `control` file from the *Updates*
directory to determine which updated SmartSVN files to launch that
contain the actual application code.


#### Warning
>
>
>By modifying the `control` file or any other contents within the
>*Updates* directory, you may easily screw up your SmartSVN installation.
>Hence, do not touch these files unless you have good reasons to do so.
>
>

## Company-wide installation

For company-wide installations, the administrator can install SmartSVN
on a network share. To make deployment and initial configuration for the
users easier, certain configuration files can be prepared and put into
the subdirectory `default` (within SmartSVN's installation directory).
For Mac OS X this `default` directory must be located in
`SmartGit.app/Contents/Resources/` (parallel to the `Java` directory),
for other operating systems within SmartGit's installation directory
(parallel to the `lib` and `bin` directories).

When a user starts SmartSVN for the first time, following files will be
copied from the `default` directory to his private configuration area:

-   `accelerators.xml`
-   `project-defaults.xml`
-   `repositories.xml`
-   `settings.xml`
-   `tag-branch-layouts.xml`
-   `tools.xml`
-   `transactionsFrame.xml`
-   `ui-config.xml`
-   `ui-settings.xml`

The `license` file (only for *Enterprise* licenses and 10+ users
*Professional* licenses) can also be placed into the `default`
directory. In this case, SmartSVN will prefill the **License** field in
the **Set Up** wizard when a user starts SmartSVN for the first time.
When upgrading SmartSVN, this `license` file will also be used, so users
won't be prompted with an 'license expired' message, but can continue
working seamlessly.


#### Note
>
>
>Typically, you will receive license files from us wrapped into a *ZIP*
>archive. In this case you have to unzip the contained `license` file
>into the `default` directory.
>
>

## JRE search order (Windows)

On Windows, the `smartsvn.exe` launcher will search for an appropriate
JRE in the following order (from top to bottom):

-   Environment variable SMARTSVN_JAVA_HOME
-   Sub-directory `jre` within SmartSVN's installation directory
-   Environment variable JAVA_HOME
-   Environment variable JDK_HOME
-   Registry key HKEY_LOCAL_MACHINE\\SOFTWARE\\JavaSoft\\Java Runtime
    Environment
