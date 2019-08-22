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
```
cp /etc/apache2/sites-available/default-ssl.conf /etc/apache2/sites-enabled/default-ssl.conf
a2enmod ssl
systemctl restart apache2
```
