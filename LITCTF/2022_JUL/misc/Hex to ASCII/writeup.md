# Hex to ASCII

## Description

Do you know how to speak hexadecimal? I love speaking in hexadecimal. In fact, in HexadecimalLand, we like to say
`4c49544354467b74306f6c355f346e645f77336273317433735f6172335f763372795f696d70307274346e745f6630725f4354467d`

## Solution
The given text is Hex enconded and on converting it to ASCII we get our flag.

On running the following script we get our flag!
```python
#solve.py
import binascii
a = "4c49544354467b74306f6c355f346e645f77336273317433735f6172335f763372795f696d70307274346e745f6630725f4354467d"
print(binascii.unhexlify(a))
```
**Output**
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads$ python solve.py
b'LITCTF{t0ol5_4nd_w3bs1t3s_ar3_v3ry_imp0rt4nt_f0r_CTF}'
```

Challenge Link -> https://lit.lhsmathcs.org/ctfchal
