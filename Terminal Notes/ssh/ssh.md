# ssh

## Check ssh

Linus - `which sshd` 

Mac - `ssh -V`

## Uninstallation

Linux - `sudo apt purge openssh-server`

## Installation

Linux - `sudo apt install openssh-server` 

Mac - default installed

## Status Check

Linux - `sudo systemctl status ssh`

Mac - `sudo systemsetup -getremotelogin`

## Enable ssh

Linux - `sudo systemctl enable ssh`

Mac - `sudo systemsetup -setremotelogin on`

## Disable ssh

Linux - `sudo systemctl disable ssh`

Mac - `sudo systemsetup -setremotelogin off`

## Change Port

Linux, Mac path - `/etc/ssh/sshd_config`

uncomment port, then change

## Reboot

Linux, Mac - `sudo reboot`

## Delete Previous Hosts

Linux - `rm .ssh/known_hosts ssh/known_hosts.old`

Mac - `rm ~/.ssh/known_hosts`

## Log in With ssh

Linux - `sudo ssh -oPort=<port> <usrname>@<ip>`

Mac - `sudo ssh -p <port> <usrname>@<ip>`

## Log in With sftp

Linux - `sudo sftp -oPort=<port> <usrname>@<ip>`

Mac - `sudo sftp -p <port> <usrname>@<ip>`

get file - `get`

put file - `put`

## Log out

`exit`

## Check Port

Mac - `netstat -an | grep LISTEN`

Linux - `sudo lsof -i -n`