# بخش 03-03 — نصب Splunk Universal Forwarder روی Windows Server 2022

## نمای کلی

### خلاصه

| مورد | توضیحات |
|------|---------|
| پروژه | نصب Splunk Universal Forwarder روی Windows Server 2022 |
| سیستم‌عامل | Windows Server 2022 |
| نسخه Forwarder | Splunk Universal Forwarder 10.0.2 |
| معماری | 64 بیتی |
| حساب سرویس | Local System |
| سرور Splunk | Ubuntu Server 24.04.4 LTS |
| IP سرور Splunk | 192.168.1.121 |
| پورت دریافت | TCP 9997 |
| لاگ‌های انتخاب‌شده | Application، Security، System |
| هدف | نصب و پیکربندی Splunk Universal Forwarder روی Windows Server 2022 |

## محیط آزمایش

### ماشین‌های مجازی

- Windows Server 2022
- Ubuntu Server 24.04.4 LTS

### نرم‌افزارهای نصب‌شده

- Splunk Enterprise 10.0.2
- Splunk Universal Forwarder 10.0.2

## مراحل نصب

### 1. دانلود Universal Forwarder

فایل نصب نسخه ۶۴ بیتی ویندوز دانلود شد.

```text
splunkforwarder-10.0.2-windows-x64.msi
```

**اسکرین‌شات**

- `01-downloaded-installer.png`

<img width="4000" height="2252" alt="01-downloaded-installer png" src="https://github.com/user-attachments/assets/b9a5bfa7-34ef-4c7e-ace5-226870d4b0fd" />

---

### 2. شروع نصب

نصب Splunk Universal Forwarder آغاز شد.

پس از پذیرش License Agreement، گزینه زیر انتخاب شد:

- On-premises Splunk Enterprise

سپس اطلاعات سرور Splunk برای برقراری ارتباط وارد شد.

> **توجه**
>
> از صفحه تنظیمات نصب اسکرین‌شات تهیه نشد.

---

### 3. انتخاب حساب سرویس

برای اجرای سرویس، گزینه زیر انتخاب شد:

- Local System

سایر تنظیمات با مقادیر پیش‌فرض ادامه یافت.

---

### 4. انتخاب Windows Event Logها

برای ارسال به Splunk، لاگ‌های زیر انتخاب شدند:

- Application
- Security
- System

**اسکرین‌شات**

- `03-windows-logs-selection.png`

<img width="4000" height="2252" alt="03-windows-logs-selection png" src="https://github.com/user-attachments/assets/128e4894-100e-4ae1-9f5d-3f5c32f06ccb" />

---

### 5. پایان نصب

فرآیند نصب با موفقیت به پایان رسید.

**اسکرین‌شات**

- `04-installation-complete.png`

<img width="4000" height="2252" alt="04-installation-complete png" src="https://github.com/user-attachments/assets/ea23a032-aeab-4004-ac65-5577a3f43547" />

---

### 6. بررسی سرویس Forwarder

پس از نصب، سرویس **SplunkForwarder** بررسی شد و در وضعیت **Running** قرار داشت.

**اسکرین‌شات**

- `05-forwarder-service-running.png`

<img width="4000" height="2252" alt="05-forwarder-service-running png" src="https://github.com/user-attachments/assets/fea1a914-f664-41ec-b598-298264729484" />

## نتیجه

Splunk Universal Forwarder با موفقیت روی Windows Server 2022 نصب شد.

سرویس **SplunkForwarder** با حساب **Local System** در وضعیت **Running** قرار گرفت.

Forwarder برای برقراری ارتباط با سرور Splunk پیکربندی شد و آماده ارسال لاگ‌های ویندوز است.

## مسیر مطالعه

---

⬅️ **بخش قبلی:** [بخش 03-02 — پیکربندی Universal Forwarder روی Windows 10 و بررسی ورود لاگ‌ها](https://github.com/microsaeid/splunk-security-labs/tree/main/Part%2003-02%20%E2%80%94%20Windows%2010%20Forwarder%20Connection%20and%20Data%20Ingestion%20Verification)

➡️ **بخش بعدی:** بخش 03-04 — اتصال Windows Server 2022 به Splunk و بررسی ورود لاگ‌ها
