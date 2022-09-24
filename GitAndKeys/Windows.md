# Windows

In this Tutorial we wil learn how to commit our changes to git using SSH with Windows.

## Step 1: Create a key

Create a new SSH key pair if you do not have one already.

If not run the following command:

```
ssh-keygen
```

Next we have to copy our public key. When creating your key it will give you the directory path of
the key. Most commonly if you left all options to default values the key is located in:

```
C:\Users\YOUR_USERNAME\.ssh
```

Go to the directory where you key is located.

![Shows an image of what the folder should look like](GitAndKeys/img/FileExplorer.png)

Next Right-Click 'id_rsa.pub' and click open with Notepad. If you do not have Notepad use another
text editor.

![Shows an image of how to open with notepad](GitAndKeys/img/OpenWithNotepad.png)

Copy the contents of the public key and save it for the next step.

## Step 2: Add the key to GitHub

Go to https://github.com/settings/keys and click "New SSH key"

![Key Button Image](GitAndKeys/img/UploadKey.png)

You should name the key from where you would be using the key from.

![Save Key Image](GitAndKeys/img/SaveKey.png)

Click "Add SSH Key" to finish adding it.

## Testing

If you would like to test if everything worked run the following command:

```
ssh -T git@github.com
```

You should get an output like this:

```
Hi james-gavin! You've successfully authenticated, but GitHub does not provide shell access.
```

## Conclusion

You have now created an SSH key to use with GitHub!

When cloning a GitHub repository make sure you select "SSH" instead of "HTTPS" as your remote origin.
