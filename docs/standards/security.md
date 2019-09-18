# Security

This page covers all standards related to security subjects.

## Sensitive Data Management

As the 12th rule from 12 Factors states: "One-off administration processes should be run against specific releases and shipped with the main process code.".

It's a good practice to keep sensitive data related to configuration and parametrization in the same VCS repository of the application. But we need a way to keep identities from contributors linked with authorization/authentication security features without requiring any external service, just tooling and a minimal process.

First, you need to know a little about [GPG](https://gnupg.org/) and you can read more about on [Wikipedia](https://pt.wikipedia.org/wiki/GNU_Privacy_Guard) too.

### GPG Keys management

**Generating a key pair**

Run the command: `gpg --gen-key`

Type your full name and your work email, you should use a strong password, this will protect your secret key.

**View current keys**

To view your trusted public keys: `gpg --list-keys`

To view your imported private keys: `gpg --list-secret-keys`

**Export your keys**

To export your public key: `gpg --export -a -o mypublickey.gpg my@email.com`

You can send this files to people who need to trust you as recipient of sensitive data. We recommend to keep commit this file into git under a common folder dedicated to known and trusted GPG keys.

To export your private key: `gpg --export-secret-key -a -o myprivatekey.gpg my@email.com`

This file is the most critical file of your keys and you should never leak this content to insecure locations. However, it's important to backup this file to a secure offline storage (like an USB stick driver).

### Keeping data secure

Well, now that you have your GPG keys, you can use [git-secret](https://git-secret.io).

### Keeping your identity public

Any identity/security subject will be placed on: https://github.com/gamaops/cookbook

To make your identity and authority known by other people, put your **public key** on `/trusted` folder and name your file with your work email, example: `/trusted/someone@gamaops.com`. **Don't put your private key here.**

**What do I need to do when an identity is not trusted anymore?**

**Examples:** someone does not work anymore on company, you loose your private key.

1. Contact any SRE of Engineering Team
2. That SRE will remove your public key from `/trusted` folder and move to `/revoked/your-email/revocation-date`
   1. The SRE will open a PR and you'll be the approver
3. You need to make an annoucement on Slack's **general** channel telling people to not trust that key anymore
4. Any **git-secret** encrypted files with the public key from that private key must be regenerated without that private key anymore

### Best practices

1. Keep all sensitive data in git using a dedicated folder named: **vault**
2. Make an offline backup of your GPG private key