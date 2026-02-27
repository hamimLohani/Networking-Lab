# Apache on MacOS

- check apache server - `sudo apachectl status`
- Start - `sudo apachectl start`
- Stop - `sudo apachectl stop`
- Restart - `sudo apachectl restart`
- Open server - `open http://localhost`
- Edit main config file - `sudo nano /etc/apache2/httpd.conf`
- add - `Include /private/etc/apache2/extra/httpd-vhosts.conf`
- Edit virtual Host file - `sudo nano /etc/apache2/extra/httpd-vhosts.conf`

```bash
<VirtualHost *:80>
    ServerName mysite.local
    DocumentRoot "/Library/WebServer/Documents/mysite"

    <Directory "/Library/WebServer/Documents/mysite">
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog "/private/var/log/apache2/mysite_error.log"
    CustomLog "/private/var/log/apache2/mysite_access.log" common
</VirtualHost>
```

- Server file  (web root) - `cd /Library/WebServer/Documents`
- Create Website Directory - `sudo mkdir mysite`
- Create html file - `sudo nano index.html`

```bash
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>My Site</title>
</head>
<body>
<h1>My macOS Apache Site 🚀</h1>
</body>
</html>
```

- Edit Hosts file - `sudo nano /etc/hosts`

```bash
127.0.0.1 mysite.local
```

- Copy - `sudo cp index.html.en index.html`
- Check configure - `sudo apachectl configtest`
- Restart - `sudo apachectl restart`
-