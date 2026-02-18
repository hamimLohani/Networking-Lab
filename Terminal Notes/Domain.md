# Domain

- Install bind9 - `sudo apt install bind9`
- Check dev name - `ip a`
- Add IP - `sudo addr add <ip> dev <dev_name>`
- Change to bind directory - `cd /etc/bind`
- copy all text - `cat db.local`
- Create zone file - `sudo nano db.s39.zhjlab.bd`
- paste it

```bash
;
; BIND data file for local loopback interface
;
$TTL    60                   # rr for roll
@       IN      SOA     ns1.s<rr>.zhjlab.bd. bsse16<rr>@iit.du.ac.bd. (
                              3         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.s<rr>.zhjlab.bd. # rr for roll
ns1     IN      A       <added_ip>
```

- `sudo nano named.conf.local`
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

- `sudo tail -f /var/log/syslog`
- `sudo systemctl restart named.service`
- for reload - `sudo systemctl reload bind9.service`
- `dig [s39.zhjlab.bd](http://s39.zhjlab.bd/) SOA @172.17.100.39` ANSWER=1