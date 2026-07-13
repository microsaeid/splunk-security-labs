# Part 02 - Splunk Enterprise Installation

Install Splunk Enterprise on Ubuntu Server and verify that the installation is completed successfully.

## Project Overview

In this lab, Splunk Enterprise was installed on an Ubuntu Server virtual machine. The installation included creating the administrator account, enabling the Splunk service, and verifying access to the Splunk Web interface.

## Objectives

* Install Splunk Enterprise
* Create the administrator account
* Start the Splunk service
* Enable Splunk at boot
* Verify the installation

## Prerequisites

* Ubuntu Server installed
* Internet connection
* Splunk Enterprise `.deb` package

## Installation

Verify the installation package.

```bash
ls -lh
```

Install Splunk Enterprise.

```bash
sudo dpkg -i splunk-*.deb
```

Move to the Splunk binary directory.

```bash
cd /opt/splunk/bin
```

Start Splunk for the first time.

```bash
sudo ./splunk start --accept-license
```

Create the administrator account when prompted.

Enable Splunk to start automatically after reboot.

```bash
sudo ./splunk enable boot-start
```

## Verification

Check the service status.

```bash
sudo ./splunk status
```

Verify the installed version.

```bash
sudo ./splunk version
```

Open a browser and access:

```text
http://<SERVER-IP>:8000
```

Log in using the administrator account.

## Screenshots

```
images/
├── 01-download-package.png
├── 02-installation.png
├── 03-first-start.png
├── 04-login-page.png
└── 05-splunk-home.png
```

## Project Structure

```text
Part-02-Splunk-Enterprise-Installation/
├── README.md
└── images/
```

## Key Takeaways

* Splunk Enterprise was installed successfully.
* The administrator account was created.
* Splunk was configured to start automatically.
* The installation was verified from both the command line and the web interface.

## Next Lab

**Part 03 - Initial Splunk Configuration**
