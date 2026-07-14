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
| File Transfer | Secure Copy Protocol (SCP) |
| Goal | Build and prepare a dedicated Ubuntu Server for Splunk Enterprise |

### Short Introduction

This lab documents the creation and preparation of a dedicated Ubuntu Server virtual machine for a Splunk Enterprise deployment.

The work included creating the virtual machine in Hyper-V, installing Ubuntu Server, configuring network connectivity, enabling secure remote access with SSH, troubleshooting TCP port 22 connectivity, and transferring the Splunk Enterprise installation package from the Windows host to the Linux server.

Splunk Enterprise was not installed during this part. The objective was to prepare and verify the underlying server environment before beginning the Splunk installation.

---

## Lab Environment

### VMs

- Splunk Server

### Operating Systems

- Ubuntu Server 24.04.4 LTS
- Windows 11 Host

### Virtualization

- Microsoft Hyper-V
- Generation 2 virtual machine
- My External Lab virtual switch

### Server Resources

| Resource | Configuration |
|----------|---------------|
| Memory | 8 GB |
| Processors | 4 vCPU |
| Virtual Disk | 100 GB dynamically expanding VHDX |
| Network | External virtual switch |
| Secure Boot | Microsoft UEFI Certificate Authority |

### Monitoring Tools

- None configured during this part

### SIEM

- Not installed during this part

---

## Investigation Steps

### 1. Created the Virtual Machine

Created a new Generation 2 virtual machine in Hyper-V with the following configuration:

- VM name: `Splunk-Server`
- Memory: 8192 MB
- Virtual processors: 4
- Virtual disk: 100 GB
- Network: My External Lab
- Installation media: Ubuntu Server 24.04.4 LTS ISO

Configured Secure Boot to use:

`Microsoft UEFI Certificate Authority`

### 2. Installed Ubuntu Server

Installed Ubuntu Server with the following selections:

- Standard Ubuntu Server installation
- Entire virtual disk used
- LVM disabled
- Disk encryption disabled
- Ubuntu Pro skipped
- Third-party drivers not selected
- Featured server snaps not installed
- OpenSSH Server selected
- Password authentication over SSH enabled

Configured the server identity:

- Server name: `splunk-server`
- Local user: `saeid`

### 3. Updated the Ubuntu Package List
