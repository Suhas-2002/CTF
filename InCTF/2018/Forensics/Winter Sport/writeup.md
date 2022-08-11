# Winter Sport

## Description
I have a friend named Jake.We were watching a football tournament on one fine chilly morning. Meanwhile Jake's sister Susan did something mischievous which cause Jake to lose some really important data. We could only find this piece of evidence, can you recover it for him?

`The challenge file is present in the same directory with the name challenge.zip`

## Solution

1. The challenge contains a zip file so, on using binwalk :

**Command**
```console
binwalk challenge.zip
```
**Output**
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads$ binwalk challenge.zip

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             Zip archive data, at least v2.0 to extract, uncompressed size: 7591, name: file.pdf
7317          0x1C95          End of Zip archive, footer length: 22
```

2. There is a embedded zip file which I extracted using binwalk.

**Command**
```console
binwalk --dd=".*" challenge.zip
```
3. On unzipping the zip archive I found a pdf!

**Command**
```console
unzip 0.zip
```

**Output**
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads/_challenge.zip.extracted$ unzip 0.zip
Archive:  0.zip
  inflating: file.pdf
```
4. The pdf has nothing usefull but on using binwalk again I got a omg.pdf which had got whitespaces.

5. The challenge name says winter and its actually suggesting us to use stegsnow which is used for whitespace steganography!

6. On using stegsnow I found the flag :)

```console
stegsnow -C omg.pdf
```

**Output**
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads/_challenge.zip.extracted/_file.pdf.extracted/361$ stegsnow -C omg.pdf
inctf{w3lcom3_t0_7h3_w0rld_0f_whit3sp4c3}
```
