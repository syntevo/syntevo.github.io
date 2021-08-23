# Inspecting SmartGit's process using JVisualVM

*JVisualVM* is a Java Profiler which is part of the JDK and can be
helpful to diagnose various problems.

-   Install the latest *JDK* from
    [http://www.oracle.com/technetwork/java/javase/downloads/index.html](index.md)
    (unless you already have a JDK installed).
-   Run JVisualVM by invoking `bin/jvisualvm.exe` (on Windows). On Linux
    and Mac, locate `jvisualvm` which should be in the same directory as
    `javac`.
-   Once JVisualVM has started up, locate the *SmartGit*-related VMs:
    there will be one *main* VM, if SmartGit is running (on Windows
    showing up as `SmartGit`, on Mac/Linux showing up as `QBootLoader`).
    If a SmartGit upgrade is in progress, there will be an additional VM
    (on Windows showing up as `SmartGitUpdater`). If SSH connections are
    currently in progress, there may be more VMs.


#### Note
>
>
>If you can't connect to *SmartGitUpdater* VM, try again running
>JVisualVM as administrator, because SmartGitUpdater is usually invoked
>with administrative privileges, too.
>
>

#### Taking thread dumps

Thread dumps are useful to investigate hangs or slow performance.

-   Select the VM you want to inspect.
-   Select tab **Threads** and invoke **Thread Dump**.
-   When investigating a problem, it's usually a good idea to create a
    couple of thread dumps.

#### Taking a heap dump

Heap dumps are useful to investigate memory-related problems.

-   Select the VM you want to inspect.
-   Select tab **Monitor** and invoke **Heap Dump**.
-   To investigate the current state yourself, the **Classes** section
    will give you a good overview of the memory usage: sorting by
    **Instances** and **Size** can be helpful to detect (unusually)
    large occurrences of specific classes. By double-clicking a certain
    class, you will switch to the **Instances** view which gives you
    detailed information for every object of this class.
-   To take a full heap dump for debug purposes, select the **Monitor**
    section and hit the **Heap Dump** button there.


#### Note
>
>
>For heap dumps, it's expected to see a lot of `char[]`, `byte[]` and
>`String` objects, as version control is more or less all about bytes and
>texts (paths, file contents, commit messages).
>
>

Heap dumps are usually huge, so first thing to do is to store them
locally using **Save As** from the context menu in the **Applications**
view. This way they can be accessed later on and if necessary can be
transferred to us.
