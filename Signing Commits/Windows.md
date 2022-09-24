# Windows

In this tutorial we will learn how to sign our commits and verify them on GitHub.

## Step 1: Install GPG

I recommend using https://gpg4win.org/. It may ask for a donation when downloading, but you can just
select 0, and it will let you continue.

## Step 2: Generate a new GPG key

The rest of the steps can be run from the terminal after installing.

Run the following command to create a new GPG key:

```
gpg --full-generate-key
```

Option 1: `1`
Option 2: `4096`
Option 3: `0`
Option 4: `y`

Rest fill out with your personal information. Then you will assign a passphrase to this key. I recommend adding one because then people cannot create commits without you entering in the password.

## Step 3: Verify the new GPG Key

Run the following command:

```
gpg --list-secret-keys --keyid-format LONG
```

This should return something like this
```
--------------------------------------
sec   rsa4096/[THIS_KEY_ID] 2021-07-07 [SC]
      2B18EEB732D15480D40A60D605AE1785E201CE95
uid                 [ultimate] Your Name <your@name.com>
ssb   rsa4096/C98A99F6B0202433 YYYY-MM-DD [E]
```

The part marked `THIS_KEY_ID` is something you should copy to your clipboard right now. We will use this later.

## Step 4: Export the key to GitHub

*NOTE: Your email you used for the GPG key has to be the same as your local Git config email. The email should be the one you used for GitHub*

We need to get the public key block. To do this run the following command replacing [THIS_KEY_ID] with your key id you copied earlier.

```
gpg --armor --export [THIS_KEY_ID]
```

This will generate your public key block. Copy everything including the headers that say BEGIN and END.

Go to https://github.com/settings/keys

Click on "New GPG key" and paste in your copied public key block. Name it something useful like where you will be sigining from.

## Step 5: Configure git to always sign your commits

To make git sign your commits with your GPG key run the following commands:

*If you run 'where.exe gpg' it will tell you the correct file path for the last command.*

```
git config --global user.signingkey [THIS_KEY_ID]
git config --global commit.gpgsign true
git config --global gpg.program "C:\Program Files (x86)\GnuPG\bin\gpg.exe"
```

# Note

Your local git email most match the email you used in your gpg key creation. To make sure it is run:
```
git config --global user.email "[KEY_EMAIL]"
```
