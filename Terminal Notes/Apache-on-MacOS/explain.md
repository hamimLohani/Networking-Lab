## File: Apache-on-MacOS.md

- **Purpose**: Quick guide for enabling and configuring the built‑in Apache server on macOS with a simple virtual host and local domain.
- **Check Apache status**: `sudo apachectl status` confirms whether the macOS Apache service is running.
- **Start/stop/restart**: `sudo apachectl start/stop/restart` control the Apache service lifecycle.
- **Open default site**: `open http://localhost` opens the Apache default page in your browser.
- **Main config**: `sudo nano /etc/apache2/httpd.conf` edits the primary Apache configuration file.
- **Include vhost config**: Adding `Include /private/etc/apache2/extra/httpd-vhosts.conf` tells Apache to load the separate virtual hosts file.
- **Edit vhost file**: `sudo nano /etc/apache2/extra/httpd-vhosts.conf` opens the file where named virtual hosts are defined.
- **VirtualHost block**: `<VirtualHost *:80> ... </VirtualHost>` defines a site that listens on port 80.
- **ServerName**: `ServerName mysite.local` sets the hostname that will route to this vhost.
- **DocumentRoot**: `DocumentRoot "/Library/WebServer/Documents/mysite"` specifies the directory that holds the site’s files.
- **Directory block**: The `<Directory ...>` section configures access and overrides for the site folder (e.g. `Require all granted` allows all clients).
- **Logs**: `ErrorLog` and `CustomLog` lines set where Apache writes site‑specific logs.
- **Change to web root**: `cd /Library/WebServer/Documents` goes to the macOS Apache document root.
- **Create site folder**: `sudo mkdir mysite` creates a directory matching the `DocumentRoot`.
- **Create index file**: `sudo nano index.html` creates the main HTML page for the site.
- **Sample HTML**: The provided `<!DOCTYPE html> ...` block is a simple test page that will be served for `mysite.local`.
- **Edit hosts file**: `sudo nano /etc/hosts` opens the system hosts file.
- **Local domain mapping**: `127.0.0.1 mysite.local` maps the custom domain to localhost so the browser can resolve it.
- **Copy default index**: `sudo cp index.html.en index.html` is an alternative way to create a basic `index.html` from a template.
- **Config test**: `sudo apachectl configtest` checks Apache configuration syntax after your changes.
- **Restart Apache**: `sudo apachectl restart` reloads configuration so the new virtual host becomes active.

