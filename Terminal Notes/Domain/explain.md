## File: Domain.md

- **Purpose**: Guide for creating and configuring a custom DNS zone in BIND9, including zone file contents and related settings.
- **Install BIND9**: `sudo apt install bind9` installs the DNS server software.
- **Check interface name**: `ip a` lists network interfaces so you know which device to bind an IP to.
- **Add IP to interface**: `sudo ip addr add <ip> dev <dev_name>` assigns an IP address to a specific network interface.
- **Enter BIND directory**: `cd /etc/bind` moves into the directory with BIND configuration and zone files.
- **Inspect template zone**: `cat db.local` prints a sample zone file used as a template.
- **Create new zone file**: `sudo nano db.s39.zhjlab.bd` creates and opens the zone file for your custom domain.
- **Paste template**: You paste and then customise the contents from `db.local` into this new file.
- **Zone file header**: `$TTL 60` sets default TTL; the `SOA` record line defines the primary nameserver and admin email using placeholders (`s<rr>`, `bsse16<rr>`).
- **SOA fields**: Serial, Refresh, Retry, Expire, and Negative Cache TTL control how secondaries sync and how long data is cached.
- **Nameserver record**: `@ IN NS ns1.s<rr>.zhjlab.bd.` declares `ns1` as the authoritative nameserver for the zone.
- **A records**: `@` and `ns1` A records map the domain root and nameserver hostname to the configured `<added_ip>`.
- **Explanation link**: The link to `Line 4` points to a separate note that deeply explains the SOA line.
- **Field summaries**: Bullets briefly define Serial, Refresh, Retry, Expire, and Negative TTL behavior.
- **NS meaning**: A note clarifies that `@ IN NS ns1.s39.zhjlab.bd.` means this domain is served by that nameserver.
- **DNS concept**: Reminder that DNS maps names to IP addresses.
- **Add zone to named.conf.local**: `sudo nano named.conf.local` opens the file where your new zone is declared.
- **Zone declaration**: The `zone "s<rr>.zhjlab.bd" { type master; file "/etc/bind/db.s<rr>.zhjlab.bd"; };` block tells BIND to load your zone file as master.
- **View live logs**: `sudo tail -f /var/log/syslog` streams system logs, including BIND messages, to debug configuration issues.
- **Restart DNS server**: `sudo systemctl restart named.service` restarts the DNS daemon to apply changes.
- **Reload bind9**: `sudo systemctl reload bind9.service` reloads configuration without a full restart.
- **Test with dig**: `dig s39.zhjlab.bd SOA @172.17.100.39` queries the SOA record from your new DNS server; `ANSWER=1` confirms a successful single answer.

