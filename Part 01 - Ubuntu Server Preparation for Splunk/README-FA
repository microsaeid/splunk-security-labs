# بخش ۰۱ - آماده‌سازی Ubuntu Server برای Splunk

## نمای کلی

### جدول خلاصه

| مورد              | توضیحات                                                  |
| ----------------- | -------------------------------------------------------- |
| پروژه             | آماده‌سازی Ubuntu Server برای Splunk                     |
| پلتفرم            | Microsoft Hyper-V                                        |
| سرور              | ماشین مجازی Splunk Server                                |
| سیستم‌عامل        | Ubuntu Server 24.04.4 LTS                                |
| شبکه              | External Virtual Switch                                  |
| دسترسی از راه دور | OpenSSH                                                  |
| هدف               | آماده‌سازی یک سرور Ubuntu برای استقرار Splunk Enterprise |

### مقدمه

در این آزمایش، یک ماشین مجازی اختصاصی Ubuntu Server برای نصب Splunk Enterprise ایجاد و آماده‌سازی شد.

## محیط آزمایش

### ماشین‌های مجازی

* سرور Splunk

### سیستم‌عامل‌ها

* Ubuntu Server 24.04.4 LTS
* Windows 11 (میزبان)

### مجازی‌سازی

* Microsoft Hyper-V
* ماشین مجازی نسل دوم (Generation 2)
* My External Lab Virtual Switch

### منابع سرور

| منبع        | پیکربندی                                |
| ----------- | --------------------------------------- |
| حافظه       | ۸ گیگابایت                              |
| پردازنده    | ۴ هسته مجازی (vCPU)                     |
| دیسک مجازی  | ۱۰۰ گیگابایت VHDX با قابلیت افزایش پویا |
| شبکه        | External Virtual Switch                 |
| Secure Boot | Microsoft UEFI Certificate Authority    |

## مراحل انجام آزمایش

### ۱. ایجاد ماشین مجازی

* نام ماشین مجازی: `Splunk-Server`
* نسل: ۲
* حافظه: 8192 مگابایت
* پردازنده: ۴ هسته
* دیسک مجازی: ۱۰۰ گیگابایت
* شبکه: My External Lab
* فایل نصب: Ubuntu Server 24.04.4 LTS ISO
* Secure Boot: Microsoft UEFI Certificate Authority

### ۲. نصب Ubuntu Server

تنظیمات نصب:

* نصب نسخه استاندارد Ubuntu Server
* استفاده از کل دیسک
* غیرفعال بودن LVM
* غیرفعال بودن رمزگذاری دیسک
* عدم فعال‌سازی Ubuntu Pro
* غیرفعال بودن درایورهای شخص ثالث
* عدم نصب Featured Server Snaps
* نصب OpenSSH Server
* فعال بودن احراز هویت با رمز عبور

تنظیمات سرور:

* نام میزبان: `splunk-server`
* نام کاربری: `saeid`

### ۳. به‌روزرسانی مخازن نرم‌افزاری

```bash
sudo apt update
```

### ۴. بررسی آدرس IP سرور

```bash
hostname -i
```

خروجی:

```text
127.0.1.1
```

```bash
hostname -I
```

خروجی:

```text
192.168.1.121
```

### ۵. بررسی ارتباط شبکه

```powershell
ping 192.168.1.121
```

### ۶. بررسی نصب بودن OpenSSH

```bash
sudo apt install openssh-server -y
```

### ۷. بررسی وضعیت سرویس SSH

```bash
sudo systemctl status ssh
```

خروجی:

```text
inactive (dead)
```

### ۸. فعال‌سازی سرویس SSH

```bash
sudo systemctl enable ssh
```

### ۹. اجرای سرویس SSH

```bash
sudo systemctl start ssh
```

### ۱۰. بررسی مجدد وضعیت سرویس SSH

```bash
sudo systemctl status ssh
```

خروجی:

```text
active (running)
```

### ۱۱. بررسی پورت TCP شماره ۲۲

```bash
sudo ss -tlnp | grep :22
```

خروجی:

```text
0.0.0.0:22
[::]:22
```

### ۱۲. بررسی دسترسی به پورت ۲۲

```powershell
Test-NetConnection 192.168.1.121 -Port 22
```

خروجی:

```text
TcpTestSucceeded : True
```

### ۱۳. اتصال به سرور Ubuntu

```powershell
ssh saeid@192.168.1.121
```

## نکات کلیدی

* یک ماشین مجازی اختصاصی Ubuntu Server برای آزمایشگاه Splunk ایجاد شد.
* تنظیمات شبکه و OpenSSH برای مدیریت از راه دور پیکربندی شد.
* وضعیت سرویس SSH و در دسترس بودن پورت TCP شماره ۲۲ بررسی و تأیید شد.
* اتصال SSH از سیستم Windows با موفقیت انجام شد.
* سرور Ubuntu برای نصب Splunk Enterprise آماده شد.

## مسیر آزمایش‌ها

➡️ آزمایش بعدی: **بخش ۰۲ - نصب Splunk Enterprise**
