# Cherry-Pick

The Cherry-Pick command allows you to 'apply' certain commits from
another branch to the current branch.



``` text
o                        o  C' [> master]
|                        |
o  [> master] A          o  A
|                        |
|   o  [a-branch]        |   o  [a-branch]
|   |                    |   |
o   |  B                 o   |  B
|   |                    |   |
|   o  C (selected)      |   o  C
|   |                    |   |
o   |  D       ===>      o   |  D
|  /        cherry-pick  |  /
| /                      | /
o                        o
```



In SmartGit, there are several places from which you can initiate a
cherry-pick:

-   **Menu and toolbar** On the main window, select
    **Branch\|Cherry-Pick** to open the **Cherry-Pick** dialog, where
    you can select one or more commits to cherry-pick. Depending on your
    toolbar settings, you can also open this dialog via the
    **Cherry-Pick** button on the toolbar.
-   **Log Graph** On the Log graph of the **Log** window, you can
    perform a cherry-pick by right-clicking on one or more commits and
    selecting **Cherry-Pick** from the context-menu.
