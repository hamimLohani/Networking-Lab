# Networking

Category: Network

## October 29, 2025

- Command: `chmod +x <filename>` gives execution permission
- delete default ip -`sudo ip r del default via <ip>` mac - `sudo route delete default`
- add default ip -`sudo ip r add default via <ip>` mac - `sudo route add default <ip>`
- `ip r` show default ip
- add ip -`sudo ip addr add <ip> dev <device_name>` mac - `sudo ifconfig <device_name> alias <ip> netmask <mask_ip>`
- delete ip -`sudo ip addr del <ip> dev <device_name>` mac - `sudo ifconfig <device_name> -alias <ip>`
- show ip -`sudo ip addr show en0` mac - `ifconfig en0`

## November 12, 2025

- For check interface `ip l` mac - `networksetup -listallhardwareports`
- show current interface (mac) - `route get default`
- It will show:

```bash
en6: <UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500 status DOWN
    link/ether 00:e0:99:00:0a:22 brd ff:ff:ff:ff:ff:ff
```

- My ethernet interface `en6`
- Then set ip `sudo ip addr add 192.168.2.1/24 dev <device_name>`
- To see ip `ifconfig en6`
- Then ping your partner `ping 192.168.2.2`
- Delete ip `sudo ip addr del 192.168.2.1/24 dev en6`
- Trace lookback ip: `sudo ip route add <others lookback ip> via <others public ip> dev <device_name>`
- then ping lookback ip `ping <others lookback ip>`

## November 19, 2025

- host mac address `ip n`

```bash
192.168.100.100 dev enp2se lladdr f4:8e:38:81:4b:74 STALE
```

- host mac address f4:8e:38:81:4b:74
- check hop - `ping -R <ip>`
- how to reach ip - `mtr -n <DNS_server_name>`
- see the hop local - `tracepath -n <DNS_server_name>` (UDP)
- du DNS - `dns1.du.ac.bd`
- 

## January 7, 2026

- check - `which ssdh` mac - `ssh -V`
- uninstall - `sudo apt purge openssh-server` mac - its default
- check - `which sshd`
- install - `sudo apt install openssh-server`
- status check - `sudo systemctl status ssh` mac - `sudo systemsetup -getremotelogin`
- enable ssh - `sudo systemctl enable ssh` mac - `sudo systemsetup -setremotelogin on`
- disable - `sudo systemctl disable ssh` mac - `sudo systemsetup - setremoteligin off`
- delete previous host - `rm .ssh/known_hosts ssh/known_hosts.old` mac - `rm ~/.ssh/known_hosts`
- logout - `exit` mac - same
- change port - `sudo nano /etc/ssh/sshd_config` file mac - same
- and reboot - `sudo reboot` mac - same
- service check - `sudo lsof -i -n`
- `ss -tuln`
- Login with ssh - `sudo ssh -oPort=2233 <usrname>@<ip>` mac - `sudo ssh -p 2233 <usrname>@<ip>`
- Login (file access) - `sudo sftp -oPort=2233 <usrname>@<ip>` mac - `sudo sftp -p 2233 <usrname>@<ip>`
- `put` for send file
- `get` for take file