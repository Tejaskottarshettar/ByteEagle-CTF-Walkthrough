# ByteEagle-CTF-Walkthrough
Walkthrough for the Byte Eagle CTF challenge from VulnHub
# ByteEagle-CTF-Walkthrough

This repository contains a detailed walkthrough of the Byte Eagle CTF challenge from VulnHub. The challenge involves penetrating an Ubuntu 14.04.6 LTS system at 192.168.96.139 to retrieve two flags using reconnaissance, SSH access, and privilege escalation techniques.

## Walkthrough
- **Reconnaissance**: Used Nmap and SMBclient to identify open ports and extract files.
- **Credential Extraction**: Decoded base64 data and leveraged a script to obtain `wavex`/`door+open` credentials.
- **SSH Access**: Gained shell access and explored writable directories with `find / -writable -type d 2> /dev/null`.
- **Privilege Escalation**: Escalated to root with `sudo su` to retrieve FLAG2.txt.
- **Flags**: Successfully obtained FLAG1 and FLAG2.

Check out the full walkthrough [here](walkthrough.md).

## Skills Demonstrated
- Penetration testing
- Linux system enumeration
- Privilege escalation
- Credential analysis

## Contact
Looking for opportunities in cybersecurity! Connect with me on [LinkedIn](https://www.linkedin.com/in/tejas-kottar-shettar-35522722b) or explore my other projects.

