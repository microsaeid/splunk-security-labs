# بخش 03-01 - نصب Universal Forwarder روی Windows 10

## معرفی

### خلاصه آزمایش

| مورد | توضیحات |
|------|---------|
| پروژه | نصب Universal Forwarder روی Windows 10 |
| سیستم‌عامل | Windows 10 |
| نسخه Forwarder | Splunk Universal Forwarder 10.0.2 |
| معماری | 64 بیتی |
| Service Account | Local System |
| سرور Splunk | Ubuntu Server 24.04.4 LTS |
| آدرس IP سرور | 192.168.1.121 |
| پورت دریافت | TCP 9997 |
| لاگ‌های انتخاب‌شده | Application، Security، System |
| هدف | نصب و پیکربندی Splunk Universal Forwarder روی Windows 10 |

---

## محیط آزمایش

### ماشین‌های مجازی

- Windows 10
- Ubuntu Server 24.04.4 LTS

### نرم‌افزارهای نصب‌شده

- Splunk Enterprise
- Splunk Universal Forwarder 10.0.2

---

## مراحل نصب

### 1. دانلود Universal Forwarder

نسخه 64 بیتی مخصوص Windows دانلود شد.

```text
splunkforwarder-10.0.2-windows-x64.msi
```

![دانلود Universal Forwarder](images/01-universal-forwarder-installer-file.png)

---

### 2. شروع نصب

در اولین مرحله:

- لایسنس نرم‌افزار پذیرفته شد.
- گزینه **On-premises Splunk Enterprise** انتخاب شد.

![شروع نصب](images/02-universal-forwarder-setup-start.png)

---

### 3. مسیر نصب

مسیر پیش‌فرض نصب بدون تغییر باقی ماند.

```text
C:\Program Files\SplunkUniversalForwarder
```

در این آزمایش از SSL Certificate اختصاصی استفاده نشد.

---

### 4. انتخاب Service Account

سرویس Universal Forwarder با حساب زیر اجرا شد:

- Local System

این حساب دسترسی لازم برای خواندن Windows Event Logها را فراهم می‌کند.

---

### 5. انتخاب Windows Event Logها

لاگ‌های زیر برای ارسال به Splunk انتخاب شدند:

- Application
- Security
- System

گزینه‌های زیر فعال نشدند:

- Forwarded Events
- Setup Log
- Performance Monitor
- Active Directory Monitoring

![انتخاب Windows Event Log](images/03-windows-event-logs-selected.png)

---

### 6. ایجاد حساب مدیریتی

برای مدیریت Universal Forwarder یک حساب محلی ایجاد شد.

```text
Username: admin
```

رمز عبور به دلایل امنیتی در این مخزن ذخیره نشده است.

![حساب مدیریتی Forwarder](images/04-forwarder-admin-account.png)

---

### 7. Deployment Server

در این آزمایش از Deployment Server استفاده نشد.

---

### 8. فعال کردن Receiving روی Splunk Enterprise

برای دریافت لاگ‌های ارسالی از Universal Forwarder، پورت TCP 9997 روی Splunk فعال شد.

فعال‌سازی Receiving:

```bash
sudo /opt/splunk/bin/splunk enable listen 9997
```

بررسی وضعیت Listening:

```bash
sudo /opt/splunk/bin/splunk display listen
```

خروجی مورد انتظار:

```text
Receiving is enabled on port 9997.
```

![فعال شدن پورت Receiving](images/05-splunk-receiving-port-enabled.png)

---

### 9. پیکربندی Receiving Indexer

Universal Forwarder برای ارسال لاگ‌ها به سرور Splunk تنظیم شد.

```text
Server IP : 192.168.1.121
Port      : 9997
```

![تنظیم Receiving Indexer](images/06-receiving-indexer-settings.png)

---

### 10. پایان نصب

نصب Universal Forwarder با موفقیت به پایان رسید.

![پایان نصب](images/07-universal-forwarder-installation-completed.png)

---

## بررسی نهایی

موارد زیر بررسی شدند:

- Universal Forwarder با موفقیت نصب شد.
- Windows Event Logهای موردنظر انتخاب شدند.
- Splunk Enterprise روی پورت TCP 9997 در حالت Listening قرار گرفت.
- تنظیمات Receiving Indexer انجام شد.

بررسی اتصال Forwarder و دریافت لاگ‌ها در بخش بعدی انجام خواهد شد.

---

## نتیجه

Splunk Universal Forwarder با موفقیت روی Windows 10 نصب و پیکربندی شد.

تنظیمات انجام‌شده:

- اجرای سرویس با حساب Local System
- جمع‌آوری Application Log
- جمع‌آوری Security Log
- جمع‌آوری System Log
- ارسال لاگ‌ها به سرور Splunk

```text
192.168.1.121:9997
```

---

⬅️ **آزمایش قبلی:** Part 02 - Splunk Enterprise Installation
