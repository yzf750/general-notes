Kali Apache setup
=================

Start Stop
-------------
```bash
service apache2 start
service apache2 stop
```

Enable SSL
---------------------
```bash
cp /etc/apache2/sites-available/default-ssl.conf /etc/apache2/sites-enabled/default-ssl.conf
a2enmod ssl
systemctl restart apache2
```

Install Attacks
---------------------
```bash
# Keylogger.js
cd /var/www/html
git clone https://github.com/JohnHoder/Javascript-Keylogger.git
# chmod -R 777 ./Javascript-Keylogger (untested)

# jsfuck
git clone https://github.com/aemkei/jsfuck.git
# http://localhost/jsfuck/index.html
```
