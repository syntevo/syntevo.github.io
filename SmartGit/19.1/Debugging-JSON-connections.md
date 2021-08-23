# Debugging JSON connections

For the majority of its integrations (JIRA, GitHub, Bitbucket, GitLab,
...), the corresponding platform will be accessed over a REST API which
is based on JSON. In case of parsing problems, it may be helpful to
debug log sent and received JSON objects. To do so:

1.  create a temporary debug output directory on your hard disk, which
    is writable for SmartGit (e.g. `c:/temp/json`)

2.  add following line to [smartgit.properties](System-Properties.md) for
    which you will replace `<absolute-path-to-debug-directory>` by your
    directory's path (on Windows, be sure to use forward-slashes instead
    of back-slashes)



    ``` java
    smartgit.json.debugDir=<absolute-path-to-debug-directory>
    ```



    Example:



    ``` java
    smartgit.json.debugDir=c:/temp/json
    ```



3.  restart SmartGit to have the changes take effect

4.  invoke the problematic operation:
    -   in case of parsing problems, SmartGit will report the debug
        output file for the failed operation in the error message

5.  check the debug output directory for sent and received JSON objects:
    -   there will be one `in` file containing the received content, an
        optional `out` file containing the sent content and an
        optional `err` file containing the received error
    -   all files belonging to the same request will be labeled by a
        unique timestamp  
          

  
