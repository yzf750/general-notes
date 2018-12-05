Install Kali then configure VirtualBox addons
---------------------------------------------------------
```bash
apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get install virtualbox-guest-x11
reboot now
```

Misc Git commands
---------------------------------------------------------
```bash
# Update Git repo 
# cd into repo directory and run
git pull

# Update all repos in parent subdirectories
# cd to parent directory and run....
find . -type d -maxdepth 1 -exec git --git-dir={}/.git --work-tree=$PWD/{} pull origin master \;
```

Clone these repos
---------------------------------------------------------
```bash
mkdir ./pentest-stuff
cd pentest-stuff

# My stuff
git clone https://github.com/yzf750/general-notes.git
git clone https://github.com/yzf750/web-application.git
git clone https://github.com/yzf750/custom-fuzzing.git

# Awsome fuzzlists
git clone https://github.com/danielmiessler/SecLists.git

# Nice fuzzing list
git clone https://github.com/fuzzdb-project/fuzzdb.git

# Dirbuster lists for use with BURP
git clone https://github.com/digination/dirbuster-ng.git

# Nice list of lists for web application
git clone https://github.com/nathanmyee/SVNDigger.git

# testssl.sh
# Remember to use alternate openssl binary in bin directory 
git clone https://github.com/drwetter/testssl.sh.git
cp ./testssl.sh/bin/openssl.Linux.x86_64 ./testssl.sh

# Phishery
git clone https://github.com/ryhanson/phishery.git

# Wordlists, rockyou, app_specific, ip_cams, etc...
git clone https://github.com/huntergregal/wordlists

# Bug Bounty Cheat Sheet
git clone https://github.com/EdOverflow/bugbounty-cheatsheet.git

# FuzzLists (large Download)
git clone https://github.com/1N3/IntruderPayloads.git

# F5 Cookie decoder
git clone https://github.com/DarkLighting/bigip-cookie-decoder.git

# All things
git clone https://github.com/swisskyrepo/PayloadsAllTheThings.git

# Nice list of robots.txt disallowed (Good to use with dirbuster)
git clone https://github.com/danielmiessler/RobotsDisallowed.git

# Deserilization (Tomcat, etc...)
git clone https://github.com/joaomatosf/jexboss.git

#NoSQLMap
git clone https://github.com/codingo/NoSQLMap.git
# cd NoSQLMap
# python setup.py install
# python nosqlmap.py

# XSS Scanner - still testing
# pip3 install fuzzywuzzy
# python3 xsstrike.py -u "http://your.url.goes/here?ddd=xxxxx" --fuzzer
git clone https://github.com/s0md3v/XSStrike.git

# List of stuff to concider cloning
#git clone https://github.com/xmendez/wfuzz.git
#git clone https://github.com/minimaxir/big-list-of-naughty-strings.git
#git clone https://github.com/foospidy/payloads.git

```
