# Wireshark doo dooo do doo...

## Description
Can you find the flag? `shark1.pcapng`.

`The challenge file can be downloaded from picoCTF website and name the file as challenge.pcapng`

Challenge Link -> https://play.picoctf.org/practice/challenge/115?category=4&originalEvent=34&page=1

## Solution

1. Open the file in wireshark.
2. On viewing through Hierarchical statistics here is what I found.

![image](https://user-images.githubusercontent.com/85097320/183053507-0b71871c-eba3-4c79-b1ff-ee9306ab297d.png)

There is some text data present in `HTTP`

3. On viewing the stream:

![image](https://user-images.githubusercontent.com/85097320/183053928-6eebb1d2-afc4-4ac1-b576-3bd96b3d2562.png)

4. The highlighted text has to be `ROT13` to get our flag.
5. Run the below script or use any online tool. [`CyberChef -> https://gchq.github.io/CyberChef/#recipe=ROT13(true,true,false,13)`] 

```python
#solve.py
import codecs
a="cvpbPGS{c33xno00_1_f33_h_qrnqorrs}"
print(codecs.encode(a, 'rot_13'))
```

### Output
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads$ python solve.py
picoCTF{p33kab00_1_s33_u_deadbeef}
```


