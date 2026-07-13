# Part 01 - Splunk Enterprise Installation on Ubuntu Server

## Overview

### Summary Table

| Item | Details |
|------|---------|
| Project | Splunk Enterprise Installation |
| Platform | Hyper-V |
| Operating System | Ubuntu Server 24.04.4 LTS |
| SIEM | Splunk Enterprise 10.0.2 |
| Goal | Deploy Splunk Enterprise on Ubuntu Server and verify a successful installation and web interface access. |

### Short Introduction

This lab documents the deployment of a dedicated Splunk Enterprise server on Ubuntu Server 24.04.4 LTS running in Hyper-V. The objective was to prepare a clean SIEM environment by installing Splunk Enterprise, configuring secure remote access with OpenSSH, transferring the installation package from Windows using SCP, completing the initial Splunk setup, and verifying successful access to the Splunk Web interface.

---

## Lab Environment

### VMs

- Splunk Server

### Operating Systems

- Ubuntu Server 24.04.4 LTS
- Windows 11 (Host)

### Monitoring Tools

- OpenSSH Server
- Secure Copy Protocol (SCP)

### SIEM

- Splunk Enterprise 10.0.2

---

## Investigation Steps

1. Created a dedicated Ubuntu Server virtual machine in Hyper-V.
2. Installed Ubuntu Server 24.04.4 LTS.
3. Updated the operating system packages.
4. Verified network connectivity.
5. Installed and verified the OpenSSH Server service.
6. Confirmed SSH was listening on TCP port 22.
7. Verified SSH connectivity from the Windows host.
8. Transferred the Splunk Enterprise installation package using SCP.
9. Installed Splunk Enterprise using the Debian package.
10. Started Splunk Enterprise for the first time.
11. Accepted the Splunk Enterprise license agreement.
12. Created the initial administrator account.
13. Verified successful access to the Splunk Web interface.

---

## Detection & Analysis

No security detections were generated during this lab because the objective was infrastructure deployment rather than security monitoring.

---

## MITRE ATT&CK Mapping

**N/A**

No MITRE ATT&CK techniques were simulated or observed during this installation lab.

---

## Key Takeaways

- Successfully deployed Splunk Enterprise on Ubuntu Server.
- Configured secure remote administration using OpenSSH and SCP.
- Verified that Splunk services initialized correctly.
- Confirmed successful access to the Splunk Web interface.
- Established the foundation for future Splunk detection and log analysis labs.

---

## Navigation

**Previous Lab**

N/A

**Next Lab**

Splunk Data Onboarding and First Search
