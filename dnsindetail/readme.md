DNS in detail
=============

Learn how DNS works and how it helps you access internet services.

## What is DNS?

DNS (Domain Name System) resolves easy-to-remember website hostnames to the
unique IP addresses each device on the Internet has.

### (1)

_What does DNS stand for?_

> Domain Name System

## Domain Hierarchy

Root domain: "."

A TLD (Top-Level Domain) is the most righthand part of a domain name.
  - gTLD (generic TLD): .com / .org / .edu / .gov / .mil
    - purpose: commercial / organisation / education / government / military
    - new ones: .io, .online, .biz etc.
    - https://data.iana.org/TLD/tlds-alpha-by-domain.txt
  - ccTLD (country code TLD): where a site is based geographically

Second-Level Domain: `tryhackme` from `tryhackme.com`
  - max. 63 chars, only w/ a-Z0-9 and hyphens (not at start/end or --)

Subdomain: left-hand side of the SLD, even multiple < 253 chars
  - same rules as the second-level domains

Each element of a domain name separated by a `.` is called a label.

### (1)

_What is the maximum length of a subdomain?_

> 63

### (2)

_Which of the following characters cannot be used in a subdomain ( 3 b _ - )?_

> _

### (3)

_What is the maximum length of a domain name?_

> 253

### (4)

_What type of TLD is .co.uk?_

> ccTLD

## Record Types

- A: resolves to IPv4
- AAAA: resolves to IPv6
- CNAME (Canonincal Name) ~ alias: resolves to other domain name
- MX: resolves to domain's email servers (w/ priority flags)
- TXT: free text fields, e.g. verify domain ownership and anti-spam

### (1)

_What type of record would be used to advise where to send email?_

> MX

### (2)

_What type of record handles IPv6 addresses?_

> AAAA

## Making a Request

- check computer's local cache
  - TTL: how long the stored record is valid
- request to recursive DNS server
  - also has local cache
- query backbone root DNS server
- query TLD server
- query the domain's authoritative nameserver
  - update your DNS records here

### (1)

_What field specifies how long a DNS record should be cached for?_

> TTL

### (2)

_What type of DNS Server is usually provided by your ISP?_

> recursive

### (3)

_What type of server holds all the records for a domain?_

> authoritative

## Practical

Command: `nslookup --type={A,CNAME,MX,TXT} <domain name>`

### (1)

_What is the CNAME of shop.website.thm?_

> shops.myshopify.com

### (2)

_What is the value of the TXT record of website.thm?_

> THM{7012BBA60997F35A9516C2E16D2944FF}

### (3)

_What is the numerical priority value for the MX record?_

> 30

### (4)

_What is the IP address for the A record of www.website.thm?_

> 10.10.10.10
