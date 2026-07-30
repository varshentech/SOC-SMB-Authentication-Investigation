## 📌 Project Overview

This project demonstrates a Security Operations Center (SOC) authentication investigation by creating a small Windows and Kali Linux lab using Oracle VirtualBox.

The objective was to simulate SMB authentication attempts from a Kali Linux machine to a Windows 10 host, generate both successful and failed login events, and investigate the generated Windows Security logs using Event Viewer.

Throughout the project, network connectivity was verified, SMB shares were configured, authentication events were generated, and Windows Event IDs 4624 (Successful Logon) and 4625 (Failed Logon) were analyzed to understand how authentication activities are recorded in Windows.

This project demonstrates fundamental SOC analyst skills including Windows administration, networking, SMB authentication, log analysis, and security event investigation.

## 🎯 Objectives

- Build a two-machine SOC lab using Oracle VirtualBox.
- Configure communication between Kali Linux and Windows 10 using a Host-Only network.
- Perform network reconnaissance using Nmap.
- Configure an SMB shared folder on Windows.
- Generate successful and failed SMB authentication attempts.
- Investigate Windows Security Event IDs 4624 and 4625 using Event Viewer.
- Understand how authentication events are recorded and analyzed in a SOC environment.

## 🏗️ Lab Architecture

```text
Host Machine (Windows)
        │
        ▼
Oracle VirtualBox
        │
 ┌──────────────┴──────────────┐
 │                             │
 ▼                             ▼
Kali Linux               Windows 10
192.168.55.101           192.168.55.102
        │
        │ SMB Authentication
        ▼
Windows Shared Folder (SOC-Lab)
        │
        ▼
Windows Security Logs
        │
 ├── Event ID 4624 (Successful Logon)
 └── Event ID 4625 (Failed Logon)
```
<img width="960" height="540" alt="virtualbox lab setup" src="https://github.com/user-attachments/assets/0e38702a-f735-4baf-b456-45fbf6508b17" />


## 🛠️ Tools Used

- Oracle VirtualBox
- Kali Linux
- Windows 10
- Nmap
- SMBClient
- Windows Event Viewer
- Command Prompt (CMD)
- ipconfig
- ifconfig / ip addr
- ping

## 🔄 Project Workflow

1. Created two virtual machines (Windows 10 and Kali Linux) using Oracle VirtualBox.
2. Configured both machines to use a Host-Only network.
3. Verified network connectivity using `ping`.
4. Identified the target system's open ports using Nmap.
5. Configured an SMB shared folder on Windows.
6. Created a local Windows user (`testuser`) for authentication testing.
7. Connected to the Windows SMB share from Kali using `smbclient`.
8. Generated both successful and failed login attempts.
9. Investigated Windows Security Event IDs 4624 and 4625 using Event Viewer.
10. Documented findings and collected screenshots as evidence.

# Commands Used

## Network

ipconfig

<img width="721" height="362" alt="Screenshot 2026-07-30 094841" src="https://github.com/user-attachments/assets/893c979c-e032-4597-94fa-51576b4077e6" />


ifconfig


<img width="628" height="308" alt="ip of kali" src="https://github.com/user-attachments/assets/cdb74493-5f5e-47d1-b2ec-8f0922c4251c" />


ping

<img width="510" height="358" alt="ping cmd" src="https://github.com/user-attachments/assets/5b59d94a-e1d2-4552-99da-d00fa9a58999" />


## Nmap

nmap 192.168.55.102

<img width="497" height="236" alt="nmap scan" src="https://github.com/user-attachments/assets/3366b7c6-68b6-44a0-ad43-3eef94c42b69" />



## SMB

smbclient -L //192.168.55.102 -U testuser

smbclient //192.168.55.102/soc-lab -U testuser

<img width="389" height="77" alt="smb connection" src="https://github.com/user-attachments/assets/410f4b95-72ef-43b6-b298-24a42348164c" />

<img width="389" height="90" alt="smb connection success" src="https://github.com/user-attachments/assets/f3466de8-7117-4447-a39f-6e2160278c58" />


## Windows

net user testuser password@123 /add

<img width="355" height="24" alt="testuser creation" src="https://github.com/user-attachments/assets/9795b077-2509-4df6-9fc6-783b4f0abae8" />

net user 

<img width="486" height="133" alt="net user" src="https://github.com/user-attachments/assets/cb97c213-91ad-455a-b1db-d6c8a575f34c" />

net share

<img width="719" height="353" alt="Screenshot 2026-07-30 095350" src="https://github.com/user-attachments/assets/670fa0a2-0ee7-4349-ad4c-018f6a330a7c" />


## 🔍 Investigation Findings

During the investigation, Windows Security logs recorded both successful and failed SMB authentication attempts.

### Event ID 4625 – Failed Logon

- Username: testuser
- Authentication Package: NTLM
- Source IP: Kali Linux
- Result: Failed authentication

<img width="463" height="51" alt="logs captured" src="https://github.com/user-attachments/assets/cef33286-79aa-4b9b-8284-983b15eecc90" />

<img width="459" height="332" alt="id 4625 testuser" src="https://github.com/user-attachments/assets/d39329db-8d90-48a6-8909-d566ad468571" />



### Event ID 4624 – Successful Logon

- Username: testuser
- Authentication Package: NTLM
- Result: Successful authentication

<img width="463" height="51" alt="logs captured" src="https://github.com/user-attachments/assets/cef33286-79aa-4b9b-8284-983b15eecc90" />

<img width="472" height="330" alt="id 4624 testuser" src="https://github.com/user-attachments/assets/effbc40f-40af-4e42-9181-6c76576983c1" />


## 💡 Skills Demonstrated

- Virtualization using Oracle VirtualBox
- Windows Administration
- Linux Basics
- Network Configuration
- Nmap Enumeration
- SMB Authentication
- Windows Event Log Analysis
- Security Event Investigation

## 🚀 Future Improvements

- Integrate Microsoft Sentinel or Splunk for centralized log analysis.
- Simulate brute-force authentication attacks.
- Create custom detection rules.
- Automate log collection using PowerShell.


## ✅ Conclusion

This project successfully demonstrated SMB authentication monitoring in a controlled SOC lab environment. By generating both successful and failed authentication attempts and analyzing Windows Security Event IDs 4624 and 4625, the project provided practical experience with Windows log analysis, SMB authentication, network reconnaissance, and basic SOC investigation techniques.
