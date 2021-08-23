# Revert

The Revert command allows you to 'undo' certain commits (from whatever
branch) in the current branch.



``` text
o                        o  reversed-C  [> master]
|                        |
o  [> master] A          o  A
|                        |
|   o  [a-branch]        |   o  [a-branch]
|   |                    |   |
o   |  B                 o   |  B
|   |                    |   |
|   o  C (selected)      |   o  C
|   |                    |   |
o   |  D         ===>    o   |  D
|  /            revert   |  /
| /                      | /
o                        o
```



In SmartGit, there are several places from which you can initiate a
Revert:

-   **Menu and toolbar** On the main window, select **Branch\|Revert**
    to open the **Revert** dialog, where you can select one or more
    commits to revert. Depending on your toolbar settings, you can also
    open this dialog via the **Revert** button on the toolbar.
-   **Log Graph** On the Log graph of the **Log** window, you can
    perform a revert by right-clicking on one or more commits and
    selecting **Revert** from the context-menu.
