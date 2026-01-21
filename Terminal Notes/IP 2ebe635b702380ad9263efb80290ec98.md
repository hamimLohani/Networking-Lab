# IP

## Check IP

Mac - `ifconfig <interface>`

Linux - `ip a`

or - `sudo ip addr show <interface>`

## Check Interface

Mac - `networksetup -listallhardwareports`

Linux - `ip l`

## Show Current Interface

Mac - `route get default`

## Show Default IP

Linux - `ip r`

Mac - `route get default`

## Add Default IP

Linux - `sudo ip r add default via <ip>`

Mac - `sudo route add default <ip>`

## Delete Default IP

Linux - `sudo ip r del default via <ip>`

Mac - `sudo route delete default` 

## Add IP

Linux - `sudo addr add <ip> dev <interface>`

Mac - `sudo ifconfig <interface> alias <ip> netmask <mask_ip>`

## Delete IP added ip

Linux - `sudo addr del <ip> dev <interface>`

Mac - `sudo ifconfig <interface> -alias <ip>`

## Show Mac Address

Linux - `ip n`

or - `sudo ip addr show <interface>`

Mac - `ifconfig <interface> | grep ether`

## Look-back IP

Mac - `sudo ifconfig <lookback_interface> alias <ip> netmask <mask_ip>`

Linux - `sudo addr add <ip> dev <lookback_interface>`

in Linux ip is to be with mask (/n)

## Delete Added IP

Mac - `sudo addr del <ip> dev <lookback_interface>`

Linux - `sudo ifconfig <lookback_interface> -alias <ip>`

# Ping Look-back IP

## Trace Look-back IP

Linux - `sudo ip route add <other_lookback_ip> via <other_public_ip> dev <interface>`

ping - `ping <ip>`