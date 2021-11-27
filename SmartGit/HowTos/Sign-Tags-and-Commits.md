# Sign Tags and Commits

-   if you are using Windows, please install Gpg4win (verified with Gpg4win 3.1.16)
-   run `gpa.exe` (usually found in `C:\Program Files (x86)\Gpg4win\bin` and create a key pair securing it with a passphrase
-   in SmartGit [Repository \| Settings](../Latest/Repository-Settings.md),
    tab "Signing" configure the full path to the `gpg.exe` (usually found in `C:\Program Files (x86)\GnuPG\bin`) and enter the
    *Key ID* of your created key pair
-   if necessary, select "Sign all commits"
-   when committing a file or tagging, a popup of GPG will occur and ask you for the key's passphrase
