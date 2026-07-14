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
| Goal | Build and prepare a dedicated Ubuntu Server for Splunk Enterprise |

### Short Introduction

This lab documents the preparation of a dedicated Ubuntu Server for a future Splunk Enterprise deployment.

The objective was to build a clean server environment by creating a new virtual machine, installing Ubuntu Server, configuring networking, enabling secure remote administration with OpenSSH, and verifying SSH connectivity before installing Splunk Enterprise.

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

Created a new Generation 2 virtual machine with the following configuration:

- VM Name: `Splunk-Server`
- Memory: 8192 MB
- Virtual Processors: 4
- Virtual Disk: 100 GB
- Network: My External Lab
- Installation Media: Ubuntu Server 24.04.4 LTS ISO

Configured Secure Boot to use:

`Microsoft UEFI Certificate Authority`

### 2. Installed Ubuntu Server

Selected the following installation options:

- Standard Ubuntu Server installation
- Use Entire Disk
- LVM Disabled
- Disk Encryption Disabled
- Skip Ubuntu Pro
- No Third-party Drivers
- No Featured Server Snaps
- Install OpenSSH Server
- Enable Password Authentication over SSH

Configured:

- Server Name: `splunk-server`
- Username: `saeid`

### 3. Updated the Package Repository

```bash
sudo apt update
```

### 4. Verified the Server IP Address

Checked the local hostname address:

```bash
hostname -i
```

Output:

```text
127.0.1.1
```

Checked the assigned network interface addresses:

```bash
hostname -I
```

Output:

```text
192.168.1.121
```

### 5. Tested Network Connectivity

From Windows PowerShell:

```powershell
ping 192.168.1.121
```

Verified successful network communication.

### 6. Verified the OpenSSH Package

```bash
sudo apt install openssh-server -y
```

Confirmed that OpenSSH Server was already installed.

### 7. Checked the SSH Service

```bash
sudo systemctl status ssh
```

Initial status:

```text
inactive (dead)
```

### 8. Enabled SSH at Startup

```bash
sudo systemctl enable ssh
```

### 9. Started the SSH Service

```bash
sudo systemctl start ssh
```

### 10. Verified the SSH Service

```bash
sudo systemctl status ssh
```

Output:

```text
active (running)
```

### 11. Verified That SSH Was Listening on TCP Port 22

```bash
sudo ss -tlnp | grep :22
```

Output:

```text
0.0.0.0:22
[::]:22
```

Confirmed that SSH was listening on both IPv4 and IPv6 interfaces.

### 12. Tested TCP Port 22 from Windows

From Windows PowerShell:

```powershell
Test-NetConnection 192.168.1.121 -Port 22
```

Output:

```text
TcpTestSucceeded : True
```

### 13. Connected to Ubuntu via SSH

From Windows PowerShell:

```powershell
ssh saeid@192.168.1.121
```

Verified successful remote administration.

### 14. Completed Server Preparation

Verified that the Ubuntu Server was fully prepared for the upcoming Splunk Enterprise installation.

## Key Takeaways

- Built a dedicated Ubuntu Server virtual machine for Splunk.
- Configured Hyper-V networking and Secure Boot.
- Learned the difference between `hostname -i` and `hostname -I`.
- Configured and validated OpenSSH for secure remote administration.
- Verified SSH service availability and TCP port 22 connectivity.
- Prepared the server for the Splunk Enterprise installation.

## Navigation

**Previous Lab**

N/A

**Next Lab**

**Part 02 - Splunk Enterprise Installation**
