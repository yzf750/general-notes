Search for found md5 and sha1 hashes using password lists
---------------------------------------------------------
MD5
```bash
#!/bin/bash
[ $# -lt 2 ] && echo "Usage: <path-to-password-file> <hash-to-find>" && exit 1
filename=$1
md5sumhash=$2
while read line; do
	# echo $filename
	# echo $md5sumhash
	if echo "$line" | md5sum | awk '{print $1}' | grep -q "$md5sumhash"; then echo "Hash:" "$md5sumhash" "Password:" "$line" ; fi
done < "$filename"
exit 0
```
SHA1
```bash
#!/bin/bash
[ $# -lt 2 ] && echo "Usage: <path-to-password-file> <hash-to-find>" && exit 1
filename=$1
sha1sumhash=$2
while read line; do
	# echo $filename
	# echo $sha1sumhash
	if echo "$line" | sha1sum | awk '{print $1}' | grep -q "$sha1sumhash"; then echo "Hash:" "$sha1sumhash" "Password:" "$line"; fi
done < "$filename"
exit 0
```
Generate SHA1 and MD5 hash from text

```bash
# SHA1
echo -n password | sha1sum | awk '{print $1}'
# MD5
echo -n password | md5sum | awk '{print $1}'
```
Convert password lists to MD5 or SHA1 hashes

```bash
#!/bin/bash
# Use to convert password lists to MD5 or SHA1 hashes
# filename: pass-to-hash.sh

[ $# -lt 3 ] && echo "Usage: <path-to-password-file> <patch-to-output-file> <hash-type MD5|SHA1" && exit 1

inputfilename=$1
outputfilename=$2
hashtype=$3

while read line; do

	if [ $hashtype == "MD5" ];
	then 
		echo -n $line | md5sum | awk '{print $1}' >> $outputfilename
	fi

	if [ $hashtype == "SHA1" ];
	then 
		echo -n $line | sha1sum | awk '{print $1}' >> $outputfilename
	fi

done < "$inputfilename"
exit 0
```


