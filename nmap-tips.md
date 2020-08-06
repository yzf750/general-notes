Parse IP addresses from nmap scans and send output to other tools
-----------------
Note: Could use almost any variable for "/https/" - run up to the awk command to find a good variable
```bash
nmap -PN -p 443 --open -oG - xxx.xxx.xxx.xxx/24 | awk '/https/{print $2}' | while read IP; do ./testssl.sh $IP | aha > $IP-ssl-audit.html ; done
```

Scan for services and versions (Seems to find more Services)
-------------------------------
```
nmap -A -T4 -v xxx.xxx.xxx.xxx
```

Scan for services and versions using specific port (Seems to find more Services)
-------------------------------
```
nmap -A -T4 -p 1-65535 xxx.xxx.xxx.xxx
```

Scan for services and versions
-------------------------------
```
nmap -A -T4 -F -v xxx.xxx.xxx.xxx
```

Find open SMB Shares
-------------------------------
```
nmap -T4 -v -oA shares --script smb-enum-shares --script-args smbuser=username,smbpass=password -p445 192.168.1.0/24
```

Enumerate SMB Users
-------------------------------
```
nmap -sU -sS --script=smb-enum-users -p U:137,T:139 192.168.11.200-254 
```
Parse searchsploit results using nmap scan xml 
---------------------------------------------------------
```bash
nmap -v -sV -oX file.xml xxx.xxx.xxx.xxx
searchsploit --nmap ./file.xml
```

