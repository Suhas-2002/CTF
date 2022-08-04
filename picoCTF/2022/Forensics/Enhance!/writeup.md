# Enhance!

## Desciption
Download this image file and find the flag.

`The challenge file is present in the same folder with the name challenge.svg.`

## Solution
The flag was found by using strings command.

**Command**
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads$ strings challenge.svg | grep "p"
```
**Output**

![image](https://user-images.githubusercontent.com/85097320/182855382-aa125e33-5be2-4e1d-87ae-66605cdb052e.png)

On combining all the highlighted characters and removing the spaces in between gives our flag.

Challenge Link -> https://play.picoctf.org/practice/challenge/265?category=4&originalEvent=70&page=1
