---
title: "Cara compress file dengan zip di Ubuntu"
date: 2023-01-05T09:59:56+07:00
draft: false # Set 'false' to publish
description: "ZIP is an archive file format that supports lossless data compression. A ZIP file may contain one or more files or directories that may have been compressed"
categories:
- Linux
tags:
- ubuntu
- zip
layout: "simple"
---

Untuk install zip, silakan install menggunakan perintah dibawah.

![Zip](/images/2023-01-05/zip.png)

Ubuntu
```
apt install zip unzip -y
```

Lagsung saja gunakan perintah berikut:
```
zip namafile.zip namafile -9 -v
```

Untuk directory:
```
zip -r namafile.zip namafile -9 -v
```

Catatan: -9 untuk compress secara lebih baik, -v untuk menampilkan output

Option:
```
-f	freshen: only changed files
-u	update: only changed or new files
-d	delete entries in zipfile
-m	move into zipfile (delete OS files)
-r	recurse into directories
-j	junk (don’t record) directory names
-0	store only
-l	convert LF to CR LF (-ll CR LF to LF)
-1	compress faster
-9	compress better
-q	quiet operation
-v	verbose operation/print version info
-c	add one-line comments
-z	add zipfile comment
-@	read names from stdin
-o	make zipfile as old as latest entry
-x	exclude the following names
-i	include only the following names
-F	fix zipfile (-FF try harder)
-D	do not add directory entries
-A	adjust self-extracting exe
-J	junk zipfile prefix (unzipsfx)
-T	test zipfile integrity
-X	eXclude eXtra file attributes
-y	store symbolic links as the link instead of the referenced file
-e	encrypt
-n	don’t compress these suffixes
-h2	show more help
```