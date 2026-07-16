# Part 03-02 — Windows 10 Forwarder Configuration and Verification

## Overview

### Summary Table

| Item | Details |
|------|---------|
| Project | Windows 10 Forwarder Configuration and Verification |
| Operating System | Windows 10 |
| Forwarder | Splunk Universal Forwarder 10.0.2 |
| Splunk Server | Ubuntu Server 24.04.4 LTS |
| Splunk Enterprise | 10.0.2 |
| Splunk Server IP | 192.168.1.121 |
| Receiving Port | TCP 9997 |
| Windows 10 IP | 192.168.1.72 |
| Windows Logs | Application, Security, System |
| Goal | Verify that the Windows 10 Universal Forwarder is connected to Splunk Enterprise and confirm successful Windows Event Log ingestion. |

---

## Lab Environment

### Virtual Machines

- Windows 10
- Ubuntu Server 24.04.4 LTS

### Installed Components

- Splunk Enterprise 10.0.2
- Splunk Universal Forwarder 10.0.2

---

## Verification Steps

### 1. Verify Splunk Enterprise Status

On the Splunk server:

```bash
sudo /opt/splunk/bin/splunk status
```

Output:

```text
splunkd is running
splunk helpers are running
```

---

### 2. Verify Receiving Port

The Splunk server was already configured to receive forwarded data on TCP port **9997**.

```text
Receiving is enabled on port 9997
```

---

### 3. Verify Network Connectivity

From the Windows 10 virtual machine:

```powershell
Test-NetConnection 192.168.1.121 -Port 9997
```

Result:

```text
RemoteAddress    : 192.168.1.121
RemotePort       : 9997
SourceAddress    : 192.168.1.72
TcpTestSucceeded : True
```

---

### 4. Verify the Universal Forwarder Service

The **SplunkForwarder** Windows service was verified to be running.

---

### 5. Verify the Forwarder Connection

From the Universal Forwarder installation directory:

```cmd
splunk list forward-server
```

Output:

```text
Active forwards:
    192.168.1.121:9997

Configured but inactive forwards:
    None
```

---

### 6. Verify Windows Event Ingestion

Open **Search & Reporting** and run:

```spl
index=*
```

Windows Security Event Logs were successfully received from the Windows 10 virtual machine.

---

### 7. Verify Event Metadata

The received events contained the following metadata:

```text
host = DESKTOP-S8HR81A
source = WinEventLog:Security
sourcetype = WinEventLog:Security
```

Example Windows Event IDs:

```text
4624
4672
```

---

## Verification Searches

### Show Windows 10 Events

```spl
index=* host=DESKTOP-S8HR81A
```
<img width="3840" height="1901" alt="Search-Splunk-10-0-2-07-15-2026_03_40_PM" src="https://github.com/user-attachments/assets/19fec4c1-02f4-48ca-b998-a9494a1b82b5" />

### Show Windows Security Events

```spl
index=* host=DESKTOP-S8HR81A sourcetype=WinEventLog:Security
```
<img width="3840" height="1907" alt="image" src="https://github.com/user-attachments/assets/326855ee-f3a4-4445-9114-952c5de71035" />

### Count Events by Host and Sourcetype

```spl
index=*
| stats count by host sourcetype
```
<img width="3840" height="1983" alt="Search-Splunk-10-0-2-07-15-2026_03_41_PM (1)" src="https://github.com/user-attachments/assets/57331a0c-22a9-4af7-a57f-9184a22ac730" />

### Count Events by Sourcetype

```spl
index=*
| stats count by sourcetype
```
<img width="3840" height="1916" alt="Search-Splunk-10-0-2-07-15-2026_03_42_PM" src="https://github.com/user-attachments/assets/531fa0ce-cba7-4833-910f-6cfbd48ef8c2" />

---

## Verification Results

- Splunk Enterprise was running successfully.
- TCP port **9997** was reachable from Windows 10.
- The **SplunkForwarder** service was running.
- The Universal Forwarder had an active connection to the Splunk server.
- Windows Security Event Logs were successfully indexed.
- The Windows host was correctly identified.
- The Windows Event Log source and sourcetype were correctly assigned.
- Searches successfully returned Windows Event Log data.

---

## Navigation

Previous: [Part 03-01 — Windows 10 Universal Forwarder Installation](../03-01-windows-10-universal-forwarder-installation/README.md)

Next: [Part 03-03 — Windows Server 2022 Universal Forwarder Installation](https://github.com/microsaeid/splunk-security-labs/tree/main/Part%2003-03%20%E2%80%94%20Windows%20Server%202022%20Universal%20Forwarder%20Installation)
