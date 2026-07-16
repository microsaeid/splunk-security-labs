# بخش 03-02 — پیکربندی و بررسی Universal Forwarder ویندوز 10

## نمای کلی

### خلاصه آزمایش

| مورد | توضیحات |
|------|---------|
| پروژه | پیکربندی و بررسی Universal Forwarder ویندوز 10 |
| سیستم‌عامل | Windows 10 |
| فورواردر | Splunk Universal Forwarder 10.0.2 |
| سرور Splunk | Ubuntu Server 24.04.4 LTS |
| نسخه Splunk Enterprise | 10.0.2 |
| آدرس IP سرور Splunk | 192.168.1.121 |
| پورت دریافت | TCP 9997 |
| آدرس IP ویندوز 10 | 192.168.1.72 |
| لاگ‌های انتخاب‌شده | Application، Security، System |
| هدف | اطمینان از اتصال Universal Forwarder ویندوز 10 به Splunk Enterprise و بررسی دریافت صحیح Windows Event Logها |

---

## محیط آزمایش

### ماشین‌های مجازی

- Windows 10
- Ubuntu Server 24.04.4 LTS

### نرم‌افزارهای نصب‌شده

- Splunk Enterprise 10.0.2
- Splunk Universal Forwarder 10.0.2

---

## مراحل بررسی

### 1. بررسی وضعیت Splunk Enterprise

روی سرور Splunk دستور زیر اجرا شد:

```bash
sudo /opt/splunk/bin/splunk status
```

خروجی نشان داد که سرویس Splunk به‌درستی در حال اجرا است.

```text
splunkd is running
splunk helpers are running
```

---

### 2. بررسی پورت دریافت

سرور Splunk از قبل برای دریافت داده‌ها روی پورت **9997/TCP** پیکربندی شده بود.

```text
Receiving is enabled on port 9997
```

---

### 3. بررسی ارتباط شبکه

برای اطمینان از برقراری ارتباط بین Windows 10 و سرور Splunk، دستور زیر در PowerShell اجرا شد.

```powershell
Test-NetConnection 192.168.1.121 -Port 9997
```

نتیجه:

```text
RemoteAddress    : 192.168.1.121
RemotePort       : 9997
SourceAddress    : 192.168.1.72
TcpTestSucceeded : True
```

این نتیجه نشان داد که ارتباط TCP با موفقیت برقرار است.

---

### 4. بررسی سرویس Universal Forwarder

سرویس **SplunkForwarder** در Windows Services بررسی شد و در وضعیت **Running** قرار داشت.

---

### 5. بررسی اتصال Universal Forwarder

در پوشه نصب Universal Forwarder دستور زیر اجرا شد:

```cmd
splunk list forward-server
```

خروجی:

```text
Active forwards:
    192.168.1.121:9997

Configured but inactive forwards:
    None
```

این خروجی نشان داد که Universal Forwarder با موفقیت به سرور Splunk متصل شده است.

---

### 6. بررسی دریافت Windows Event Log

در محیط **Search & Reporting** دستور زیر اجرا شد:

```spl
index=*
```

نتایج جستجو نشان داد که Windows Security Event Logها با موفقیت وارد Splunk شده‌اند.

---

### 7. بررسی اطلاعات Event

اطلاعات Eventهای دریافت‌شده شامل موارد زیر بود:

```text
host = DESKTOP-S8HR81A
source = WinEventLog:Security
sourcetype = WinEventLog:Security
```

نمونه Event IDهای مشاهده‌شده:

```text
4624
4672
```

---

## جستجوهای انجام‌شده

### نمایش Eventهای Windows 10

```spl
index=* host=DESKTOP-S8HR81A
```
<img width="3840" height="1901" alt="Search-Splunk-10-0-2-07-15-2026_03_40_PM" src="https://github.com/user-attachments/assets/e6270877-b6fa-4c80-881e-b2fa67ce164a" />

### نمایش Eventهای Security

```spl
index=* host=DESKTOP-S8HR81A sourcetype=WinEventLog:Security
```
<img width="3840" height="1907" alt="image" src="https://github.com/user-attachments/assets/3fac8d85-b1bd-47ac-b146-33948ba2847b" />

### شمارش Eventها بر اساس Host و Sourcetype

```spl
index=*
| stats count by host sourcetype
```
<img width="3840" height="1983" alt="Search-Splunk-10-0-2-07-15-2026_03_41_PM (1)" src="https://github.com/user-attachments/assets/b9423346-3066-4c05-b436-05f1b9fc6cd7" />

### شمارش Eventها بر اساس Sourcetype

```spl
index=*
| stats count by sourcetype
```
<img width="3840" height="1916" alt="Search-Splunk-10-0-2-07-15-2026_03_42_PM" src="https://github.com/user-attachments/assets/40592758-12ef-4eb3-a2b3-87b4e9ce02ed" />

---

## نتایج بررسی

- سرویس Splunk Enterprise با موفقیت در حال اجرا بود.
- پورت **9997/TCP** از Windows 10 قابل دسترس بود.
- سرویس **SplunkForwarder** در وضعیت Running قرار داشت.
- Universal Forwarder با موفقیت به سرور Splunk متصل شده بود.
- Windows Security Event Logها با موفقیت وارد Splunk شدند.
- نام Host ویندوز به‌درستی شناسایی شد.
- Source و Sourcetype به‌درستی ثبت شدند.
- جستجوها با موفقیت Eventهای ویندوز را نمایش دادن

## مسیر آزمایش

**بخش قبلی:**

[بخش 03-01 — نصب Universal Forwarder روی Windows 10](../03-01-windows-10-universal-forwarder-installation/README.md)

**بخش بعدی:**

[بخش 03-03 — نصب Universal Forwarder روی Windows Server 2022](../03-03-windows-server-2022-universal-forwarder-installation/README.md)
