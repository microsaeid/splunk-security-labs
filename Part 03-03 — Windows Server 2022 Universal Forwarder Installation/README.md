# Part 03-03 — Windows Server 2022 Universal Forwarder Installation

## Overview

### Summary Table

| Item | Details |
|------|---------|
| Project | Windows Server 2022 Universal Forwarder Installation |
| Operating System | Windows Server 2022 |
| Forwarder Version | Splunk Universal Forwarder 10.0.2 |
| Architecture | 64-bit |
| Service Account | Local System |
| Splunk Server | Ubuntu Server 24.04.4 LTS |
| Splunk Server IP | 192.168.1.121 |
| Receiving Port | TCP 9997 |
| Selected Windows Logs | Application, Security, System |
| Goal | Install and configure Splunk Universal Forwarder on Windows Server 2022 |

## Lab Environment

### Virtual Machines

- Windows Server 2022
- Ubuntu Server 24.04.4 LTS

### Installed Components

- Splunk Enterprise 10.0.2
- Splunk Universal Forwarder 10.0.2

## Installation Steps

### 1. Download the Universal Forwarder

Downloaded the 64-bit Windows MSI installer.

```
splunkforwarder-10.0.2-windows-x64.msi
```

**Screenshot**

- `01-downloaded-installer.png`
<img width="4000" height="2252" alt="01-downloaded-installer png" src="https://github.com/user-attachments/assets/b9a5bfa7-34ef-4c7e-ace5-226870d4b0fd" />


---

### 2. Start the Installation

Started the Universal Forwarder installation.

Accepted the license agreement.

Selected:

- On-premises Splunk Enterprise

Configured the forwarder to communicate with the Splunk Enterprise server.

> **Note**
>
> The installation configuration screen was not captured during the lab.

---

### 3. Configure the Service Account

Selected:

- Local System

Continued with the default installation settings.

---

### 4. Select Windows Event Logs

Selected the following Windows Event Logs for forwarding:

- Application
- Security
- System

**Screenshot**

- `03-windows-logs-selection.png`
<img width="4000" height="2252" alt="03-windows-logs-selection png" src="https://github.com/user-attachments/assets/128e4894-100e-4ae1-9f5d-3f5c32f06ccb" />
---

### 5. Complete the Installation

Completed the installation successfully.

**Screenshot**

- `04-installation-complete.png`
<img width="4000" height="2252" alt="04-installation-complete png" src="https://github.com/user-attachments/assets/ea23a032-aeab-4004-ac65-5577a3f43547" />
---

### 6. Verify the Forwarder Service

Verified that the **SplunkForwarder** service was running after the installation.

**Screenshot**

- `05-forwarder-service-running.png`
<img width="4000" height="2252" alt="05-forwarder-service-running png" src="https://github.com/user-attachments/assets/fea1a914-f664-41ec-b598-298264729484" />
## Result

The Splunk Universal Forwarder was successfully installed on Windows Server 2022.

The SplunkForwarder service was running under the Local System account.

The forwarder was configured for communication with the Splunk Enterprise server and was ready for log forwarding.

## Navigation


---

⬅️ Previous Lab: [Part 03-02 — Windows 10 Forwarder Configuration and Verification](https://github.com/microsaeid/splunk-security-labs/tree/main/Part%2003-02%20%E2%80%94%20Windows%2010%20Forwarder%20Connection%20and%20Data%20Ingestion%20Verification)

➡️ Next Lab: 
