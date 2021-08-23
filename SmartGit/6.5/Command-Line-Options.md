# Command-Line Options

This section gives an overview of the various options SmartGit can be
started with. These options should be given as parameters to the
SmartGit launcher. The launcher to be used depends on your platform:

-   **Windows** `bin\smartgit.exe` or `bin\smartgitc.exe`. The first one
    is meant for regular usage, while the second one will print
    additional information on the console while the program runs.
-   **Mac OS X** `SmartGit <version-number>.app/Contents/MacOS/SmartGit`
-   **Linux** `bin/smartgit.sh`

In the following, we'll use `smartgitc.exe` as an example to explain the
available options. Substitute it with the respective launcher for your
platform if you're not using Windows.

There may be additional options available that mainly serve debugging
purposes and are therefore not documented here.

## Options "-?" and "--help"

With either of the two following commands you can print all command-line
options on the console that are specifically supported by the version of
SmartGit you're using:



#### Example
>
>
>
>`smartgitc.exe -?`
>
>`smartgitc.exe --help`
>
>


#### Note
>
>
>On Windows, make sure to call `smartgitc.exe` (with 'c' on the end),
>otherwise when calling `smartgit.exe` this parameter has no effect,
>since the SmartGit process won't be attached to any console to print the
>help output to.
>
>

## Option "--cwd"

This option sets the current working directory, which affects the path
given in the `open`, `log` and `blame` option (see below) as follows:

-   If the `open`, `log` or `blame` options are specified without their
    own path arguments, the path given with the `cwd` option will be
    used as argument for `open` or `log`.
-   If the `open`, `log` or `blame` options are specified with relative
    paths, these relative paths will be resolved against the path given
    with the `cwd` option.
-   If the `open`, `log` or `blame` options are specified with absolute
    paths, the path given with the `cwd` option is ignored.

The path given with the `cwd` option must be an absolute path. If the
path is relative, it will be ignored.

## Option "--open"

This option launches SmartGit and opens the repository in the specified
location.



#### Example
>
>
>
>`smartgitc.exe --open C:\path\to\repository`
>
>



#### Example
>
>
>
>`smartgitc.exe --cwd C:\path --open to\repository`
>
>

## Option "--log"

This option opens SmartGit's Log window for the repository or file in
the specified location. The project window is not opened.



#### Example
>
>
>
>`smartgitc.exe --log C:\path\to\repository\path\to\file`
>
>



#### Example
>
>
>
>`smartgitc.exe --cwd C:\path --log to\repository`
>
>

## Option "--blame"

This option opens SmartGit's Blame window for the specified file.



#### Example
>
>
>
>`smartgitc.exe --blame C:\path\to\repository\path\to\file`
>
>
