# GitHub

In this Tutorial we wil learn how to commit our changes to git using SSH.

1. Create a key
2. Add the key to GitHub

## Step 1: Create a key

We have to create our SSH key. You could use a key you already have created but in our case we will create a brand new key for this machine.

In this example I am using Ubuntu 22.04 LTS

Run the following command to generate a new key (you should follow default instructions if you do not know what you are doing):

```
ssh-keygen
```

Next copy the output of your PUBLIC key:

```
cat ~/.ssh/id_rsa.pub
```

## Step 2: Add the key to GitHub

Go to https://github.com/settings/keys and click "New SSH key"

You should name the key from where you would be using the key from.

Click "Add SSH Key" to finish adding it.

## Notes

When copying a github repository make sure you select "SSH" instead of "HTTPS" as your remote origin.
