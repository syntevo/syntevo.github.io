# SSH

## Create private key

To create a private/public key pair, execute following command in a
Terminal:

`$ ssh-keygen -t rsa -b 4096 -m PEM`

The parameters `-m PEM` are necessary, because some newer SSH
implementations, e.g. on macOS 10.14+, use a different format of the
private key file that is not (yet) supported by the SSH library SmartGit
is using.

### Converting an existing private key to PEM-format

If you have a private key file which is not supported, please try this
command in a Terminal:

`$ ssh-keygen -f <private_key_file> -p -m PEM`

It will prompt for the old passphrase once (if any) and for the new
passphrase twice.

## Windows: Configure PuTTY and Pageant

### Create your public/private key pair

Use **PuTTY Key Generator** (`puttygen.exe`) to create a new
public/private key pair and save to a location of your choice. Usually
the private key file ends with `.ppk`. It is recommended to use strong
passphrase.

### Tell you SSH server your public key

Copy/paste the long text (actually a long single line) from the large
"Public key" input field in PuTTY Key Generator to the
`~/.ssh/authorized_keys` file of your SSH server or paste to the
appropriate input field of your Git/SSH hosting provider.

### Tell Git to use Plink

Set the environment variable `GIT_SSH` to point to `plink.exe`.

### Start Pageant

Start **Pageant** (`pageant.exe`) which only will show a small icon in
the system tray. Double click that and add your private key file(s) -
those created in the previous step with the PuTTY Key Generator and the
`.ppk` extension - by providing their locations and passphrases.

It looks like Pageant does not remember your private keys and
passphrases, so you have to re-add them again after each start of
Pageant.
