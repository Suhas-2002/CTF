# GO Deep!

## Description
Our one of the agent gave us this file and said "Go Deep!"

`The challenge file is present in the same directory with the name challenge.zip`

## Solution

1. The challenge consists of a zip file which on unzipping gives us a `file.wav` audio file.
2. The challenge says Go Deep!. This Deep says that we have to dig into the audio file.
3. There is tool name `DeepSound` which is used in audio steganography.
4. But on uploading the audio file in `DeepSound` it asks for a password.
5. The password is `shell` which was found on using `exiftool`

**Command**
```console
exiftool file.wav
```

**Output**
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads$ exiftool file.wav
ExifTool Version Number         : 11.88
File Name                       : file.wav
Directory                       : .
File Size                       : 19 MB
File Modification Date/Time     : 2022:08:11 18:52:32+05:30
File Access Date/Time           : 2022:08:13 17:54:18+05:30
File Inode Change Date/Time     : 2022:08:12 18:42:03+05:30
File Permissions                : rwxrwxrwx
File Type                       : WAV
File Type Extension             : wav
MIME Type                       : audio/x-wav
Encoding                        : Microsoft PCM
Num Channels                    : 2
Sample Rate                     : 44100
Avg Bytes Per Sec               : 176400
Bits Per Sample                 : 16
Artist                          : https://www.youtube.com/watch?v=dQw4w9WgXcQ
Product                         : https://www.youtube.com/watch?v=dQw4w9WgXcQ
Genre                           : password:shell
Date Created                    : Password:shell
Comment                         : Password: shell
Duration                        : 0:01:53
```
6. By using `shell` as a password a file named `Deep Flag` was extracted.

![image](https://user-images.githubusercontent.com/85097320/184494191-25fab59b-aa8e-405c-a4b0-d0d718e792bc.png)
![image](https://user-images.githubusercontent.com/85097320/184494212-49092a3f-c9a3-40c7-a1cf-4f41fd4232f0.png)

7. The flag was present inside this file :)
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads$ cat Deep\ Flag.txt
SHELL{y0u_w3r3_7h1nk1ng_R3ally_D33p}
```

