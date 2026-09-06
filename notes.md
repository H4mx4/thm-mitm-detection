\# Notes \& Summary



\## What stood out across all three

\- ARP has no authentication built in — that single design gap is what makes spoofing possible at all

\- DNS spoofing comes down to a race condition — whichever response arrives first wins, real or fake

\- SSL stripping is the sneakiest of the three because there's no obvious "attack" moment — just a connection quietly staying on HTTP



\## If I saw this in a real environment

1\. I'd isolate the suspicious host first, before doing anything else — stop the bleeding before investigating further

2\. I'd check authentication logs around the same timestamp to see if any sessions were actually compromised, not just theoretically at risk

3\. I'd check whether the same gap (missing HSTS, no static ARP entries, etc.) exists elsewhere on the network, not just the one host I caught



\## Honest gaps

\- Finding the right Wireshark filter took longer than I expected — I knew conceptually what I was looking for but had to try a few filter combinations before narrowing in on the correct one for each technique

\- Identifying \*which\* IP was actually suspicious wasn't always obvious at first glance — I had to cross-reference against the baseline traffic to tell normal activity from the anomaly, rather than it jumping out immediately

