# Part 04-01 — Search Interface

## Overview

This lab introduces the Splunk Search & Reporting interface and its main components.

## Lab Environment

- Splunk Enterprise 10.0.2
- Ubuntu Server 24.04.4 LTS

## Steps

### 1. Open Search & Reporting

From the Splunk home page, opened the **Search & Reporting** application.

![Search & Reporting App](https://github.com/microsaeid/splunk-security-labs/blob/main/Splunk%2004-01-Search%20Interface/Search%20Interface%201.png)

---

### 2. Review the Search Interface

Reviewed the main interface, including:

- Search Bar
- Time Range Picker
- Search Mode
- Search Results
- Timeline

![Search Interface](https://github.com/microsaeid/splunk-security-labs/blob/main/Splunk%2004-01-Search%20Interface/Search%20Interface%202.png)

---

### 3. Run the First Search

Executed the following search:

```spl
index=main
```

Verified that indexed events were returned successfully.

![First Search Results](https://github.com/microsaeid/splunk-security-labs/blob/main/Splunk%2004-01-Search%20Interface/Search%20Interface%203.png)

## Result

Successfully explored the Search & Reporting interface and verified that searchable events were available in Splunk.
