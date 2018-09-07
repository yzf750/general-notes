Create simple packet then send it.
from scapy.all import *
A = 'source.ip'
B = 'detination.ip'
C = source.port
D = dst.port
payload = "stuff to put in the payload"
spoofed_packet = IP(src=A, dst=B) / TCP(sport=C, dport=D) / payload
send(spoofed_packet)
