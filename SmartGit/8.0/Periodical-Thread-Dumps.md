# Periodical Thread Dumps

Logging periodical thread dumps is a built in feature of SmartGit to
track *well reproducible*, *pervasive* performance problems. To
investigate a problem using periodical thread dumps, do the following:

-   While SmartGit is running, locate the settings directory: invoke
    **Help\|About SmartGit** and check the **Information** page for the
    settings directory (**Settings Path**).
-   Shutdown SmartGit (use **Repository\|Exit** and afterwards make sure
    that no more SmartGit process is running).
-   In the settings directory, open `smartgit.properties` (create this
    file if necessary) and add following line to enable the **Debug**
    menu:



``` java
smartgit.debug=true
```



-   Remove all `log.txt*` files from the settings directory.
-   Startup SmartGit.
-   Trigger the slow operation.
-   Invoke **Debug\|Create Periodical Thread Dumps.**
-   After the offending operation has finished, shutdown SmartGit again.
-   Compress all `log.txt.*` files from the settings directory as a
    *zip* or *tar/gzip* archive and send this archive, as well as a
    short description of how to reproduce the problem, to
    [smartgit@syntevo.com](mailto:support@smartsvn.com.md).
