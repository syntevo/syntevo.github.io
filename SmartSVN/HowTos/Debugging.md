# Debugging

# General advices/preparations

Always try to investigate problems with a fresh SmartSVN setup:

-   on Windows, use the *Portable* bundle:
    <https://www.smartsvn.com/download/>
-   on macOS and Linux, temporary use a new
    [smartsvn.settings](System-Properties.md) directory


Why?


SmartSVN has plenty of **Preferences** options and even more **Low-Level
Properties** which may sometimes affect the behavior of operations in
non-obvious ways. This is especially true if the behavior you are
experiencing is unexpected and/or looks like a bug.



Also, before investigating a problem, restart SmartSVN with clean logs:

-   locate the [Installation and Files](Installation-and-Files.md) in the
    **Help\|About** dialog
-   from sub-directory `logs/` remove all `log.txt*` files

When sending logs to us, make sure they are **compressed** either with
*ZIP* or *7z*. This prevents the logs from becoming inlined into the
email.

# Enabling debug logging for certain keys

To enable debug logging for a certain key `foo.bar`, first decide the
log-level – whether it should be fine (`DEBUG`) or as fine as
possible `TRACE`. Usually SmartSVN support will tell you. After that add
the corresponding line to `smartsvn.properties` (in the Settings
directory, see [Installation and Files](Installation-and-Files.md)).
Depending on the log-level this will be either:


style="border-bottom-width: 1px;">

**DEBUG logging**



``` java
log4j.foo.bar=DEBUG
```



Or:


style="border-bottom-width: 1px;">

**TRACE logging**



``` java
log4j.foo.bar=TRACE
```



After that, restart SmartSVN and repeat the operation for which debug
logging should be collected and shutdown SmartSVN again.

Now `logs/log.txt.0` should contain `DEBUG` lines for the specified key.



If asked by support to enable debug logging for key `foo.bar`, always be
sure to use `log4j` prefix, i.e. `log4j.foo.bar`.



  

  

  
  
  
