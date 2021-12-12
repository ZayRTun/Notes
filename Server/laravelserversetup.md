**Home**
- [Home](../index.md)
---

# Laravel Vultr Server Setup

## Creating ssh keys to access server from your computer

`ssh-keygen -t rsa -b 4096 -C "goldenland"`

## then you will b prompted to Enter file in which to save the key
`(/home/zay/.ssh/id_rsa): /home/zay/.ssh/id_goldenland`

## to copy set the ssh key on the server from the `.ssh` directory:
`ssh-copy-id -i id_goldenland.pub root@45.77.244.159`

# Add new user account
**Create a new user account with the `adduser` command. Use a strong password for the new user. You can enter values for the user information, or press ENTER to leave those fields blank.**
```bash
# adduser example_user
Adding user `example_user' ...
Adding new group `example_user' (1001) ...
Adding new user `example_user' (1001) with group `example_user' ...
Creating home directory `/home/example_user' ...
Copying files from `/etc/skel' ...
New password:
Retype new password:
passwd: password updated successfully
Changing the user information for example_user
Enter the new value, or press ENTER for the default
        Full Name []: Example User
        Room Number []:
        Work Phone []:
        Home Phone []:
        Other []:
Is the information correct? [Y/n] y
```
#Add the User to the Sudo Group
##Add the new user to the sudo group with `usermod`.
`# usermod -aG sudo example_user`

### To switch user
`# su - example_user`

## To add ssh to this new user
**first create a `.ssh` directory `mkdir .ssh`**

**then cd into `.ssh` and create and edit file with `vi authorized_keys`**

**then copy and paste the previously created `ssh keys`**

## To restrict any other users
- `sudo vi /etc/ssh/sshd_config`

**the edit the following line to no**

- `PermitRootLogin no`
- `PasswordAuthentication no`

**Finally then you need to restart the system for the changes to take effect**
- `sudo reboot`
