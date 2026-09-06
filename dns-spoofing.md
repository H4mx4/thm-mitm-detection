\# Unmasking DNS Spoofing



\## The core idea

DNS spoofing works by racing the legitimate DNS server's response — the attacker sends a fake reply back faster, pointing a domain at an IP they control. If the victim's machine accepts the forged answer first, it never sees the real one.



\## What gave it away

\[Describe what you actually noticed — was it multiple responses to one query? A mismatched IP? Something in the TTL?]



!\[Normal DNS query](screenshots/dns-spoofing/01\_dns\_query\_normal.png)

\[What a clean DNS exchange looked like in your capture]



!\[Suspicious DNS response](screenshots/dns-spoofing/02\_suspicious\_dns\_response.png)

\[The actual mismatch you found]



!\[Multiple responses](screenshots/dns-spoofing/03\_multiple\_responses.png)

\[What you actually saw — how many responses, what was different between them]



\## Filter used

dns

dns.flags.response == 1 \&\& ip.src == 8.8.8.8

dns.flags.response==1

dns \&\& dns.qry.name == "corp-login.acme-corp.local"

dns.flags.response == 1 \&\& ip.src == 8.8.8.8 \&\& dns.qry.name == "corp-login.acme-corp.local"

dns.flags.response == 1 \&\& ip.sr**c != 8.8.8.8 \&**\& dns.qry.name == "corp-login.acme-corp.local"

