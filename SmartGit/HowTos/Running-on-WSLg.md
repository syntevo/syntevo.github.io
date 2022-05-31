# Running on WSLg

This page is dedicated to running SmartGit on Windows Subsystem for Linux with GUI (WSLg).
WSLg allows running GUI based Linux applications, such as SmartGit, in emulated Linux environment on Windows.
This is convenient if you need to mix Windows and Linux development and prefer Windows as main OS.

Note that you need **Win11 or higher**, because WSLg is not supported on Win10 (it only has plain WSL).

# WSLg installation

Run this command in administrator commandline:
```
wsl --install -d Ubuntu
```

and reboot when suggested. After the reboot, find new `Ubuntu on Windows` item in Start menu and launch it.

Run these commands in WSL terminal to make sure that WSLg works as intended:
```
sudo apt update
sudo apt install gedit
gedit
```

You should see `gedit` window open in your Windows. If this doesn't happen, then either you don't have WSLg or it's broken in some way.

# SmartGit installation

1. Download SmartGit to WSLg
   * On Windows, navigate to [https://www.syntevo.com/smartgit/download/](https://www.syntevo.com/smartgit/download/)
   * Click `Download for Linux`
   * Start `Ubuntu on Windows` from Windows Start menu. This will open a console, you'll use it later.
   * In your Windows Explorer, notice `Linux` item on side panel.
   * Navigate to location where you want to install SmartGit on Linux, such as<br>
      `Ubuntu\home\user`<br>
      (replace `user` with your username)
   * Copy the `.tar.gz` file you downloaded to this folder in Windows Explorer
2. In `Ubuntu on Windows`, run these commands:<br>
   * `cd ~`<br>
     If you downloaded SmartGit to a different folder, adjust this step.
   * `tar xvzf smartgit-linux-21_2_2.tar.gz`<br>
     Replace filename with the one you downloaded.<br>
     This will extract `smartgit` folder from the archive.
   * `sudo apt update`<br>
     A preparation for `sudo apt install` steps.
   * `sudo apt install libgtk-3-0`<br>
     SmartGit is a GTK based program. GTK is installed in most GUI based Linux, but not on WSL. Without GTK installed, SmartGit will fail to start with error like
	 ```
	 java.lang.reflect.InvocationTargetException
	     at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	     at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	     at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	     at java.base/java.lang.reflect.Method.invoke(Method.java:566)
	     at com.syntevo.QBootLoader.main(SourceFile:115)
	 Caused by: java.lang.UnsatisfiedLinkError: Could not load SWT library. Reasons:
	     Can't load library: /home/user/.smartgit/21.2/swt.tmp/libswt-pi4-gtk-4946r10.so
	     Can't load library: /home/user/.smartgit/21.2/swt.tmp/libswt-pi4-gtk.so
	     Can't load library: /home/user/.smartgit/21.2/swt.tmp/libswt-pi4.so
	     no swt-pi4-gtk-4946r10 in java.library.path: [/usr/java/packages/lib, /usr/lib64, /lib64, /lib, /usr/lib]
	     no swt-pi4-gtk in java.library.path: [/usr/java/packages/lib, /usr/lib64, /lib64, /lib, /usr/lib]
	     no swt-pi4 in java.library.path: [/usr/java/packages/lib, /usr/lib64, /lib64, /lib, /usr/lib]

	     at org.eclipse.swt.internal.Library.loadLibrary(Library.java:348)
	     at org.eclipse.swt.internal.Library.loadLibrary(Library.java:257)
	     at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:96)
	     at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:209)
	     at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:155)
	     at org.eclipse.swt.widgets.Display.<clinit>(Display.java:165)
	     at smartgit.IV.a(SourceFile:63)
	     at smartgit.abZ.a(SourceFile:161)
	     at com.syntevo.smartgit.p.a(SourceFile:384)
	     at com.syntevo.smartgit.p.a(SourceFile:283)
	     at smartgit.acE.b(SourceFile:68)
	     at com.syntevo.smartgit.SmartGit.main(SourceFile:11)
	     ... 5 more
	 ```
   * `sudo apt install xdg-utils`<br>
     A package necessary for next step. Installed by default on most Linux distros. For some reason, not present by default on WSL.
   * `sudo mkdir /usr/share/desktop-directories`<br>
     A workaround for Linux bug, see [https://askubuntu.com/questions/405800](https://askubuntu.com/questions/405800).
	 Without it, you might have error `No writable system menu directory found` in next step.
   * `sudo ./smartgit/bin/add-menuitem.sh`<br>
     This will let Windows know about SmartGit. Right after running this command, your Windows Start menu will get new entry `SmartGit (Ubuntu)`.
     Note that you need to run it with `sudo`, because Windows only picks up info from system `/usr/share/applications` and ignores user `~/.local/share/applications`.
3. Run and set up SmartGit
   * Find `SmartGit (Ubuntu)` in Windows Start menu and run it.
   * When asked for license, know that you can pick your Windows license from inside WSLg. To do that, navigate to
     `/mnt/c/Users/win-user/AppData/Roaming/syntevo/SmartGit/22.1/license`<br>
     (here, `win-user` is your Windows username, and `22.1` with your SmartGit version. Just use directory browser button)
   * From this point, you can use SmartGit as usual.

# Current WSLg issues in SmartGit

We plan to investigate and fix what we can.

1. SmartGit fails to check for updates<br>
   Disabling Windows Firewall seems to help. But see next problem.
2. SmartGit fails to install updates<br>
   Current workaround is to re-install new version manually (see `SmartGit installation` chapter above).
3. SmartGit windows do not have minimize/maximize buttons<br>
   This is due to how WSLg is configured by default. You can change that:
   * In WSL commandline, run commands:
     ```
     sudo apt install gnome-tweaks
     gnome-tweaks
     ```
   In `gnome-tweaks` that opened, navigate to `Window Titlebars` and enable minimize and maximize buttons there.
4. If you noticed anything else, please send us a mail to `smartgit@syntevo.com`.

# Other WSLg issues

## VirtualBox has a lot of bugs when WSL is installed

Installing WSLg also installs `Windows Hyper-V`, which is required for `WSLg`
to run. Unfortunately, having `Hyper-V` installed causes `VirtualBox` VMs to
fail in various ways: they will crash, hang, etc.

The workaround is to create an additional Windows boot configuration. This way,
you can select either `Hyper-V` or no `Hyper-V` on every boot.
Run these commands on Windows administrator commandline:
```
bcdedit /copy {current} /d "Win11 + Hyper-V"
bcdedit /set {current} hypervisorlaunchtype off
```

See also: [https://forums.virtualbox.org/viewtopic.php?t=90853](https://forums.virtualbox.org/viewtopic.php?t=90853)

## No internet / network after installing WSL

This seems to be happening on some machines, but not the others. For me, the following fixed the problem:

1. Press Win+R and run `ncpa.cpl`. This will show your network adapters.
2. Right-click adapter you're using for internet and select `Diagnose`.
3. Agree to reset adapter and reboot when suggested.
