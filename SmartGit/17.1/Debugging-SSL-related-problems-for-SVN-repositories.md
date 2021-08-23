# Debugging SSL-related problems for SVN repositories

When experiencing problems to connect to SVN repositories over the
*https*-protocol, it can be helpful to debug Java's networking layer. To
do that, first add the system property `javax.net.debug=ssl` to the
:EXTREF:smartgit.properties:EXTREF: file. After that, restart SmartGit
from the command line and pipe the output to a file:

-   On Windows: execute `<install-dir>\bin\smartgitc.exe > dump.txt`.
-   On Mac OS: execute
    `<install-dir>/Contents/MacOS/SmartGit > dump.txt`.
-   On Linux: execute `<install-dir>/bin/smartgit.sh > dump.txt`.

Finally, verify that `dump.txt` contains SSL-related output.

*How to send the dump.txt file*: Compress the `dump.txt` file as a *zip*
or *tar/gzip* archive, and also include the file `log.txt` from
:EXTREF:SmartGit's settings directory:EXTREF:. Send this archive, as
well as a short description of how to reproduce the problem, to
<smartgit@syntevo.com>.
