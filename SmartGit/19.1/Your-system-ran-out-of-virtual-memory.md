# Your system ran out of virtual memory

# Introduction

When SmartGit crashed, your computer was low on virtual memory.

This usually happens due to two reasons:

1.  One of the programs on your computer is bugged, gradually eating all
    available memory.
2.  You don't have enough RAM installed and run too many programs. This
    shouldn't be the case if you have at least 16GB RAM.

# Windows: Diagnosing with Event Log

This is the best and easiest way to diagnose.

1.  Start Windows `Event Viewer` application
    1.  Go to
        `Control Panel → System and Security → Administrative Tools`
    2.  Start `Event Viewer` from there.
2.  Expand `Windows Logs → System` on the left.``
3.  Search for `Resource-Exhaustion-Detector` events  
    1.  Press Ctrl+F to open search box.
    2.  Enter `Resource-Exhaustion-Detector`
    3.  Search
4.  Investigate
    1.  Double-click found event to view details for it.

    2.  It will say something like this:



            Windows successfully diagnosed a low virtual memory condition.
            The following programs consumed the most virtual memory:
            BuggedProgram.exe (11584) consumed 55.660.101.632 bytes
            firefox.exe (5304) consumed 1.009.725.440 bytes.



    3.  Look for anything suspicious  
        Values above 4.000.000.000 bytes are already suspicious.  
        Values above 16.000.000.000 bytes most likely mean that this
        program causes problems for you.
5.  If these steps didn't help you, please send us a mail!



If you found the program, please let us know! This lets us help other
users better.



# Windows: Diagnosing with our script

To try to diagnose the problem, please download, extract and run this
script:  
<https://www.syntevo.com/downloads/misc/AnalyseMemoryUsage.cmd.zip>  
  
These are reasonable values for typical workflows:

1.  "Virtual Memory - Programs total" should be below 6GB.
2.  "Virtual Memory - Used" should be below 10GB. Value over 30GB is a
    strong indication of memory leaks.
3.  "Virtual Memory - Used" should be roughly a sum of "Virtual Memory -
    Programs total" and "Kernel - Cache", plus any memory you allocated
    to virtual machines, if you have them. If the value is higher, then
    it's likely that one of your kernel drivers has a memory leak.
4.  "Kernel - Pool" both values should be below 300MB.

Script will also provide a list of individual programs with their memory
usage. Hopefully, one of the programs will have an obviously high memory
consumption. Otherwise, the memory leak probably happens in kernel
driver, which is harder to diagnose.



If you found the program, please let us know! This lets us help other
users better.



# Windows: Diagnosing with RAMMap

[SysInternals RAMMap](https://docs.microsoft.com/en-us/sysinternals/downloads/rammap)
is an utility that shows some additional kernel memory stats.

In typical workflows, each of these values should be below 1GB:

1.  Page Table
2.  Paged Pool
3.  Nonpaged pool
4.  System PTE (except when you run virtual machines)
5.  Session private
6.  Driver Locked
7.  Kernel Stack

If any of these counters is significantly higher then 1GB, this likely
points to a problem. Diagnosing it further is different for every case.

# Didn't find the program to be blamed?

Please contact support, attaching outputs from AnalyseMemoryUsage.cmd
and RAMMap and we will try to help.
