# VM options

Certain configuration of SmartGit has to be done by *VM options*, in
files called `smartgit.vmoptions`. Usually you will want to specify VM
options just for your account (current user):

-   **Windows:** `%APPDATA%\syntevo\SmartGit\smartgit.vmoptions`
    (`%APPDATA%` is the path defined in the environment variable
    `APPDATA`)
-   **Linux:** `~/.smartgit/smartgit.vmoptions`
-   **Mac:** `~/Library/Preferences/SmartGit/smartgit.vmoptions`

Alternatively (but **not recommended**), VM options can also be
specified system-wide in following files:

-   **Windows:** the global file is `bin\smartgit.vmoptions` in
    SmartGit's installation directory
-   **Linux:** the global file is `bin/smartgit.vmoptions` in SmartGit's
    installation directory
-   **Mac:** the global file is `Contents/MacOS/smartgit.vmoptions` in
    SmartGit's installation directory `SmartGit.app`

## Location of the Settings Directory

The *settings* contains SmartGit's settings. See [Installation and Files](Installation-and-Files.md#InstallationandFiles-installation)
for information about the default location and contents of the settings
directory. On Windows and Linux, you can change its location by
modifying the VM option `-Dsmartgit.settings`.


#### Note
>
>
>Changing the settings directory's location is *not* supported on Mac OS
>X.
>
>

Within the value of `smartgit.settings`, certain Java system properties
are allowed, such as `user.home`. Another accepted value is the special
`smartgit.installation` property, which refers to the SmartGit
installation directory.



#### Example
>
>
>
>To tell SmartGit to store its settings in the subdirectory `.settings`
>of the SmartGit installation directory, add follow line to
>`smartgit.vmoptions`:
>
>`-Dsmartgit.settings=${smartgit.installation}\.settings` (Windows)
>
>`-Dsmartgit.settings=${smartgit.installation}/.settings` (Linux)
>
>

## Location of the Updates Directory

The *Updates* directory contains downloaded program updates. See
[Installation and Files](Installation-and-Files.md#InstallationandFiles-installation)
for information about the default location and contents of the *Updates*
directory. On Windows and Linux, you can change its location by
modifying the VM option `-Dsmartboot.sourceDirectory`.



#### Example
>
>
>
>To tell SmartGit to store its program updates in the subdirectory
>`.updates` of the SmartGit installation directory, add follow line to
>`smartgit.vmoptions`:
>
>`-Dsmartgit.settings=.updates`
>
>

## Used Java Runtime Environment

### Windows

Use the Windows environment variable `SMARTGIT_JAVA_HOME` to tell
SmartGit which JRE to use. In case of using a 64-Bit JRE, you will have
to run SmartGit using `bin/smartgit64.exe`.



#### Example
>
>
>
>To tell SmartGit to use the 64-Bit JRE located at in
>`C:\Program Files\Java\jre8`, set the environment variable
>`SMARTGIT_JAVA_HOME=C:\Program Files\Java\jre8`.
>
>

### Linux

On Linux, you can configure the JRE to be used by adding
`jre=/path/to/jre` to `smartgit.vmoptions`.



#### Example
>
>
>
>To tell SmartGit to use the JRE located in `/opt/jre/jre32/jre1.7.0`,
>add following line to `smartgit.vmoptions`:
>
>`jre=/opt/jre/jre32/jre1.7.0`
>
>

## Memory Limit

The memory limit (also known as maximum heap size) specifies how much
RAM the SmartGit process is allowed to use. The memory limit can be
configured by the VM option `-Xmx`.



#### Example
>
>
>
>To change the maximum memory limit to 1GB, add following line to
>`smartgit.vmoptions`:
>
>`-Xmx1024m`
>
>

If the set value is too low, SmartGit may run out of memory during
memory-intensive operations.


#### Note
>
>
>32-Bit Java VMs only allow to configure a maximum memory limit of
>roughly `1200M`. For almost all setups and repository sizes, this should
>be sufficient. If you nevertheless need to configure a higher limit, you
>will have to use a 64-bit VM and on Windows invoke `smartgit64.exe`.
>
>

## Extended PATH

On Linux and Mac OS X, you can extend the PATH used by SmartGit (and all
processes invoked by SmartGit, especially Git itself) by
adding `path=/additional/path` to `smartgit.vmoptions`. This `path=`
lines can be used multiple times and will be **appended** to the PATH in
the order of occurrence.



#### Example
>
>
>
>To add the directory `/opt/git-lfs` to the PATH, add following line to
>`smartgit.vmoptions`:
>
>`path=/opt/git-lfs`
>
>
