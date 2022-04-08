# Running on WSLg

This page is dedicated to running SmartGit on Windows Subsystem for Linux with GUI (WSLg).
WSLg allows running GUI based Linux applications, such as SmartGit, in emulated Linux environment on Windows.
This is convenient if you need to mix Windows and Linux development and prefer Windows as main OS.

# WSLg installation 

If you're running Windows 11 21H2 or higher, then run this command in administrator commandline:
```
wsl --install -d Ubuntu
```

and reboot when suggested. After the reboot, find new `Ubuntu on Windows` item in Start menu and launch it.

# SmartGit installation

1. Download SmartGit to WSLg
   * On Windows, navigate to [https://www.syntevo.com/smartgit/download/](https://www.syntevo.com/smartgit/download/)
   * Click `Download for Linux`
   * Start `Ubuntu on Windows` from Windows Start menu. This will open a console, you'll use it later.
   * In your Windows Explorer, notice `Linux` item on side panel.
   * Navigate to location where you want to install SmartGit on Linux, such as    
      `Ubuntu\home\user`  
      (replace `user` with your username)
   * Copy the `.tar.gz` file you downloaded to this folder in Windows Explorer
2. In `Ubuntu on Windows`, run these commands:    
   * `cd ~`  
     If you downloaded SmartGit to a different folder, adjust this step.
   * `tar xvzf smartgit-linux-21_2_2.tar.gz`  
     Replace filename with the one you downloaded.  
     This will extract `smartgit` folder from the archive.
   * `sudo apt install xdg-utils`  
     A package necessary for next step. Installed by default on most Linux distros, but on WSL.
   * `sudo ./smartgit/bin/add-menuitem.sh`  
     This will let Windows know about SmartGit. Right after running this command, your Windows Start menu will get new entry `SmartGit (Ubuntu)`.
     Note that you need to run it with `sudo`, because Windows only picks up info from system `/usr/share/applications` and ignores user `~/.local/share/applications`.
3. Run and set up SmartGit     
   * Find `SmartGit (Ubuntu)` in Windows Start menu and run it.
   * When asked for license, know that you can pick your Windows license from inside WSLg. To do that, navigate to
     `/mnt/c/Users/win-user/AppData/Roaming/syntevo/SmartGit/22.1/license`  
     (here, `win-user` is your Windows username, and `22.1` with your SmartGit version. Just use directory browser button)
   * From this point, you can use SmartGit as usual.
 
# Current WSLg issues in SmartGit

We plan to investigate and fix what we can, hopefully soon(tm).

1. SmartGit fails to check for updates  
   Disabling Windows Firewall seems to help. But see next problem.
2. SmartGit fails to install updates  
   Current workaround is to re-install new version manually (see `SmartGit installation` chapter above). 
3. SmartGit windows do not have minimize/maximize buttons  
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

## No internet / network after installing WSL

This seems to be happening on some machines, but not the others. For me, the following fixed the problem:

1. Press Win+R and run `ncpa.cpl`. This will show your network adapters.
2. Right-click adapter you're using for internet and select `Diagnose`.
3. Agree to reset adapter and reboot when suggested.
