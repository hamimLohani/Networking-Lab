## File: Networking.md

- **Purpose**: Date‑tagged lab notes collecting useful networking commands for Linux and macOS (IP, routes, SSH, tracing, etc.).

### Section: October 29, 2025

- **Execution permission**: `chmod +x <filename>` allows a script or binary to be executed.
- **Delete default IP/route (Linux)**: `sudo ip r del default via <ip>` removes a specific default route.
- **Delete default IP/route (macOS)**: `sudo route delete default` clears the current default route.
- **Add default IP/route (Linux)**: `sudo ip r add default via <ip>` adds a new default route via a gateway.
- **Add default IP/route (macOS)**: `sudo route add default <ip>` sets the default gateway.
- **Show default route (Linux)**: `ip r` shows the routing table, including the default route.
- **Add IP (Linux)**: `sudo ip addr add <ip> dev <device_name>` gives an interface a new IP.
- **Add IP (macOS)**: `sudo ifconfig <device_name> alias <ip> netmask <mask_ip>` adds an alias IP on macOS.
- **Delete IP (Linux)**: `sudo ip addr del <ip> dev <device_name>` removes an IP from an interface.
- **Delete IP (macOS)**: `sudo ifconfig <device_name> -alias <ip>` removes an alias IP.
- **Show IP (Linux)**: `sudo ip addr show en0` shows addresses for interface `en0`.
- **Show IP (macOS)**: `ifconfig en0` shows configuration for `en0` on macOS.

### Section: November 12, 2025

- **Check interfaces (Linux)**: `ip l` lists interfaces (links) and their states.
- **Check interfaces (macOS)**: `networksetup -listallhardwareports` maps ports to interface names.
- **Show current interface (macOS)**: `route get default` reveals which interface handles default traffic.
- **Sample output**: The `en6` example shows interface flags, MTU, and MAC address from `ifconfig`.
- **Identify ethernet interface**: Note that `en6` is the ethernet interface used in the lab.
- **Set IP (Linux)**: `sudo ip addr add 192.168.2.1/24 dev <device_name>` assigns a subnet IP to the interface.
- **Verify IP**: `ifconfig en6` is used to confirm the interface’s IP settings.
- **Ping partner**: `ping 192.168.2.2` tests connectivity to another host in the same subnet.
- **Remove IP**: `sudo ip addr del 192.168.2.1/24 dev en6` deletes the IP from the interface.
- **Trace loopback IP**: `sudo ip route add <others lookback ip> via <others public ip> dev <device_name>` adds a route so you can reach another host’s loopback IP via their public IP.
- **Ping loopback**: `ping <others lookback ip>` confirms that the static route works.

### Section: November 19, 2025

- **Show MAC table**: `ip n` displays neighbour (ARP) entries, including IP to MAC mappings.
- **Example ARP entry**: The `192.168.100.100 ... lladdr f4:8e:38:81:4b:74` line shows an IP and its MAC address.
- **Extract MAC**: The MAC `f4:8e:38:81:4b:74` is the host’s hardware address for that IP.
- **Ping with record route**: `ping -R <ip>` requests routers to record the route in the IP header (limited hops).
- **mtr**: `mtr -n <DNS_server_name>` continuously traces route and packet loss to a server (numeric output).
- **tracepath**: `tracepath -n <DNS_server_name>` shows hop paths using UDP probes.
- **University DNS**: `dns1.du.ac.bd` is given as the example DNS server used in the lab.

### Section: January 7, 2026

- **Check ssh (Linux)**: `which ssdh` (typo, meant `sshd`) finds the OpenSSH server binary.
- **Check ssh (macOS)**: `ssh -V` shows the installed SSH client version.
- **Uninstall ssh server (Linux)**: `sudo apt purge openssh-server` removes the server package.
- **Default on macOS**: Note that ssh is installed by default on macOS (no uninstall example given).
- **Check sshd path**: `which sshd` confirms the sshd binary location.
- **Install ssh server (Linux)**: `sudo apt install openssh-server` installs the SSH daemon.
- **Service status (Linux)**: `sudo systemctl status ssh` checks the ssh service.
- **Service status (macOS)**: `sudo systemsetup -getremotelogin` shows whether Remote Login is on.
- **Enable ssh (Linux)**: `sudo systemctl enable ssh` enables service at boot.
- **Enable ssh (macOS)**: `sudo systemsetup -setremotelogin on` enables Remote Login.
- **Disable ssh (Linux)**: `sudo systemctl disable ssh` disables automatic start.
- **Disable ssh (macOS)**: `sudo systemsetup - setremoteligin off` (typo) is intended to disable Remote Login.
- **Delete known hosts (Linux)**: `rm .ssh/known_hosts ssh/known_hosts.old` clears cached hostkey entries.
- **Delete known hosts (macOS)**: `rm ~/.ssh/known_hosts` deletes the known hosts file for the user.
- **Logout**: `exit` ends an ssh/sftp shell session (same on macOS and Linux).
- **Change ssh port**: `sudo nano /etc/ssh/sshd_config` opens the SSH server config for port and other changes.
- **Reboot**: `sudo reboot` restarts the system (applies low‑level config changes).
- **Service check (Linux)**: `sudo lsof -i -n` lists listening services and open network connections.
- **Service check (Linux alt)**: `ss -tuln` lists listening TCP/UDP sockets with numeric ports.
- **SSH login (Linux)**: `sudo ssh -oPort=2233 <usrname>@<ip>` connects to a server on a non‑standard port.
- **SSH login (macOS)**: `sudo ssh -p 2233 <usrname>@<ip>` is the macOS syntax for specifying port.
- **SFTP login (Linux)**: `sudo sftp -oPort=2233 <usrname>@<ip>` opens an SFTP session.
- **SFTP login (macOS)**: `sudo sftp -p 2233 <usrname>@<ip>` uses `-p` to set the port.
- **SFTP commands**: `put` uploads files; `get` downloads files within an SFTP session.

