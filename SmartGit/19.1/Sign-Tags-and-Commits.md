# Sign Tags and Commits

-   if you are using Windows, please install GPG4Win (the light version
    should be sufficient)
    -   run `gpa.exe` and create a key securing it with a passphrase
-   in SmartGit [Repository \| Settings](https://www.syntevo.com/doc/display/SG170/Repository+%7C+Settings),
    tab "Commit" configure the full path to the `gpg2.exe` and enter the
    ID of your created key
    -   if necessary, select "Sign all commits"
-   when committing a file or tagging, a popup of GPG will occur and ask
    you for the key's passphrase
