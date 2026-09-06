\# Spotting SSL Stripping in Action



\## What's actually happening

SSL stripping works by sitting in the traffic path and quietly downgrading a connection that should be HTTPS down to plain HTTP, before the browser gets the chance to establish encryption. Most people don't check the address bar closely enough to notice the missing padlock.



\## What gave it away

\[Was it a missing redirect? Visible plaintext data? A downgrade you could see in the request flow?]



!\[Expected HTTPS](screenshots/ssl-stripping/01\_expected\_https.png)

\[What the connection should have looked like]



!\[Downgrade evidence](screenshots/ssl-stripping/02\_downgrade\_evidence.png)

\[What exactly changed]



!\[Cleartext data](screenshots/ssl-stripping/03\_cleartext\_data.png)

\[What was visible — redact any real values before saving the screenshot]



\## Filter used

tls || ssl

tls.handshake.type == 1 \&\& tls.handshake.extensions\_server\_name == "corp-login.acme-corp.local"

dns.flags.response == 1 \&\& ip.src == 192.168.10.55 \&\& dns.qry.name == "corp-login.acme-corp.local"

http \&\& ip.src == 192.168.10.10 \&\& ip.dst == 192.168.10.55



