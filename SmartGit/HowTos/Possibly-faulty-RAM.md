# Possibly faulty RAM

# Introduction

Quite often, the presence of random unexplained problems is caused by
faulty RAM. This is easy to test and is a good first step to diagnose.

# Windows - Quick test

1.  If you have a few spare hours when you don't need your computer,
    please run [Extended test](#windows---extended-test)
    instead.

2.  The test will take around half an hour. You won't be able to use
    your computer while the test runs. It could be convenient to run it
    during the lunch break.

3.  Run from Win+R or from command line:



    ``` java
    MdSched.exe
    ```



4.  Choose whether to restart now or postpone it until next restart.

5.  Once your computer is restarted, the test will run automatically.

6.  If you need your computer before the test completes, you can
    interrupt it with Esc and run again later.

7.  Once the test is finished, the computer will automatically boot back
    into Windows.

8.  You can find test results in Windows Event Log :  
    a. Go to
    `Control Panel > System and Security > Administrative Tools > Event Viewer > Windows Logs > System`

    b\. Find event with `Source` equal to `MemoryDiagnostics-Results`

9.  If the test detected any errors, read [this chapter](#test-detected-errors).

10. Sometimes, a quick test does not detect errors. Please also run
    [Extended test](#windows---extended-test).

# Windows - Extended test

1.  The test will take a few hours. You won't be able to use your
    computer while the test runs. It could be convenient to run during
    the night.

2.  Run from Win+R or from command line:



    ``` java
    MdSched.exe
    ```



3.  Choose whether to restart now or postpone it until next restart.

4.  Once your computer is restarted, the test will run automatically.

5.  Press F1 and select `Extended` test mix. Press F10 to apply.

6.  If you need your computer before the test completes, you can
    interrupt it with Esc and run again later.

7.  Once the test is finished, the computer will automatically boot back
    into Windows.

8.  You can find test results in Windows Event Log :  
    a. Go to
    `Control Panel > System and Security > Administrative Tools > Event Viewer > Windows Logs > System`

    b\. Find event with `Source` equal to `MemoryDiagnostics-Results`

9.  If the test detected any errors, read [this chapter](#test-detected-errors).

# Test detected errors?

1.  Even if just a single error was detected, your RAM is faulty and
    it's best to replace it.
2.  Having a test error means that a specific location in memory changes
    its values unpredictably. The more locations are faulty, the higher
    the probability of unexpected errors.
3.  Depending on which program gets this memory you can observe crashes,
    blue screens, all other forms of unexpected behavior. Or it can work
    "fine", if non-important data was corrupted this time, such as a
    single pixel in some image on screen.
4.  On every computer restart, the error will likely corrupt something
    new, so random programs will crash.
5.  If you have multiple RAM chips, you can find the faulty one by
    removing them one by one and running the test again.
