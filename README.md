### In development
We use [git-secret](https://git-secret.io/) to encrypt a `.secrets` file that's then checked into source control. This file contains all local secrets needed for development, and is loaded as environment variables into our app.

#### Set up a GPG key

To set up secret handling you'll need to create a `gpg` RSA key-pair: public and secret key identified by your email address.

* [Follow these instructions to generate GPG key-pair](https://help.github.com/en/github/authenticating-to-github/generating-a-new-gpg-key#generating-a-gpg-key)
  * For the first step, you can use `brew install gpg` instead of dowloading the installation if you prefer
  * **IMPORTANT:** Remember the passphrase you set: this will be the passphrase you use to encrypt and decrypt the secrets time and time again
* [Then follow these instructions to add it to your Github account](https://help.github.com/en/github/authenticating-to-github/adding-a-new-gpg-key-to-your-github-account)

#### Get going with git-secret
Install `git-secret`:
```
brew install git-secret
```

Add yourself as a person who can encrypt and decrypt secrets (this will require having set up your GPG):
```
git secret tell -m
```

Now that you've added yourself, the keyring has changed and the files will need to be re-encrypted before being decrypted:

```
git secret hide
```
(you may be prompted for your passphrase)

Now check to see if you can generate unencrypted versions of the secrets:

```
git secret reveal
```
(you may be prompted for your passphrase)


Or just view the secrets:
```
git secret cat .secrets
```
(you may be prompted for your passphrase)
