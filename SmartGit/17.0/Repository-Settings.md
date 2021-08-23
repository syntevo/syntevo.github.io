# Repository \| Settings

Use this dialog to configure certain options of your repository or make
these settings globally by selecting the "Remember as default" checkbox.

## Pull

With these settings you can configure whether to delete obsolete remote
branches or how to handle submodules when pulling.

## Commit

With these settings you can configure what name and email address should
be used when committing, as well as whether to sign all commits (see
also [Sign Tags and Commits](Sign-Tags-and-Commits.md)).



You need to ensure the specified GPG program is configured to use an
agent that can ask you for your key's passphrase using a GUI.

Otherwise you may get a gpg error "cannot open tty \`/dev/tty': Device
not configured".



## Text Encoding

Here you should configure the text encoding SmartGit should assume when
viewing or editing text files, e.g. with the Compare, Index Editor or
Conflict Solver.

UTF-8 with BOM, UTF-16 with BOM are detected automatically. Files with
UTF-8 and without BOM should be able to be automatically detected from
the content.
