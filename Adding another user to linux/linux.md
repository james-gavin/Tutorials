# Linux

In this tutorial we will learn how to add another user to our virtual server so they may too connect to it. We will

## Step 1: Create the user and

Create a new user by running the following commands:

```
sudo useradd -m -d /home/username -s /bin/bash username
```

*Replace username with the name you want to be displayed*

## Step 2: Set the password

In most cases you will want to set their password so they can either sign in or use sudo. I would personally recommend to disable password log in options as it is insecure.

Run the following command to set their password (you may need to sudo it):

'''
passwd username
'''

## Step 3: Transfer their public ssh keys to the

You will need to setup a folder in the users home directory called .ssh and copy the public keys to a file named authorized_keys.

## Step 4: Setup permissions

For most of the tutorial you have been acting as *not* the user you created so we need to give this new user permissions.

*You may need to use sudo in these commands*

First run this command to ensure the directory is owned by the new user:

'''
chown -R username:username /home/username/.ssh
'''

Next run these commands to ensure only the new user has permissions to access their .ssh:

'''
chmod 700 /home/username/.ssh
chmod 600 /home/username/.ssh/authorized_keys
'''

## Step 5: (Optional) Grant them sudo access

If you so choose you can grant this new user sudo access with the following command:

'''
sudo usermod -a -G sudo username
'''

They will use the password you set for them eariler to use sudo. They can always change their password by running:

'''passwd username'''

