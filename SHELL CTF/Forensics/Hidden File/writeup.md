# Hidden File
## Description
Our Agent gave us this image can you find whats there with this image?

`The challenge file is present in the same directory with the name challenge.jpg`

## Solution

1. On using exiftool on the image I found the password which suggests that there is some file hidden!
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads$ exiftool challenge.jpg
ExifTool Version Number         : 11.88
File Name                       : challenge.jpg
Directory                       : .
File Size                       : 2011 kB
File Modification Date/Time     : 2022:08:13 15:33:07+05:30
File Access Date/Time           : 2022:08:13 19:23:32+05:30
File Inode Change Date/Time     : 2022:08:13 19:22:41+05:30
File Permissions                : rwxrwxrwx
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : inches
X Resolution                    : 72
Y Resolution                    : 72
Exif Byte Order                 : Big-endian (Motorola, MM)
Make                            : the password is shell;
Artist                          : the password is shell
XP Author                       : the password is shell
Padding                         : (Binary data 2060 bytes, use -b option to extract)
About                           : uuid:faf5bdd5-ba3d-11da-ad31-d33d75182f1b
Creator                         : the password is shell
Image Width                     : 3000
Image Height                    : 4500
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 3000x4500
Megapixels                      : 13.5
```
2. Then I used steghide inorder to check and extract embedded files (if any).
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads$ steghide extract -sf challenge.jpg
Enter passphrase:
wrote extracted data to "Hidden Files.zip".
```
3. A zip file named `Hidden Files` was extracted and on unzipping it I found out the below files:
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads$ unzip Hidden\ Files.zip
Archive:  Hidden Files.zip
  inflating: se3cretf1l3.pdf
  inflating: something.jpg
  inflating: flag.zip
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads$ cd Hidden\ Files/
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads/Hidden Files$ ls
flag.zip  se3cretf1l3.pdf  something.jpg
```
4. The something.jpg had a barcode which on scanning leads to a youtube link which is useless.
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads/Hidden Files$ zbarimg something.jpg
Connection Error (Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory)
Connection Null
QR-Code:https://www.youtube.com/watch?v=dQw4w9WgXcQ
scanned 1 barcode symbols from 1 images in 0.16 seconds
```
5. The `flag.zip` file has a `flag.txt` which is password encrypted.
6. I found the password on analysing the pdf file named `se3cretf1l3.pdf`.
7. On using an online steganography tool for pdf I found out this:

**Original PDF**
![image](https://user-images.githubusercontent.com/85097320/184497741-2b5a94da-7b57-4e22-b480-6e0da11936da.png)

**On Analysing**

![image](https://user-images.githubusercontent.com/85097320/184497766-a71e6e0e-186f-41fb-8bd1-a0428bf0d7dc.png)

**It says the key is `shellctf`. This is the password for the `flag.txt` file**

8. On unzipping the `flag.zip` file and opening the `flag.txt` file with the password obtained I found the flag.

```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads/Hidden Files$ 7z x flag.zip

7-Zip [64] 16.02 : Copyright (c) 1999-2016 Igor Pavlov : 2016-05-21
p7zip Version 16.02 (locale=C.UTF-8,Utf16=on,HugeFiles=on,64 bits,8 CPUs Intel(R) Core(TM) i5-1035G1 CPU @ 1.00GHz (706E5),ASM,AES-NI)

Scanning the drive for archives:
1 file, 248 bytes (1 KiB)

Extracting archive: flag.zip
--
Path = flag.zip
Type = zip
Physical Size = 248


Enter password (will not be echoed):
Everything is Ok

Size:       30
Compressed: 248
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads/Hidden Files$ cat flag.txt
shell{y0u_g07_th3_flag_N1c3!}
```
