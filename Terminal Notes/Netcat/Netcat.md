# Netcat

## File Transfer

**B (Receiver):**
- `nc -l -p 8080 > received_file.txt` (Linux)
- `nc -l 8080 > received_file.txt` (macOS)

**A (Sender):**
- `nc <B_ip> 8080 < file.txt`

## Chat/Communication

**Server:**
- `nc -l 8080`

**Client:**
- `nc <server_ip> 8080`

## Port Scanning

- `nc -zv <host> <port>` - Check single port
- `nc -zv <host> 20-80` - Scan port range

## Localhost Testing

- Terminal 1: `nc -l 8080`
- Terminal 2: `nc localhost 8080`

## UDP Mode

- Listen: `nc -ul 5000`
- Connect: `nc -u <host> 5000`

## Banner Grabbing

- `nc -v <host> <port>` - See service banner

## Options

- `-l` - Listen mode
- `-p` - Port (Linux)
- `-v` - Verbose
- `-z` - Port scan (no data)
- `-u` - UDP mode
