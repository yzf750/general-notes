Create simple packet then send it.
-----------------------------------
```
from scapy.all import *
A = 'source.ip'
B = 'detination.ip'
C = source.port
D = dst.port
payload = "stuff to put in the payload"
spoofed_packet = IP(src=A, dst=B) / TCP(sport=C, dport=D) / payload
send(spoofed_packet)
```


This one lets scapy deal with the MAC layer (by using the "send" function) More testing required
-----------------------------------
from scapy.all import *
ip_map = {"1.2.3.4": "10.0.0.1", "1.2.3.5": "10.0.0.2"}
for p in PcapReader("single-packet.pcap"):
    if IP not in p:
        continue
    p = p[IP]
    # if you want to use a constant map, only let the following line
    p.src = "source.ip"
    p.dst = "dst.ip"
    # if you want to use the original src/dst if you don't find it in ip_map
    p.src = ip_map.get(p.src, p.src)
    p.dst = ip_map.get(p.dst, p.dst)
    # if you want to drop the packet if you don't find both src and dst in ip_map
    if p.src not in ip_map or p.dst not in ip_map:
        continue
    p.src = ip_map[p.src]
    p.dst = ip_map[p.dst]
    # as suggested by @AliA, we need to let Scapy compute the correct checksum
    del(p.chksum)
    # then send the packet
    send(p)
    
Import a pcap file and change the source and destinaion ip's
-----------------------------------
```python    
from scapy.all import *
from scapy.utils import rdpcap

pkts=rdpcap("single-packet.pcap")
for pkt in pkts:
     pkt[IP].src= new_src_ip="src.ip"
     pkt[IP].dst= new_dst_ip="dst.ip"
     send(pkt)
 ```
  
  
    
