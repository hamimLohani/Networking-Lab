# Domain

- Install bind9 - `sudo apt install bind9`
- Check dev name - `ip a`
- Add IP - `sudo ip addr add <ip> dev <dev_name>`
- Change to bind directory - `cd /etc/bind`
- copy all text on this zone file - `cat db.local`
- Create new zone file - `sudo nano db.s39.zhjlab.bd`
- paste it

```bash
;
; BIND data file for local loopback interface
;
$TTL    60 # time to live        # rr for roll
@       IN      SOA     ns1.s<rr>.zhjlab.bd. bsse16<rr>.iit.du.ac.bd. (
                              3         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.s<rr>.zhjlab.bd. # rr for roll
@       IN      A       <added_ip>
ns1     IN      A       <added_ip>
```

[Line 4](https://github.com/hamimLohani/Networking-Lab/blob/main/Terminal%20Notes/Line%204.md)

- Serial → Increment when zone update
- Refresh → Secondary server checks every X second
- Retry → If failed, retry after X second
- Expire → After this, secondary discards
- Negative TTL → Cache negative responses
- @ IN NS [ns1.s39.zhjlab.bd](http://ns1.s39.zhjlab.bd/). → This domain is served by ns1
- [ns1.s39.zhjlab.bd](http://ns1.s39.zhjlab.bd/) → 172.17.100.39
- DNS = name → IP translation
- Add zone file - `sudo nano named.conf.local`
- Paste

```bash
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "s<rr>.zhjlab.bd" { # rr for roll
	type master;
	file "/etc/bind/db.s<rr>.zhjlab.bd"; # file path
};
```

- Show live logs - `sudo tail -f /var/log/syslog`
- Restart DNS server - `sudo systemctl restart named.service`
- Reload - `sudo systemctl reload bind9.service`
- `dig [s39.zhjlab.bd](http://s39.zhjlab.bd/) SOA @172.17.100.39` ANSWER=1
