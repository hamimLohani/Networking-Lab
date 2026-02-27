## File: IP.md

- **Purpose**: Practical notes for viewing and manipulating IP addresses, routes, and interfaces on macOS and Linux.
- **Check IP (macOS)**: `ifconfig <interface>` shows IP configuration and status for a specific interface (e.g. `en0`).
- **Check IP (Linux)**: `ip a` lists all interfaces and their IP addresses.
- **Alternative Linux view**: `sudo ip addr show <interface>` shows detailed IP info for one interface only.
- **List interfaces (macOS)**: `networksetup -listallhardwareports` maps hardware ports to interface names.
- **List interfaces (Linux)**: `ip l` shows network interfaces and their states (UP/DOWN, MAC, etc.).
- **Show current interface (macOS)**: `route get default` displays which interface is used for the default route.
- **Show default IP (Linux)**: `ip r` prints the routing table to see the default gateway and routes.
- **Show default IP (macOS)**: `route get default` also reveals the default gateway on macOS.
- **Add default route (Linux)**: `sudo ip r add default via <ip>` sets the default gateway for outbound traffic.
- **Add default route (macOS)**: `sudo route add default <ip>` adds a default route via a given IP.
- **Delete default route (Linux)**: `sudo ip r del default via <ip>` removes a specific default gateway.
- **Delete default route (macOS)**: `sudo route delete default` removes the current default route.
- **Add IP (Linux)**: `sudo addr add <ip> dev <interface>` adds an IP address to an interface.
- **Add IP (macOS)**: `sudo ifconfig <interface> alias <ip> netmask <mask_ip>` adds an alias IP with a netmask.
- **Delete added IP (Linux)**: `sudo addr del <ip> dev <interface>` removes an IP from an interface.
- **Delete added IP (macOS)**: `sudo ifconfig <interface> -alias <ip>` removes an alias IP.
- **Show MAC (Linux)**: `ip n` or `sudo ip addr show <interface>` show ARP neighbours and hardware addresses.
- **Show MAC (macOS)**: `ifconfig <interface> | grep ether` prints the MAC address line for an interface.
- **Loopback IP (macOS)**: `sudo ifconfig <lookback_interface> alias <ip> netmask <mask_ip>` adds a loopback IP.
- **Loopback IP (Linux)**: `sudo addr add <ip> dev <lookback_interface>` adds a loopback IP (with `/mask` notation).
- **Mask note (Linux)**: Loopback IP in Linux is typically written with CIDR, e.g. `10.0.0.1/32`.
- **Delete loopback IP (macOS)**: `sudo addr del <ip> dev <lookback_interface>` (note: swapped in your note, but intention is removing the address).
- **Delete loopback IP (Linux)**: `sudo ifconfig <lookback_interface> -alias <ip>` removes a loopback alias (naming reversed, but purpose is deletion).
- **Trace route via other loopback**: `sudo ip route add <other_lookback_ip> via <other_public_ip> dev <interface>` sets a route to another host’s loopback via their public IP.
- **Ping**: `ping <ip>` sends ICMP echo requests to test connectivity to an IP (including loopbacks or remote hosts).

