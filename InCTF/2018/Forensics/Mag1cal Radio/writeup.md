# Mag1cal Radio

## Description
 A number station in Russia broadcasted a series of encoded messages to one of it's intelligence agency. We have been able to get a piece of that message along with a picture hidden by one of the spy. Decode the transmitted data and be a hero!!
 
 `The link for challenge files are present in the folder named challenge`
 
 ## Solution
 
1. Firstly, I used binwalk on png file and there so important files embedded.
**Command**
```console
binwalk challenge.png
```
**Output**
```console
DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 5184 x 3456, 8-bit/color RGBA, non-interlaced
41            0x29            Zlib compressed data, default compression
25002756      0x17D8304       MySQL ISAM index file Version 1
35573037      0x21ECD2D       MySQL ISAM index file Version 1
```
2. Apart from png there is a mp3 file in this challenge. On viewing the morse code this was result found : 

 ![image](https://user-images.githubusercontent.com/85097320/183260472-1eb6fa89-b891-4424-8e19-c4324fc7939a.png)
 
3. As none of these worked I used steg solve on png file and found this!

 ![image](https://user-images.githubusercontent.com/85097320/183260659-ee526f5e-b833-4c0d-ad9a-452df237dc68.png)
 
`looks like some password :)`
 
4. Then I used StegoMagic on the audio file and extracted the secret text which resulted a png file.

 ![image](https://user-images.githubusercontent.com/85097320/183260718-6dfb9e9c-3b53-4829-b66a-06a9d2c86d04.png)

5. This did ask for password, and I procided the same (`1517`) which worked right.
 
6. This was the image present in the extraction.
 
 ![image](https://user-images.githubusercontent.com/85097320/183260766-c38125a5-f6f6-45ac-8e54-13434a138129.png)
 
A QR Code!

7. As the image had a QR Code I used zbarimg and it redirected me here.

Command
```console
zbarimg new.png
```

Output
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads$ zbarimg flag.png
Connection Error (Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory)
Connection Null
QR-Code:http://qrs.ly/ai7bsyn
scanned 1 barcode symbols from 1 images in 0.03 seconds
```
QR-Code:http://qrs.ly/ai7bsyn

![image](https://user-images.githubusercontent.com/85097320/183260861-a2329081-58c8-4786-97b2-0a6c82fac073.png)

This string is nothing but the reversed string of a **Malbolge program**

8. Reversed string

```D'`;_9K!<Y|98Vg5v@,+O<oLn%l6F4EV${d!>PO^)]xqYutm3Tpinglkd*KJfedc\[Z~A]\[TxXWVU7Mq43OHlLE-CBG@d'=BA@?>7[5{3270/.R,+*)M'm+*)(!Ef$#zy~w={tyxwvo5mrkji/Pfkjcb(I_d]\"`B^WV[TYXWPtTS54Jn1MFjJIB*FE>b%A:?87[|43876/Sts10/.'K+*j"!~De#"!~}v<]yxwputm3Tpinglkd*Kg`edcb[Z~^@\[ZSwQVUTMLp32HGLKDh+GFE>bBA@"8=<5Yz870T4t2+*)M-,l$H('g%|{"!x>|^tyxqp6nVl2Sinmled*hg`H^$EaZ_X]Vz=SXQPUTSLKPImGFKJIHAe?'C<;@9]=}5Y981w/4-,P0po-&%*#Gh&%|Bz!~w|{zsr8pXn4rkSi/gfkd*Kgfedc\"ZY^]\UTxX:PtT65QJn1MLEDIBfF(>bO```

9. On runnig this in a online Malbolge compiler I got the flag!!!!

**Output**

![image](https://user-images.githubusercontent.com/85097320/183261013-b23c52fa-1aa5-4496-96b3-1114038cf221.png)
