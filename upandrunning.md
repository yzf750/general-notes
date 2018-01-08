Misc Git commands
---------------------------------------------------------
# Update Git repo 
# cd to repo directory and run
```bash
git pull
```


Clone these repos
---------------------------------------------------------
```bash
mkdir ~/pentest-stuff
cd ~/pentest-stuff

# My stuff
git clone https://github.com/yzf750/general-notes.git
git clone https://github.com/yzf750/web-application.git
git clone https://github.com/yzf750/custom-fuzzing.git

# Awsome fuzzlists
git clone https://github.com/danielmiessler/SecLists.git

# Nice fuzzing list
git clone https://github.com/fuzzdb-project/fuzzdb.git

# testssl.sh
# Remember to use alternate openssl binary in bin directory 
git clone https://github.com/drwetter/testssl.sh.git
cp ./testssl.sh/bin/openssl.Linux.x86_64 ./testssl.sh

# Phishery
git clone https://github.com/ryhanson/phishery.git

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

# List of stuff to concider cloning
#git clone https://github.com/xmendez/wfuzz.git
#git clone https://github.com/fuzzdb-project/fuzzdb.git
#git clone https://github.com/minimaxir/big-list-of-naughty-strings.git
#git clone https://github.com/foospidy/payloads.git
```
