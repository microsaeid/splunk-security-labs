# Part 03-01 - Windows 10 Universal Forwarder Installation

## Overview

### Summary Table

| Item | Details |
|------|---------|
| Project | Windows 10 Universal Forwarder Installation |
| Operating System | Windows 10 |
| Forwarder Version | Splunk Universal Forwarder 10.0.2 |
| Architecture | 64-bit |
| Service Account | Local System |
| Splunk Server | Ubuntu Server 24.04.4 LTS |
| Splunk Server IP | 192.168.1.121 |
| Receiving Port | TCP 9997 |
| Selected Windows Logs | Application, Security, System |
| Goal | Install and configure Splunk Universal Forwarder on Windows 10 |

---

## Lab Environment

### Virtual Machines

- Windows 10
- Ubuntu Server 24.04.4 LTS

### Installed Components

- Splunk Enterprise
- Splunk Universal Forwarder 10.0.2

---

## Installation Steps

### 1. Download the Universal Forwarder

Downloaded the 64-bit Windows MSI installer.

```text
splunkforwarder-10.0.2-windows-x64.msi
```

![Universal Forwarder Installer](images/01-universal-forwarder-installer-file.png)

---

### 2. Start the Installer

Accepted the license agreement and selected:

- On-premises Splunk Enterprise

![Universal Forwarder Setup](images/02-universal-forwarder-setup-start.png)

---

### 3. Installation Directory

Kept the default installation directory.

```text
C:\Program Files\SplunkUniversalForwarder
```

No custom SSL certificate was configured.

---

### 4. Service Account

Configured the Universal Forwarder service to run as:

- Local System

This allows the forwarder to access local Windows Event Logs.

---

### 5. Windows Event Log Selection

Selected the following Event Logs:

- Application
- Security
- System

The following options were not enabled:

- Forwarded Events
- Setup Log
- Performance Monitor
- Active Directory Monitoring

![Windows Event Log Selection](images/03-windows-event-logs-selected.png)

---

### 6. Administrator Account

Created a local administrator account for the Universal Forwarder.

```text
Username: admin
```

The password was not stored in this repository.

![Forwarder Administrator Account](images/04-forwarder-admin-account.png)

---

### 7. Deployment Server

No Deployment Server was configured for this lab.

---

### 8. Enable Receiving on Splunk Enterprise

Configured Splunk Enterprise to receive forwarded events on TCP port 9997.

Enable receiving:

```bash
sudo /opt/splunk/bin/splunk enable listen 9997
```

Verify the listening port:

```bash
sudo /opt/splunk/bin/splunk display listen
```

Expected output:

```text
Receiving is enabled on port 9997.
```

![Receiving Port Enabled](images/05-splunk-receiving-port-enabled.png)

---

### 9. Receiving Indexer Configuration

Configured the Universal Forwarder to send data to the Splunk server.

```text
Server IP : 192.168.1.121
Port      : 9997
```

![Receiving Indexer Configuration](images/06-receiving-indexer-settings.png)

---

### 10. Complete the Installation

Completed the installation successfully.

![Installation Completed](images/07-universal-forwarder-installation-completed.png)

---

## Verification

Verified that:

- Splunk Universal Forwarder was installed successfully.
- Windows Event Logs were selected.
- Splunk Enterprise was listening on TCP port 9997.
- The Receiving Indexer configuration was completed.

Verification of the Forwarder connection and log ingestion will be performed in the next part.

---

## Result

Successfully installed Splunk Universal Forwarder on Windows 10.

Configuration completed:

- Local System service account
- Application Event Log
- Security Event Log
- System Event Log
- Receiving Indexer: **192.168.1.121:9997**

---

⬅️ Previous Lab: [Part 02 - Splunk Enterprise Installation](https://github.com/microsaeid/splunk-security-labs/tree/main/Part%2002%20-%20Splunk%20Enterprise%20Installation)

➡️ Next Lab: 
