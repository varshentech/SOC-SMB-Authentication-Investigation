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
