TryHackMe
=========

Go to https://tryhackme.com/access and download the config file.

* Connect to THM OpenVPN: `sudo openvpn --daemon --config *.ovpn`
* Disconnect from THM OpenVPN: `ps aux | grep openvpn; sudo pkill -I openvpn`

Each directory in this repository refers to `https://tryhackme.com/room/{dirname}`.
