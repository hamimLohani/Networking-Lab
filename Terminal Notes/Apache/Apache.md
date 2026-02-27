# Apache

- installation - `sudo apt install apache2`
- verify - `systemctl status apache2`
- check listening port - `ss -tl`
- it will show the port number 80 - `ss -tln`
- rename - `sudo mv index.html index.html.orig` in the directory  - `/var/www/html`
- Change directory - `cd /etc/apache2/sites-available`
- make copy - `sudo cp 000-default.conf 001-mysite.conf`
- edit - `sudo nano 001-mysite.conf`

```jsx
<VirtualHost *:80>
	
	ServerName www.s47.zhjlab.bd # uncomment and add ip

	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/deyversonmygoat # add path and create directoryctory

	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
```

- `cd /var/www`
- Create website directory - `sudo mkdir deyversonmygoat`
- `cd deyversonmygoat`
- add index.html - `sudo nano index.html`
- `cd /etc`
- `sudo nano hosts`
- add hosts

```jsx
127.0.0.1 localhost
127.0.1.1 iit-du-ASUS-EXPERTCENTER-D700ME-D500ME
172.17.100.47 www.s47.zhjlab.bd
172.17.100.49 www.s49.zhjlab.bd
172.17.100.55 www.s55.zhjlab.bd
172.17.100.39 www.s39.zhjlab.bd

# add your domain
```

- Check - `sudo apachectl configtest`
- `sudo a2ensite 001-mysite.conf`
- `sudo systemctl reload apache2`
- check sites enable - `ls -l ../sites-enabled/`
- then test in the browser - [`http://www.s47.zhjlab.bd`](http://www.s47.zhjlab.bd/)