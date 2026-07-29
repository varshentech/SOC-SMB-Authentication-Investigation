# SOC SMB Authentication Investigation

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

 
 ## 📸 Screenshots

The `Screenshots` folder contains evidence collected during the investigation, including:

- VirtualBox Lab Setup
- Windows IP Configuration
- Kali Linux IP Configuration
- Ping Connectivity Test
- Nmap Scan Results
- SMB Authentication
- Event ID 4624 (Successful Logon)
- Event ID 4625 (Failed Logon)
- Local User Configuration
- Shared Folder Configuration

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

ifconfig

ping

## Nmap

nmap 192.168.55.102

## SMB

smbclient -L //192.168.55.102 -U testuser

smbclient //192.168.55.102/soc-lab -U testuser

## Windows

net user

net user testuser

net share

## 🔍 Investigation Findings

During the investigation, Windows Security logs recorded both successful and failed SMB authentication attempts.

### Event ID 4625 – Failed Logon

- Username: testuser
- Authentication Package: NTLM
- Source IP: Kali Linux
- Result: Failed authentication

### Event ID 4624 – Successful Logon

- Username: testuser
- Authentication Package: NTLM
- Result: Successful authentication

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
