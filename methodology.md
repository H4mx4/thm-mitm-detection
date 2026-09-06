\# Methodology: Spotting MITM Activity in Traffic



\## Approach

Each of the three techniques below (ARP spoofing, DNS spoofing, SSL stripping) targets a different point in the network stack, so I treated them separately — but the underlying process was the same each time:



1\. \*\*Look at what "normal" looks like first\*\* — before I could spot something wrong, I needed a baseline (clean ARP resolution, a normal DNS query/response, a proper HTTPS handshake)

2\. \*\*Filter down to the anomaly\*\* — Wireshark captures a lot of unrelated traffic, so the real work is narrowing filters until only the suspicious packets are left

3\. \*\*Confirm it's actually the indicator, not noise\*\* — e.g. a duplicate ARP reply could be a misconfigured device, not an attack, so I checked for the specific pattern the room pointed to

4\. \*\*Think about what this means defensively\*\* — what would actually catch this in a live network, not just in a lab



See each individual file for the specific indicators I found in that technique.

