# GPG-PGP

Create a public and private key (and keyring + trustdb if not already present) in the current directory under .gnupg folder

```
gpg --gen-key --homedir .gnupg
```

output and add your name :
```
gpg (GnuPG) 2.2.27; Copyright (C) 2021 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Note: Use "gpg --full-generate-key" for a full featured key generation dialog.

GnuPG needs to construct a user ID to identify your key.

Real name: jon snow
Email address: jon.snow@stark.com
You selected this USER-ID:
    "jon snow <jon.snow@stark.com>"
...
```

content of .gnupg folder
```
drwx------     - rfabas 18 avril 11:26 openpgp-revocs.d
drwx------     - rfabas 18 avril 11:26 private-keys-v1.d
.rw-rw-r--  1,7k rfabas 18 avril 11:33 public_key_ring.gpg
.rw-rw-r--  2,0k rfabas 18 avril 11:26 pubring.kbx
.rw-------    32 rfabas 18 avril 11:26 pubring.kbx~
.rw-rw-r--  3,8k rfabas 18 avril 11:32 secret_keys_ring.gpg
.rw-------  1,3k rfabas 18 avril 11:26 trustdb.gpg

```

Export private key ring
```
gpg --no-default-keyring --homedir ./.gnupg/ --export-secret-keys > ./.gnupg/secret_keys_ring.gpg
```

Export public key ring
```
gpg --no-default-keyring --homedir ./.gnupg/ --export > ./.gnupg/public_key_ring.gpg
```

list secret-keys id in keyring
```
gpg --no-default-keyring --homedir ./.gnupg/ --list-secret-keys --keyid-format LONG
```

output
```
/home/rfabas/go/src/github.com/remifabas/pgp-test/./.gnupg/pubring.kbx
----------------------------------------------------------------------
sec   rsa3072/840F06145BCC384E 2023-04-18 [SC] [expires: 2025-04-17]
      45E3IDIDIDIDC5D22144DF06145BCC384E.....
uid                 [ultimate] jonsnow <jonsnow@stark.com>
ssb   rsa3072/0A5EC7E2D68FF709 2023-04-18 [E] [expires: 2025-04-17]
```

Export as armored a specific secret key
```
gpg --no-default-keyring --homedir ./.gnupg/ --armor --export-secret-keys 45E3IDIDIDIDC5D22144DF06145BCC384E...
```

Export as armored a specific public key
```
gpg --no-default-keyring --homedir ./.gnupg/ --armor --export 45E3IDIDIDIDC5D22144DF06145BCC384E...
```
