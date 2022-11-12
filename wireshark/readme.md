Wireshark 101
=============

Learn the basics of Wireshark and how to analyze various protocols and PCAPs.

## 1. Introduction

PCAP: network packet capture file.

### (1)

__

> N/A

## 2. Installation

### (1)

__

* `sudo pacman -Sy wireshark-qt wireshark-cli`

> N/A

## 3. Wireshark Overview

### (1)

__

> N/A

## 4. Collection Methods

- Network tap: intercept (vampire) / inline (Throwing Star LAN).
- MAC flood: fill CAM table and force the switch to broadcast mode.
- ARP poisoning: redirect traffic to your station.
- Port mirroring?

### (1)

__

> N/A

## 5. Filtering Captures

- Capture filter <-> display filter.
- `&& || == != > <`
- `ip.addr` = `ip.src` or `ip.dst`
- `tcp`, `udp`, `tcp.port`, `udp.port`
- `sudo tshark -i wlo1 -w test.pcap`
- `wireshark -r test.pcap`

### (1)

__

> N/A

## 6. Packet Dissection

### (1)

__

> N/A

## 7. ARP Traffic

- Address Resolution Protocol
- Layer 2: IP -> MAC resolution.
- Request (1) / Response (2) opcode.
- View > Name Resolution > Resolve Physical Addresses
  - Look out for untrusted / unidentified requests (responses?)

### (1)

__

> request (1)

### (2)

__

> 80:fb:06:f0:45:d7

### (3)

__

`arp.opcode == 2`

> 76,400,459,520

### (4)

__

- Check `arp.dst.hw_mac` and `arp.src.hw_mac`
- Who has IP: `(arp.dst.proto_ipv4 == IP) && (arp.opcode==1)`
- Tell IP: `(arp.src.proto_ipv4 == IP) && (arp.opcode==1)`

> 10.251.23.1

## 8. ICMP Traffic

- Internet Control Message Protocol (RFC792)
- Ping (echo): request (8) / reply (0).
- Check for anomalous opcodes.
- Can contain 48 bytes of "random" data: exfiltration?
- `.pcap` vs `.pcapng` vs `.cap`?

### (1)

__

Filter: `icmp`

> 8

### (2)

__

> 0

### (3)

__

> May 30, 2013

### (4)

__

right click > copy > value

> 08090a0b0c0d0e0f101112131415161718191a1b1c1d1e1f
  202122232425262728292a2b2c2d2e2f3031323334353637

## 9. TCP Traffic

- Transmission Control Protocol (RFC793)
- Other tools: RSA NetWitness, NetworkMiner.
- Check RST packets in TCP handshakes (nmap).
- ACK number = 0 (& RST?): port is not open.
- Uncheck "relative sequence numbers" option?

### (1)

__

> N/A

## 10. DNS Traffic

- Domain Name Service protocol (RFC1035)
- Usually over UDP, although: DNS over HTTPS?

### (1)

__

Filter: `dns`

> 8.8.8.8.in-addr.arpa

### (2)

__

> www.wireshark.org

### (3)

__

> 0x2c58

## 11. HTTP Traffic

- HyperText Transfer Protocol (RFC2616)
- Statistics > Protocol Hierarchy.
- File > Export Objects > HTTP.
- Statistics > Endpoints.

### (1)

__

> 4.7

### (2)

__

> 145.254.160.237

### (3)

__

> Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.6) Gecko/20040113

### (4)

__

> http://pagead2.googlesyndication.com/pagead/ads?client=ca-pub-23091919486736
  29&random=1084443430285&lmt=1082467020&format=468x60_as&output=html&url=http
  %3A%2F%2Fwww.ethereal.com%2Fdownload.html&color_bg=FFFFFF&color_text=333333&
  color_link=000000&color_url=666633&color_border=666633
  
### (5)

__

> www.ethereal.com

### (6)

__

> http://www.ethereal.com/download.html

## 12. HTTPS Traffic

- HTTP Secure
- Secure tunnel establishment: protocol, algorithm, authentication.
- Client Hello, Server Hello, Client Key Exchange.
- Decrypt traffic only with the secret key.

### (1)

__

- Import RSA key:
  - Edit > Preferences > Protocols > TLS > [+]
  - IP, Port, Protocol = HTTP, Keyfile

> https://localhost/icons/apache_pb.png

### (2)

__

> https://localhost/icons/back.gif

### (3)

__

> Mozilla/5.0 (X11; U; Linux i686; fr; rv:1.8.0.2) Gecko/20060308 Firefox/1.5.0.2

## 13. Analyzing Exploit PCAPs

Active Directory exploit: Zerologon + SMB Secretsdump.

### (1)

__

> N/A

## 14. Conclusion

- https://wiki.wireshark.org/SampleCaptures
- https://dfirmadness.com/case-001-pcap-analysis/

### (1)

__

> N/A
