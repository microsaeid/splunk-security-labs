# Part 02 - Splunk Enterprise Installation

## Overview

### Summary Table

| Item | Details |
|------|---------|
| Project | Splunk Enterprise Installation |
| Platform | Microsoft Hyper-V |
| Operating System | Ubuntu Server 24.04.4 LTS |
| SIEM | Splunk Enterprise 10.0.2 |
| Installation Package | Debian (.deb) |
| Goal | Install and initialize Splunk Enterprise on Ubuntu Server |

### Short Introduction

This lab documents the installation and initial configuration of Splunk Enterprise on a dedicated Ubuntu Server.

The installation package was securely transferred from the Windows host using SCP. Splunk Enterprise was then installed, initialized, configured with the first administrator account, and verified through the Splunk Web interface.

## Lab Environment

### VMs

- Splunk Server

### Operating Systems

- Ubuntu Server 24.04.4 LTS
- Windows 11 Host

### SIEM

- Splunk Enterprise 10.0.2 (All-in-One Instance)

## Investigation Steps

### 1. Connected to the Ubuntu Server

From Windows PowerShell:

```powershell
ssh saeid@192.168.1.121
```

Verified remote access before beginning the installation.

### 2. Transferred the Splunk Enterprise Package

```powershell
scp "D:\Windows Files\Downloads\Programs\Splunk\splunk-10.0.2-e2d18b4767e9-linux-amd64.deb" saeid@192.168.1.121:/home/saeid/
```

Successfully copied the installation package to the Ubuntu Server.

### 3. Verified the Transferred Package

```bash
ls -lh /home/saeid/splunk-10.0.2-e2d18b4767e9-linux-amd64.deb
```

Verified that the installation package was available before starting the installation.

### 4. Installed Splunk Enterprise

```bash
sudo dpkg -i /home/saeid/splunk-10.0.2-e2d18b4767e9-linux-amd64.deb
```

Successfully installed Splunk Enterprise.

### 5. Verified the Installed Package

```bash
dpkg -l | grep splunk
```

Confirmed that Splunk Enterprise 10.0.2 was installed.

### 6. Verified the Installation Directory

```bash
ls -ld /opt/splunk
```

Confirmed that the installation directory was created successfully.

### 7. Initialized Splunk Enterprise

```bash
sudo /opt/splunk/bin/splunk start --accept-license
```

Completed the initial setup by:

- Accepting the license agreement
- Creating the administrator account
- Initializing Splunk services
- Creating default certificates
- Creating default indexes

### 8. Verified Splunk Web

Opened the Splunk Web interface.

```text
http://192.168.1.121:8000
```

Successfully authenticated using the administrator account.

## Key Takeaways

- Successfully installed Splunk Enterprise on Ubuntu Server.
- Initialized the Splunk platform for first-time use.
- Created the initial administrator account.
- Verified successful access to the Splunk Web interface.
- Prepared the SIEM platform for future data onboarding and log analysis.

## Navigation

⬅️ Previous Lab: [Part 01 - Ubuntu Server Preparation for Splunk](https://github.com/microsaeid/splunk-security-labs/tree/main/Part%2001%20-%20Ubuntu%20Server%20Preparation%20for%20Splunk)

➡️ Next Lab: [Part 03-01 - Windows 10 Universal Forwarder Installation](https://github.com/microsaeid/splunk-security-labs/tree/main/Part%2003-01%20-%20Windows%2010%20Universal%20Forwarder%20Installation)
 

