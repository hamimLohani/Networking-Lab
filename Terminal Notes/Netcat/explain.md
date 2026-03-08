## File: Netcat.md

- **Purpose**: Essential netcat (nc) commands for file transfer, communication, port scanning, and network testing on Linux and macOS.
- **File transfer receiver (Linux)**: `nc -l -p 8080 > received_file.txt` listens on port 8080 and saves incoming data to a file.
- **File transfer receiver (macOS)**: `nc -l 8080 > received_file.txt` listens without the `-p` flag (BSD-style netcat).
- **File transfer sender**: `nc <B_ip> 8080 < file.txt` connects to the receiver's IP and sends the file.
- **Chat server**: `nc -l 8080` opens a listening socket for text communication.
- **Chat client**: `nc <server_ip> 8080` connects to the server for bidirectional text chat.
- **Port scan single**: `nc -zv <host> <port>` checks if a specific port is open with verbose output.
- **Port scan range**: `nc -zv <host> 20-80` scans multiple ports in a range.
- **Localhost test**: Terminal 1 runs `nc -l 8080` to listen; Terminal 2 runs `nc localhost 8080` to connect on the same machine.
- **UDP listen**: `nc -ul 5000` listens on UDP port 5000 instead of TCP.
- **UDP connect**: `nc -u <host> 5000` connects to a UDP port.
- **Banner grabbing**: `nc -v <host> <port>` connects with verbose mode to see service banners and version info.
- **Option -l**: Listen mode; makes netcat wait for incoming connections.
- **Option -p**: Specifies the port number on Linux (not needed on macOS).
- **Option -v**: Verbose output; shows connection details.
- **Option -z**: Zero-I/O mode for port scanning; no data is sent.
- **Option -u**: UDP mode; uses UDP protocol instead of TCP.
