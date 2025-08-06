#  Byte Eagle CTF -  Privilege Escalation Walkthrough


 Overview

This repository contains a detailed walkthrough of the **Byte Eagle CTF Challenge**, focused on Linux enumeration, privilege escalation, and flag retrieval using SSH and system misconfigurations. The challenge involved accessing a vulnerable Ubuntu machine, discovering credentials, escalating privileges, and capturing flags.



### Target Information

- **Machine IP**: `192.168.96.139`
- **OS**: Ubuntu 14.04.6 LTS
- **Challenge Type**: SSH & Privilege Escalation
- **Users**: `wavex` → `aveng` → `root`

---

### Tools Used

- `nmap`
- `smbclient`
- `base64`
- `ssh`
- `find`, `cat`, `su`, `sudo`

---

### Step-by-Step Walkthrough

### Step 1: Reconnaissance with Nmap


nmap 192.168.96.139 -sV -sC


Discovered open ports:
- 22 (SSH)
- 80 (HTTP)
- 139/445 (SMB)

---

### Step 2: Enumerate SMB Shares

smbclient -L 192.168.96.139 -N
smbclient //192.168.96.139/wave -N
get FLAG1.txt
get message_from_aveng.txt
```

---

### Step 3: Decode FLAG1


echo "<base64-string>" | base64 -d


Decoded credentials:
- `user: wavex`
- `password: door+open`
- `FLAG1`: `Flag1{Welcome_T0_THE-W3ST-W1LD-B0rder}`

---

### 🔗 Step 4: SSH into Target


ssh wavex@192.168.96.139


- Logged into the machine.
- Verified user with `whoami` → `wavex`

---

###  Step 5: Find Writable Directories


find / -writable -type d 2>/dev/null


Found:
```
/usr/share/av/westsidesecret
```

Inside:
```
ififoregt.sh
```

---

### 🧾 Step 6: Read Script and Get New Credentials


cat ififoregt.sh


Revealed:
- `user: aveng`
- `password: kaizen+80`

---

###  Step 7: Switch User & Gain Root Access


su aveng
sudo su


- Switched to `aveng`
- Gained root using same password: `kaizen+80`

---

###  Step 8: Navigate to Root Directory & Retrieve Final Flag


cd /root
cat FLAG2.txt


Output:
```
FLAG2 { WELCOME TO 67 84 70 }
```

ASCII Translation:
- 67 → C
- 84 → T
- 70 → F

Final Flag: `WELCOME TO CTF`

---

##  Conclusion

The Byte Eagle CTF demonstrated practical experience in:

- Network Reconnaissance (Nmap, SMB)
- Base64 decoding and credential extraction
- Linux privilege escalation
- Post-exploitation and flag retrieval

> Successfully rooted the machine and captured both flags. Great learning experience!

---


##  About Me

I'm **Tejas Kottarshettar**, an aspiring cybersecurity professional with interests in:
- Web Application Penetration Testing
- Red Team Operations
- CTFs & Offensive Security

 Let's connect:
- [LinkedIn](www.linkedin.com/in/tejas-kottar-shettar-35522722b)




