Introductory Networking
=======================

An introduction to networking theory and basic networking tools.

## 1. Introduction

### (1)

_Let's get started!_

> N/A

## 2. OSI Model

- Open Systems Interconnection.
- 7 layers: APSTNDP
- Transmission Control Protocol = segments.
- User Datagram Protocol = datagrams.
- Network = logical (IP), Data link = physical (MAC).
  - MAC: Media Access Control.

### (1)

_Which layer would choose to send data over TCP or UDP?_

> 4

### (2)

_Which layer checks received packets to make sure that they haven't been corrupted?_

> 2

### (3)

_In which layer would data be formatted in preparation for transmission?_

> 2

### (4)

_Which layer transmits and receives data?_

> 1

### (5)

_Which layer encrypts, compresses, or otherwise transforms the
initial data to give it a standardised format?_

> 6

### (6)

_Which layer tracks communications between the host and receiving computers?_

> 5

### (7)

_Which layer accepts communication requests from applications?_

> 7

### (8)

_Which layer handles logical addressing?_

> 3

### (9)

_When sending data over TCP, what would you call the "bite-sized" pieces of data?_

> segments

### (10)

_[Research] Which layer would the FTP protocol communicate with?_

> 7

### (11)

_Which transport layer protocol would be best suited to transmit a live video?_

> UDP

## 3. Encapsulation

- Headers and trailers (layer 2) added to the payload.
- Bits > Frames > Packets > Segments / Datagrams > Data > Data > Data

### (1)

_How would you refer to data at layer 2 of the encapsulation process (with the OSI model)?_

> frames

### (2)

_How would you refer to data at layer 4 of the encapsulation process
(with the OSI model), if the UDP protocol has been selected?_

> datagrams

### (3)

_What process would a computer perform on a received message?_

> de-encapsulation

### (4)

_Which is the only layer of the OSI model to add a trailer during encapsulation?_

> data link

### (5)

_Does encapsulation provide an extra layer of security (Aye/Nay)?_

> aye

## 4. TCP/IP Model

- Older than OSI.
- 4/5 layers: ATIN / ATIDP
  - Application = Application + Presentation + Session
  - Internet = Network
  - Network Interface = Data link + Physical
- Three-way handshake: SYN > SYN/ACK > ACK.

### (1)

_Which model was introduced first, OSI or TCP/IP?_

> TCP/IP

### (2)

_Which layer of the TCP/IP model covers the functionality of the
Transport layer of the OSI model (Full Name)?_

> Transport

### (3)

_Which layer of the TCP/IP model covers the functionality of the
Session layer of the OSI model (Full Name)?_

> Application

### (4)

_The Network Interface layer of the TCP/IP model covers the functionality of two
layers in the OSI model. These layers are Data Link, and?.. (Full Name)?_

> Physical

### (5)

_Which layer of the TCP/IP model handles the functionality of the OSI network layer?_

> Internet

### (6)

_What kind of protocol is TCP?_

> connection-based

### (7)

_What is SYN short for?_

> synchronise

### (8)

_What is the second step of the three way handshake?_

> SYN/ACK

### (9)

_What is the short name for the "Acknowledgement" segment in the three-way handshake?_

> ACK

## 5. Ping

- ICMP: Internet layer protocol.
- `ping <target>`
  - `-4`/`-6` forces IPv4/IPv6.

### (1)

_What command would you use to ping the bbc.co.uk website?_

> ping bbc.co.uk

### (2)

_Ping muirlandoracle.co.uk. What is the IPv4 address?_

> 217.160.0.152

### (3)

_What switch lets you change the interval of sent ping requests?_

> -i

### (4)

_What switch would allow you to restrict requests to IPv4?_

> -4

### (5)

_What switch would give you a more verbose output?_

> -v

## 6. Traceroute

- ICMP / UDP.
- `traceroute <destination>`

### (1)

_Use traceroute on tryhackme.com. Can you see the path your request has taken?_

> N/A

### (2)

_What switch would you use to specify an interface when using Traceroute?_

> -i

### (3)

_What switch would you use if you wanted to use TCP SYN requests when tracing the route?_

> -T

### (4)

_[Lateral Thinking] Which layer of the TCP/IP model will traceroute run on by default (Windows)?_

> Internet

## 7. WHOIS

- Domain Names, Domain Registrars.
- `whois <domain>`

### (1)

_Perform a whois search on facebook.com_

>N/A

### (2)

__What is the registrant postal code for facebook.com?

> 94025

### (3)

_When was the facebook.com domain first registered (Format: DD/MM/YYYY)?_

> 29/03/1997

### (4)

_Perform a whois search on microsoft.com_

> N/A

### (5)

_Which city is the registrant based in?_

> Redmond

### (6)

_[OSINT] What is the name of the golf course that is near the registrant address for microsoft.com?_

Google Maps: `golf club near One Microsoft Way`

> Bellevue Golf Course

### (7)

_What is the registered Tech Email for microsoft.com?_

> msnhst@microsoft.com

## 8. Dig

- DNS: Domain Name System
  1. Computer: local cache until TTL (Time To Live) seconds.
  2. Router.
  3. Recursive DNS server.
  4. Authoritative name server (record).
  5. Top-Level Domain (TLD) server: .com, .co.uk.
  6. Root name server (13).
- ISP: Internet Service Provider.
- `dig <domain> @<dns-server-ip>`

### (1)

_What is DNS short for?_

> Domain Name System

### (2)

_What is the first type of DNS server your computer would query when you search for a domain?_

> Recursive

### (3)

_What type of DNS server contains records specific to domain extensions
(i.e. .com, .co.uk*, etc)*? Use the long version of the name._

> Top-Level Domain

### (4)

_Where is the very first place your computer would look to find the IP address of a domain?_

> local cache

### (5)

_[Research] Google runs two public DNS servers. One of them can be queried with
the IP 8.8.8.8, what is the IP address of the other one?_

> 8.8.4.4

### (6)

_If a DNS query has a TTL of 24 hours, what number would the dig query show?_

> 86400

## 9. Further Reading

Cisco Self Study Guide by Steve McQuerry

### (1)

_Read the final thoughts_

> N/A
