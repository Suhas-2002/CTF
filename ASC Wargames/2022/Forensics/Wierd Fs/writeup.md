# Wierd Fs

## Description

our sysadmin wasn't able to mount this weird filesystem to extract the needed file, can you mount it?.

`The challenge file can be found in the same directory with the name as challenge.img`

## Solution

1. By using binwalk on the file i could find out that there were several files embedded.

**Command :**
```console
binwalk challenge.img
```
**Output**
```console
DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
292047        0x474CF         mcrypt 2.2 encrypted data, algorithm: blowfish-448, mode: CBC, keymode: 8bit
308431        0x4B4CF         mcrypt 2.2 encrypted data, algorithm: blowfish-448, mode: CBC, keymode: 8bit
324815        0x4F4CF         mcrypt 2.2 encrypted data, algorithm: blowfish-448, mode: CBC, keymode: 8bit
341199        0x534CF         mcrypt 2.2 encrypted data, algorithm: blowfish-448, mode: CBC, keymode: 8bit
357583        0x574CF         mcrypt 2.2 encrypted data, algorithm: blowfish-448, mode: CBC, keymode: 8bit
373967        0x5B4CF         mcrypt 2.2 encrypted data, algorithm: blowfish-448, mode: CBC, keymode: 8bit
390351        0x5F4CF         mcrypt 2.2 encrypted data, algorithm: blowfish-448, mode: CBC, keymode: 8bit
406735        0x634CF         mcrypt 2.2 encrypted data, algorithm: blowfish-448, mode: CBC, keymode: 8bit
423119        0x674CF         mcrypt 2.2 encrypted data, algorithm: blowfish-448, mode: CBC, keymode: 8bit
1138688       0x116000        XML document, version: "1.0"
1933312       0x1D8000        XML document, version: "1.0"
1941524       0x1DA014        Zlib compressed data, compressed
2576239       0x274F6F        mcrypt 2.2 encrypted data, algorithm: blowfish-448, mode: CBC, keymode: 8bit
2617199       0x27EF6F        mcrypt 2.2 encrypted data, algorithm: blowfish-448, mode: CBC, keymode: 8bit
2711572       0x296014        Zlib compressed data, compressed
3317780       0x32A014        Zlib compressed data, compressed
3768320       0x398000        Zip archive data, encrypted at least v1.0 to extract, compressed size: 35, uncompressed size: 23, name: Flag.txt
3768515       0x3980C3        End of Zip archive, footer length: 22
3977236       0x3CB014        Zlib compressed data, compressed
4149248       0x3F5000        gzip compressed data, last modified: 1970-01-01 00:00:00 (null date)
4153344       0x3F6000        gzip compressed data, last modified: 1970-01-01 00:00:00 (null date)
19636224      0x12BA000       XML document, version: "1.0"
20381696      0x1370000       XML document, version: "1.0"
20398100      0x1374014       Zlib compressed data, compressed
```
2. Extract these files by using the command :
```console
binwalk --dd=".*" challenge.img
```
3. I could find out that there is a zip file with a embedded file Flag.txt.
4. The zip file is password protected so, I cracked the password using fcrackzip

**Command :**
```console
fcrackzip -v -u -D -p rockyou.txt 398000.zip
```
5. Th above command cracked and uprooted the Flag.txt.
6. On viewing the file I found the flag!

**Command :**
```console
cat challenge.img
```
**Output**
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads$ cat Flag.txt
ASCWG{M4C_4N6_1$_Co0l}
```
