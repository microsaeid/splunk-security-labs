# Part 01 - Ubuntu Server Preparation for Splunk

## Overview

### Summary Table

| Item | Details |
|------|---------|
| Project | Ubuntu Server Preparation for Splunk |
| Platform | Microsoft Hyper-V |
| Server | Splunk Server VM |
| Operating System | Ubuntu Server 24.04.4 LTS |
| Network | External Virtual Switch |
| Remote Access | OpenSSH |
| Goal | Prepare an Ubuntu Server for a Splunk Enterprise deployment |

### Short Introduction

This lab documents the preparation of a dedicated Ubuntu Server virtual machine before installing Splunk Enterprise.

## Lab Environment

### VMs

- Splunk Server

### Operating Systems

- Ubuntu Server 24.04.4 LTS
- Windows 11 Host

### Virtualization

- Microsoft Hyper-V
- Generation 2 Virtual Machine
- My External Lab Virtual Switch

### Server Resources

| Resource | Configuration |
|----------|---------------|
| Memory | 8 GB |
| Processors | 4 vCPU |
| Virtual Disk | 100 GB Dynamically Expanding VHDX |
| Network | External Virtual Switch |
| Secure Boot | Microsoft UEFI Certificate Authority |

## Investigation Steps

### 1. Created the Virtual Machine

- VM Name: `Splunk-Server`
- Generation: 2
- Memory: 8192 MB
- Processors: 4
- Virtual Disk: 100 GB
- Network: My External Lab
- Installation Media: Ubuntu Server 24.04.4 LTS ISO
- Secure Boot: Microsoft UEFI Certificate Authority

### 2. Installed Ubuntu Server

Installation options:

- Standard Ubuntu Server
- Entire Disk
- LVM Disabled
- Disk Encryption Disabled
- Ubuntu Pro Skipped
- Third-party Drivers Disabled
- Featured Server Snaps Disabled
- OpenSSH Server Installed
- Password Authentication Enabled

Server configuration:

- Hostname: `splunk-server`
- Username: `saeid`

### 3. Updated the Package Repository

```bash
sudo apt update
```

### 4. Checked the Server IP Address

```bash
hostname -i
```

Output

```text
127.0.1.1
```

```bash
hostname -I
```

Output

```text
192.168.1.121
```

### 5. Tested Network Connectivity

```powershell
ping 192.168.1.121
```

### 6. Checked the OpenSSH Package

```bash
sudo apt install openssh-server -y
```

### 7. Checked the SSH Service

```bash
sudo systemctl status ssh
```

Output

```text
inactive (dead)
```

### 8. Enabled the SSH Service

```bash
sudo systemctl enable ssh
```

### 9. Started the SSH Service

```bash
sudo systemctl start ssh
```

### 10. Checked the SSH Service

```bash
sudo systemctl status ssh
```

Output

```text
active (running)
```

### 11. Checked TCP Port 22

```bash
sudo ss -tlnp | grep :22
```

Output

```text
0.0.0.0:22
[::]:22
```

### 12. Tested TCP Port 22

```powershell
Test-NetConnection 192.168.1.121 -Port 22
```

Output

```text
TcpTestSucceeded : True
```

### 13. Connected to the Ubuntu Server

```powershell
ssh saeid@192.168.1.121
```

## Key Takeaways

- Created a dedicated Ubuntu Server virtual machine for the Splunk lab.
- Configured networking and OpenSSH for remote administration.
- Verified SSH service status and TCP port 22 availability.
- Confirmed remote SSH access from the Windows host.
- Completed the Ubuntu Server preparation before installing Splunk Enterprise.

## Navigation

➡️ Next Lab: [Part 02 - Splunk Enterprise Installation](../Part 02 - Splunk Enterprise Installation)
