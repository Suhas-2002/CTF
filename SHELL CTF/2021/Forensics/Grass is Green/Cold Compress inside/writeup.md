# Cold Compress inside

## Description
Raj wanted to send a huge chunk of data. Find it.

`The challenge ile is present in the same directory with the name challenge.jpeg.`

## Solution
1. I used binwalk on the image and found out that there was a zip file embedded.
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads$ binwalk challenge.jpeg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 3840 x 2558, 8-bit/color RGBA, non-interlaced
17158270      0x105D07E       Zip archive data, at least v2.0 to extract, compressed size: 18722, uncompressed size: 48441, name: o.exe
17177027      0x10619C3       Zip archive data, at least v2.0 to extract, compressed size: 2987, uncompressed size: 17256, name: o
17180215      0x1062637       End of Zip archive, footer length: 22
```
2. On exctracting and unzipping the zip file, there was a executable file named `o.exe`.
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads/_challenge.jpeg.extracted/105D07E$ ls
o  o.exe
```
3. On running this file I found the flag!
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads/_challenge.jpeg.extracted/105D07E$ chmod +x o.exe
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads/_challenge.jpeg.extracted/105D07E$ ./o.exe
Hello, World!
CRazy_MosQUIto_nEEDS_odoMOS
```
