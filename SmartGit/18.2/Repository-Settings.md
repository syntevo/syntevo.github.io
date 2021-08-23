# Repository \| Settings

Use this dialog to configure certain options of your repository or make
these settings globally by selecting the "Remember as default" checkbox.
The effective values are displayed - they can be configured for your
repository (`<repository>/.git/config`) or globally (`~/.gitconfig`).

## Text Encoding

Here you should configure the text encoding SmartGit should assume when
viewing or editing text files, e.g. with the Compare, Index Editor or
Conflict Solver.

UTF-8 with BOM, UTF-16 with BOM are detected automatically. Files with
UTF-8 and without BOM are likely to be automatically detected from the
content.

## User

Configure your name and email address to identify who created the
commits.

## Pull

With these settings you can configure whether to delete obsolete remote
branches or how to handle submodules when pulling.

## Push

Configure what should happen with submodules if you push a submodule
change.

## Signing

Configure the GPG program and your signing key to [Sign Tags and Commits](Sign-Tags-and-Commits.md).



You need to ensure the specified GPG program is configured to use an
agent that can ask you for your key's passphrase using a GUI.

Otherwise you may get a gpg error "cannot open tty \`/dev/tty': Device
not configured".


