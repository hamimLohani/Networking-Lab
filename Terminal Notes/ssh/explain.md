## File: ssh.md

- **Purpose**: Focused SSH reference for Linux and macOS: installation, status, enabling/disabling, ports, and connection commands.
- **Check ssh (Linux)**: `which sshd` locates the SSH daemon binary to confirm it’s installed.
- **Check ssh (macOS)**: `ssh -V` prints the SSH client version and ensures the binary exists.
- **Uninstall ssh server (Linux)**: `sudo apt purge openssh-server` completely removes the OpenSSH server package.
- **Install ssh server (Linux)**: `sudo apt install openssh-server` installs or reinstalls the SSH server.
- **Install ssh on macOS**: Not needed; SSH is installed by default on macOS.
- **Status (Linux)**: `sudo systemctl status ssh` displays whether the SSH service is active, failing, or stopped.
- **Status (macOS)**: `sudo systemsetup -getremotelogin` reports whether Remote Login (SSH) is on or off.
- **Enable ssh (Linux)**: `sudo systemctl enable ssh` configures the SSH service to start on boot.
- **Enable ssh (macOS)**: `sudo systemsetup -setremotelogin on` turns on Remote Login, allowing SSH connections.
- **Disable ssh (Linux)**: `sudo systemctl disable ssh` prevents SSH from starting automatically.
- **Disable ssh (macOS)**: `sudo systemsetup -setremotelogin off` turns off Remote Login so SSH access is blocked.
- **Change port config**: `/etc/ssh/sshd_config` is the main SSH server configuration file on both Linux and macOS; you edit and uncomment the `Port` line here to change the listen port.
- **Reboot**: `sudo reboot` restarts the machine (ensuring all service changes are fully applied).
- **Delete known hosts (Linux)**: `rm .ssh/known_hosts ssh/known_hosts.old` removes stored host fingerprints from the user’s home directory.
- **Delete known hosts (macOS)**: `rm ~/.ssh/known_hosts` clears known SSH host entries for the current user.
- **SSH login (Linux)**: `sudo ssh -oPort=<port> <usrname>@<ip>` connects to a server using a custom port via the `-oPort=` option.
- **SSH login (macOS)**: `sudo ssh -p <port> <usrname>@<ip>` uses `-p` to specify the non‑default SSH port.
- **SFTP login (Linux)**: `sudo sftp -oPort=<port> <usrname>@<ip>` opens a secure file transfer session on a custom port.
- **SFTP login (macOS)**: `sudo sftp -p <port> <usrname>@<ip>` uses `-p` to set the SFTP port.
- **SFTP commands**: `get` downloads a file from the server; `put` uploads a file to the server.
- **Logout**: `exit` closes the ssh/sftp session and returns to the previous shell.
- **Check ports (macOS)**: `netstat -an | grep LISTEN` lists listening sockets and helps verify if sshd is listening.
- **Check ports (Linux)**: `sudo lsof -i -n` shows processes with open network sockets and their ports.

