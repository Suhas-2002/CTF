# shark on wire 2

## Description
We found this `packet capture`. Recover the flag that was pilfered from the network.

`The challenge file is present in the same directory with the name challenge.pcap`

## Solution

1. Open the file in wireshark.
2. On analysing through udp stream there was a interesting pattern.
3. udp port 22 had packets orginating and ending with the same port source port as `5000`.

 ![image](https://user-images.githubusercontent.com/85097320/183048701-0636ffa9-b1d1-4776-9442-de2387097c45.png)

![image](https://user-images.githubusercontent.com/85097320/183048642-7d54b25d-545e-4133-adc6-abb007623d87.png)

4. We can see that the second message originates from source port `5112`. `112` is a number which should alert us, since its `ASCII` representation is `p`, which matches the flag template.
5. The flag was obtained on conerting all the source ports to ASCII and this can be done by running the below python script!

```python
#solve.py
from scapy.all import *

flag = ""

packets = rdpcap('challenge.pcap')
for packet in packets:
    # if the packet is a UDP packet going to point 22
    if UDP in packet and packet[UDP].dport == 22:
        flag += chr(packet[UDP].sport - 5000)
print("Flag: {}".format(flag))
```

### Output
```console
hsp@DESKTOP-9IK0E1G:/mnt/d/Downloads$ python solve.py
Flag: picoCTF{p1LLf3r3d_data_v1a_st3g0}
```

Challenge Link -> https://play.picoctf.org/practice/challenge/84?category=4&originalEvent=1&page=1
