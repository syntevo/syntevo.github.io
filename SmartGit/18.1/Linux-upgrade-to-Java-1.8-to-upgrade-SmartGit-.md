# Linux: upgrade to Java 1.8 (to upgrade SmartGit)

1.  Download the appropriate `.tar.gz` bundle for your platform of
    the Java 8 Runtime Environment from:
    \<<http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html>\>  
      
    For example:` jre-8u121-linux-x64.tar.gz`  
      
2.  Unpack the bundle to a directory of your choice, for example to
    `/optsudo tar -xzf jre-8u121-linux-x64.tar.gz -C /opt`
3.  Tell SmartGit to use this JRE by adding following line to
    `~/.smartgit/smartgit.vmoptions`:  
      
    `jre=/path/to/your/jre`  
      
    For example:  
      
    `jre=``/opt/jre1.8.0_121`
4.  Restart SmartGit
5.  Invoke `Help|About` and make sure your JRE 1.8 is displayed there.  
      
    For example:  
      
    ![](attachments/16548037/16548038.png)  
      

Invoke `Help|Check for New Version` to upgrade to the latest SmartGit
version.  
  


