# Line 4

# **First Understand What This Is**

This is an **SOA (Start of Authority)** record.

It declares:

- Who is the primary DNS server
- Who is the admin
- Zone timing control

`@   IN   SOA   [ns1.s39.zhjlab.bd](http://ns1.s39.zhjlab.bd/).   [bsse1639@iit.du.ac.bd](mailto:bsse1639@iit.du.ac.bd).`

- @ → root of the domain
- IN → Internet class
- SOA → Start Of Authority Record
- [ns1.s39.zhjlab.bd](http://ns1.s39.zhjlab.bd) → Primary name server
- bsse1639@iit.du.ac.bd. → admin email (@ replaced by .)

### With DOT (.)

[`ns1.s39.zhjlab.bd](http://ns1.s39.zhjlab.bd/).`

This is called a **Fully Qualified Domain Name (FQDN)**.

The final . means:

> “This is the absolute full domain name. Do NOT append anything.”
> 

DNS internally treats everything relative to the current zone **unless** you end it with a dot.

### Without DOT (.)

[`ns1.s39.zhjlab.bd`](http://ns1.s39.zhjlab.bd/)

BIND assumes it is **relative to current zone**. Since current zone [`s39.zhjlab.bd`](http://s39.zhjlab.bd) . It becomes [`ns1.s39.zhjlab.bd.s39.zhjlab.bd`](http://ns1.s39.zhjlab.bd.s39.zhjlab.bd/) . So without a dot → BIND auto-appends the zone name.

### Same Logic for email

> This dot represent the root domain name. Browser hide dot, but DNS doesn’t.
>