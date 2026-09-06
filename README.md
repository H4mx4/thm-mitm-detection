\# Man-in-the-Middle Detection — Network Traffic Analysis



Documentation of three MITM detection techniques from TryHackMe's SOC Level 1 path: ARP spoofing, DNS spoofing, and SSL stripping. Each file breaks down how the attack shows up in traffic and what specifically gave it away.



\## Contents

\- \[Methodology](./methodology.md)

\- \[ARP Spoofing Detection](./arp-spoofing.md)

\- \[DNS Spoofing Detection](./dns-spoofing.md)

\- \[SSL Stripping Detection](./ssl-stripping.md)

\- \[Notes \& Summary](./notes.md)



\## Tools Used

\- Wireshark

\- Filters used: `arp`, `dns`, `http.request.method == "POST"`, `tcp.port == 80` 



\## Note on Scope

This covers detection reasoning and traffic analysis only. Room answers/flags are excluded per TryHackMe's Terms of Service.

