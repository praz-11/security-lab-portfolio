# Wireshark Filters Used

## Baseline analysis
dns
tls
tcp
udp

## Malicious investigation
ip.addr == 153.92.1.49
nbns
kerberos.CNameString
http && ip.addr == 153.92.1.49
