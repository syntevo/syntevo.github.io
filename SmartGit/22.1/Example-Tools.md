# Example Tools

## Format Patch

Save this content to a file `format-patch.yml` and use the *Import* button on the Tools page of the preferences to restore the *Format Patch* feature from SmartGit versions < 22.1.
``` yml
tools:
- name: Format Patch
  fileStarter: {command: '${git}', parameters: 'format-patch -o "${dirSelect}" -1 ${commit}'}
  useForOpen: false
  waitUntilFinished: true
  filePattern: '*'
- name: Format Patch
  fileStarter: {command: '${git}', parameters: 'format-patch -o "${dirSelect}" ${commit}..${commit2}'}
  useForOpen: false
  waitUntilFinished: true
  filePattern: '*'
```

## Open top-most Visual Studio solution from current repository

This powershell script can be used to open a solution file .sln inside a
repository, in Visual Studio. The script iterates through the repository
folders and looks for a .sln file. It stops at the first match and then
launches Visual Studio.

![](attachments/53215435/53215436.png)


**Powershell script C:\\SmartGit-Scripts\\openVS.ps1**



``` java
Install-Module VSSetup -Scope CurrentUser
$slnname = Get-ChildItem -Path $args[0] -Filter *.sln -Recurse -ErrorAction SilentlyContinue -Force | Select-Object -First 1 | Select-Object -ExpandProperty FullName

switch ( $args[1] )
{
    2017
    {
        $ver = '[15.0,16.0)'
    }

    2019
    {
        $ver = '[16.0,17.0)'
    }

    default
    {
        $ver = '[1.0,1000.0)'
    }
}

$devenv = Get-VSSetupInstance | Select-VSSetupInstance -Version $ver -Latest | Select-Object -ExpandProperty InstallationPath
$devenv = $devenv + "\Common7\IDE\devenv.exe"
Start-Process -FilePath $devenv -ArgumentList $slnname
```
