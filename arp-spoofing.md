\# Detecting ARP Spoofing



\## What ARP spoofing actually breaks

ARP has no built-in authentication — any device on the network can claim to own an IP address, and everyone else just believes it. An attacker sends out ARP replies claiming their MAC address belongs to, say, the gateway's IP, and traffic starts routing through them instead.



\## What I looked for

The clearest giveaway is a duplicate ARP reply — the same IP address getting claimed by two different MAC addresses in a short window.



!\[ARP baseline](screenshots/arp-spoofing/01\_arp\_baseline.png)

\[Describe what you actually saw — the normal IP-to-MAC mapping before anything looked wrong]



!\[Duplicate ARP alert](screenshots/arp-spoofing/02\_duplicate\_arp\_alert.png)

\[Describe the actual alert/warning Wireshark showed you]



!\[MAC/IP mismatch](screenshots/arp-spoofing/03\_mac\_ip\_mismatch.png)

\[Which IP was affected, and what the two conflicting MAC addresses were]



\## Filter used

arp

arp.opcode == 1

arp.opcode == 2

arp.isgratuitous

arp \&\& arp.src.proto\_ipv4 == 192.168.10.1 \&\& eth.src == 02:aa:bb:cc:00:01

arp.opcode == 2 \&\& arp.src.proto\_ipv4 == 192.168.10.1

arp.opcode ==2 \&\& \_ws.col.info contains "192.168.10.1 is at 

arp.opcode == 2 \&\& arp.src.proto\_ipv4 == 192.168.10.1 \&\& eth.src == 02:fe ( contains answer , so cant write full )

arp.duplicate-address-detected || arp.duplicate-address-frame



