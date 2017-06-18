Parse IP addresses from nmap scans and send output to other tools
-----------------
Note: Could use almost any variable for "/https/" - run up to the awk command to find a good variable
```
nmap -PN -p 443 --open -oG - xxx.xxx.xxx.xxx/24 | awk '/https/{print $2}' | while read IP; do ./testssl.sh $IP | aha > $IP-ssl-audit.html ; done
```
Scan for services and versions
-------------------------------
```
nmap -A -T4 -F -v xxx.xxx.xxx.xxx
```
