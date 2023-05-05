# Debugging SSL-related problems

Various built-in SmartGit functionality will connect to *https* URLs, for example:

- **Check for New Version**
- various integrations, like Hosting Providers

When experiencing problems here, it can be helpful to debug Java's networking layer.
To do that, add the following system property to the [smartgit.properties](../Latest/System-Properties.md) file:

```
javax.net.debug=ssl:handshake
```
After that, restart SmartGit from the command line and pipe the output to a file:

- On Windows: execute `<install-dir>\bin\smartgitc.exe > dump.txt` 2>&1
- On MacOS: execute `<install-dir>/Contents/MacOS/SmartGit > dump.txt` 2>&1
- On Linux: execute `<install-dir>/bin/smartgit.sh > dump.txt` 2>&1

Finally, verify that `dump.txt` contains SSL-related output.

*How to send the dump.txt file*:
Compress the `dump.txt` file as a *zip* or *tar/gzip* archive, and also include the zipped `log` directory from SmartGit's settings directory.
Send this archive, as well as a short description of how to reproduce the problem, to <smartgit@syntevo.com>.
