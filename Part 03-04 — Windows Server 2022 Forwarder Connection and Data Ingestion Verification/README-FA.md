# بخش 03-04 — بررسی اتصال Universal Forwarder ویندوز سرور 2022 و تأیید ورود لاگ‌ها

## نمای کلی

### جدول خلاصه

| مورد | توضیحات |
|------|---------|
| پروژه | بررسی اتصال Universal Forwarder ویندوز سرور 2022 و تأیید ورود لاگ‌ها |
| سیستم‌عامل | Windows Server 2022 |
| فورواردر | Splunk Universal Forwarder 10.0.2 |
| سرور Splunk | Ubuntu Server 24.04.4 LTS |
| نسخه Splunk Enterprise | 10.0.2 |
| آدرس IP سرور Splunk | 192.168.1.121 |
| پورت دریافت | TCP 9997 |
| نام میزبان ویندوز سرور | DC01 |
| هدف | بررسی اتصال Universal Forwarder به Splunk Enterprise و اطمینان از ورود لاگ‌های Windows Event Log |

## محیط آزمایشگاه

### ماشین‌های مجازی

- Windows Server 2022
- Ubuntu Server 24.04.4 LTS

### اجزای نصب‌شده

- Splunk Enterprise 10.0.2
- Splunk Universal Forwarder 10.0.2

## مراحل بررسی

### 1. بررسی اتصال Forwarder

اطمینان حاصل شد که Universal Forwarder با موفقیت به سرور Splunk Enterprise متصل است.

مقصد اتصال:

- 192.168.1.121:9997

**اسکرین‌شات**

- `01-forwarder-connected.png`

<img width="1917" height="1165" alt="01-forwarder-connected png" src="https://github.com/user-attachments/assets/343b65bb-2637-455b-a642-7bebee747f02" />

---

### 2. بررسی ورود Eventهای ویندوز

بخش **Search & Reporting** در Splunk Enterprise باز شد و بررسی شد که Eventهای Windows Server با موفقیت ایندکس شده‌اند.

موارد تأییدشده:

- Host: DC01
- Eventهای Windows Event Log قابل جستجو هستند.

**اسکرین‌شات**

- `02-windows-server-events-arriving.png`

<img width="1730" height="1403" alt="02-windows-server-events-arriving png" src="https://github.com/user-attachments/assets/f07f1ae6-30f6-4c52-b3f2-6bbbda8b48d3" />

---

### 3. بررسی جمع‌آوری Windows Event Log

برای بررسی نوع لاگ‌های دریافتی، جستجوی زیر در Splunk اجرا شد:

```spl
host=DC01 sourcetype=WinEventLog:*
| stats count by sourcetype
```

تأیید شد که لاگ‌های زیر در حال جمع‌آوری هستند:

- WinEventLog:Application
- WinEventLog:Security
- WinEventLog:System

**اسکرین‌شات**

- `03-windows-server-log-summary.png`

<img width="1730" height="1443" alt="03-windows-server-log-summary png" src="https://github.com/user-attachments/assets/852fc20c-80b3-4e66-82af-99176db7e2b7" />

---

## نتیجه

اتصال Universal Forwarder ویندوز سرور 2022 به Splunk Enterprise با موفقیت برقرار شد.

همچنین تأیید شد که لاگ‌های **Application**، **Security** و **System** با موفقیت به Splunk ارسال، ایندکس و قابل جستجو هستند.

## مسیر مطالعه

---

⬅️ **بخش قبلی:** [بخش 03-03 — نصب Universal Forwarder روی Windows Server 2022](https://github.com/microsaeid/splunk-security-labs/tree/main/Part%2003-03%20%E2%80%94%20Windows%20Server%202022%20Universal%20Forwarder%20Installation)

➡️ **بخش بعدی:**
