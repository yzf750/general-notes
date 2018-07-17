Hashcat Notes
=============
Built in Charsets
-----------------
```bash
?l = abcdefghijklmnopqrstuvwxyz
?u = ABCDEFGHIJKLMNOPQRSTUVWXYZ
?d = 0123456789
?s = «space»!"#$%&'()*+,-./:;<=>?@[]^_`{|}~
?a = ?l?u?d?s
?b = 0x00 - 0xff
```
Brute force all characters sets password min = 0, password max - 256 (Will take a long time, better to sniper using techniques below)
-------------------------------------------------------------------------------------------------------------------------------------
```bash
# "-a 3" to specify brute forcing
# "-m 100" specifies SHA1
# "hasheszz.txt" file containing hashes
hashcat64.exe -a 3 -m 100 hasheszz.txt
```
Cracks using Custom Charsets
-------------------------
```bash
# "-a 3" to specify brute forcing
# "-m 100" specifies SHA1
# "hasheszz.txt" file containing hashes
# "-1" specifies that only the "pasword123" characters will be used.
# Will only crack a hash if the password is 7 characters (count the mask)
hashcat64.exe -a 3 -m 100 hasheszz.txt -1 pasword123 ?1?1?1?1?1?1?1
```
Tests for 8 character hashed passwords using only lower case letters (Use Charsets from above) (these are eell's not one's)
-------------------------
```bash
# "-a 3" to specify brute forcing
# "-m 100" specifies SHA1
# "hasheszz.txt" file containing hashes
# "?l?l?l?l?l?l?l?l" specifies the length of the password, in this case 8 characters
hashcat64.exe -a 3 -m 100 hasheszz.txt ?l?l?l?l?l?l?l?l
```
Tests for 8 character hashed passwords using custom character set
-------------------------
```bash
# "-a 3" to specify brute forcing
# "-m 100" specifies SHA1
# "hasheszz.txt" file containing hashes
# -1 specifies the custom custom set to use
# "?1?1?1?1?1?1?1" specifies the length if the password as well as the position of each character
hashcat64.exe -a 3 -m 100 hasheszz.txt -1 paswword123 ?1?1?1?1?1?1?1
```
Cracks using minimum and maximum length password
-------------------------
```bash
# "-m 100" specifies SHA1
# "-a 3" to specify brute forcing
# "-O" hashcat seems to like this??
# "--status" displays the status
# "--status-timer=5" how often to update the status, in this case every 5 seconds.
# "--increment" Tells hashcat you want to increment the length (will start at 1 character password unless you specify "--increment-min=??")
# "--increment-min=12" Tells hashcat you want to start at a minimum length, in the case the minimum is 12 characters
# "hasheszz.txt" file containing hashes
# "-1" specifies the desired character set to use. In this case a custom charset is used "123456789password"
# The maximum length is determined by the mask, in this case "?1?1?1?1?1?1?1?1?1?1?1?1" specifies the max length of 12 in this case.
hashcat64.exe -m 100 -O -a 3 --status --status-timer=5 --increment --increment-min=12 hasheszz.txt -1 123456789password ?1?1?1?1?1?1?1?1?1?1?1?1

# Same as above but his time used built in charset
# "-1 ?l?d" specifies what built in character sets you want to use, in this case you will be using both lowercase and digits for all positions
hashcat64.exe -m 100 -O -a 3 --status --status-timer=5 --increment --increment-min=12 hasheszz.txt -1 ?l?d ?1?1?1?1?1?1?1?1?1?1?1?1
```
Cracks hashes from a list of passwords
-------------------------
```bash
# "-m 100" specifies SHA1
# "-O" hashcat seems to like this??
# "--status" displays the status
# "--status-timer=5" how often to update the status, in this case every 10 seconds.
# "hasheszz.txt" file containing hashes
# C:\path\to\your\password-lists\rockyou-75.txt
hashcat64.exe -m 100 -O --status --status-timer=10 hasheszz.txt C:\path\to\your\password-lists\rockyou-75.txt
```
