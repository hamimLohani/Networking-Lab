## File: Apache.md

- **Purpose**: Step‑by‑step checklist to create and host a simple website on Apache on Linux, using a custom virtual host and `/etc/hosts` entries.
- **Install Apache**: `sudo apt install apache2` installs the Apache web server package.
- **Verify service**: `systemctl status apache2` checks whether Apache is running correctly.
- **Check listening port**: `ss -tl` / `ss -tln` list TCP listening ports so you can confirm Apache is listening on port 80.
- **Rename default index**: `sudo mv index.html index.html.orig` in `/var/www/html` hides the default Apache welcome page so your own site can show instead.
- **Go to vhost config dir**: `cd /etc/apache2/sites-available` moves into the directory where site (virtual host) configs live.
- **Copy default vhost**: `sudo cp 000-default.conf 001-mysite.conf` duplicates the default site config as a starting point for your custom site.
- **Edit new vhost**: `sudo nano 001-mysite.conf` opens the new config so you can customise it.
- **VirtualHost block**: The `<VirtualHost *:80> ... </VirtualHost>` block defines how Apache should serve requests on port 80.
- **ServerName**: `ServerName www.s47.zhjlab.bd` tells Apache which hostname should map to this virtual host.
- **ServerAdmin**: `ServerAdmin webmaster@localhost` sets the admin contact address for this site (mainly used in error pages/logs).
- **DocumentRoot**: `DocumentRoot /var/www/deyversonmygoat` sets the directory from which Apache will serve files for this site.
- **Logs**: `ErrorLog` and `CustomLog` define where Apache writes error and access logs for the site.
- **Create web root**: `cd /var/www` then `sudo mkdir deyversonmygoat` create the directory that matches the `DocumentRoot`.
- **Create index**: `cd deyversonmygoat` and `sudo nano index.html` create the site’s homepage file.
- **Edit hosts file**: `cd /etc` then `sudo nano hosts` opens the system hosts file.
- **/etc/hosts entries**: The `127.0.0.1` lines map hostnames like `www.s47.zhjlab.bd` to IP addresses so you can reach the site by name without external DNS.
- **Config test**: `sudo apachectl configtest` validates Apache config syntax before enabling the new site.
- **Enable vhost**: `sudo a2ensite 001-mysite.conf` enables the new virtual host configuration.
- **Reload Apache**: `sudo systemctl reload apache2` reloads configs so the new site becomes active.
- **Check enabled sites**: `ls -l ../sites-enabled/` shows which vhost configs are active (symlinked).
- **Browser test**: Opening `http://www.s47.zhjlab.bd` in a browser confirms that DNS/hosts, Apache, and your site are all working together.

