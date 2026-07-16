# Part 03-04 — Windows Server 2022 Forwarder Connection and Data Ingestion Verification

## Overview

### Summary Table

| Item | Details |
|------|---------|
| Project | Windows Server 2022 Forwarder Connection and Data Ingestion Verification |
| Operating System | Windows Server 2022 |
| Forwarder | Splunk Universal Forwarder 10.0.2 |
| Splunk Server | Ubuntu Server 24.04.4 LTS |
| Splunk Enterprise | 10.0.2 |
| Splunk Server IP | 192.168.1.121 |
| Receiving Port | TCP 9997 |
| Windows Server Host | DC01 |
| Goal | Verify the connection between the Windows Server 2022 Universal Forwarder and Splunk Enterprise and confirm Windows Event Log ingestion |

## Lab Environment

### Virtual Machines

- Windows Server 2022
- Ubuntu Server 24.04.4 LTS

### Installed Components

- Splunk Enterprise 10.0.2
- Splunk Universal Forwarder 10.0.2

## Verification Steps

### 1. Verify the Forwarder Connection

Verified that the Universal Forwarder was actively connected to the Splunk Enterprise server.

Destination:

- 192.168.1.121:9997

**Screenshot**

- `01-forwarder-connected.png`

<img width="1917" height="1165" alt="01-forwarder-connected png" src="https://github.com/user-attachments/assets/343b65bb-2637-455b-a642-7bebee747f02" />

---

### 2. Verify Incoming Windows Events

Opened **Search & Reporting** in Splunk Enterprise and verified that Windows Server events were being indexed successfully.

Verified:

- Host: DC01
- Windows Event Log events were searchable.

**Screenshot**

- `02-windows-server-events-arriving.png`

<img width="1730" height="1403" alt="02-windows-server-events-arriving png" src="https://github.com/user-attachments/assets/f07f1ae6-30f6-4c52-b3f2-6bbbda8b48d3" />

---

### 3. Verify Windows Event Log Collection

Executed the following SPL search:

```spl
host=DC01 sourcetype=WinEventLog:*
| stats count by sourcetype
```

Verified that the following Windows Event Logs were being collected:

- WinEventLog:Application
- WinEventLog:Security
- WinEventLog:System

**Screenshot**

- `03-windows-server-log-summary.png`

<img width="1730" height="1443" alt="03-windows-server-log-summary png" src="https://github.com/user-attachments/assets/852fc20c-80b3-4e66-82af-99176db7e2b7" />

---

## Result

The Windows Server 2022 Universal Forwarder successfully connected to the Splunk Enterprise server.

Windows Event Logs from **Application**, **Security**, and **System** were successfully forwarded, indexed, and searchable in Splunk Enterprise.

## Navigation

---

⬅️ Previous Lab: [Part 03-03 — Windows Server 2022 Universal Forwarder Installation](https://github.com/microsaeid/splunk-security-labs/tree/main/Part%2003-03%20%E2%80%94%20Windows%20Server%202022%20Universal%20Forwarder%20Installation)

➡️ Next Lab: 
