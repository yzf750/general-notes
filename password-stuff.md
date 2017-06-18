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
