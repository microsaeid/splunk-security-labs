# بخش ۰۲ - نصب Splunk Enterprise

## نمای کلی

### جدول خلاصه

| مورد       | توضیحات                                                    |
| ---------- | ---------------------------------------------------------- |
| پروژه      | نصب Splunk Enterprise                                      |
| پلتفرم     | Microsoft Hyper-V                                          |
| سیستم‌عامل | Ubuntu Server 24.04.4 LTS                                  |
| SIEM       | Splunk Enterprise 10.0.2                                   |
| بسته نصب   | Debian (.deb)                                              |
| هدف        | نصب و راه‌اندازی اولیه Splunk Enterprise روی Ubuntu Server |

### مقدمه

در این آزمایش، نصب و راه‌اندازی اولیه Splunk Enterprise روی یک سرور اختصاصی Ubuntu مستند شده است.

ابتدا فایل نصب از سیستم Windows با استفاده از پروتکل SCP به سرور Ubuntu منتقل شد. سپس Splunk Enterprise نصب، مقداردهی اولیه، پیکربندی و اولین حساب کاربری مدیر ایجاد شد. در پایان نیز از طریق رابط وب Splunk صحت نصب بررسی و تأیید شد.

## محیط آزمایش

### ماشین‌های مجازی

* سرور Splunk

### سیستم‌عامل‌ها

* Ubuntu Server 24.04.4 LTS
* Windows 11 (میزبان)

### SIEM

* Splunk Enterprise 10.0.2 (نسخه All-in-One)

## مراحل انجام آزمایش

### ۱. اتصال به سرور Ubuntu

از طریق Windows PowerShell:

```powershell
ssh saeid@192.168.1.121
```

قبل از شروع نصب، اتصال از راه دور به سرور بررسی و تأیید شد.

### ۲. انتقال بسته نصب Splunk Enterprise

```powershell
scp "D:\Windows Files\Downloads\Programs\Splunk\splunk-10.0.2-e2d18b4767e9-linux-amd64.deb" saeid@192.168.1.121:/home/saeid/
```

بسته نصب با موفقیت به سرور Ubuntu منتقل شد.

### ۳. بررسی فایل منتقل‌شده

```bash
ls -lh /home/saeid/splunk-10.0.2-e2d18b4767e9-linux-amd64.deb
```

قبل از شروع نصب، وجود فایل نصب بررسی و تأیید شد.

### ۴. نصب Splunk Enterprise

```bash
sudo dpkg -i /home/saeid/splunk-10.0.2-e2d18b4767e9-linux-amd64.deb
```

Splunk Enterprise با موفقیت روی سرور نصب شد.

### ۵. بررسی بسته نصب‌شده

```bash
dpkg -l | grep splunk
```

نصب موفق Splunk Enterprise نسخه 10.0.2 تأیید شد.

### ۶. بررسی مسیر نصب

```bash
ls -ld /opt/splunk
```

ایجاد صحیح پوشه نصب بررسی و تأیید شد.

### ۷. راه‌اندازی اولیه Splunk Enterprise

```bash
sudo /opt/splunk/bin/splunk start --accept-license
```

در این مرحله عملیات زیر انجام شد:

* پذیرش توافق‌نامه مجوز (License)
* ایجاد اولین حساب کاربری مدیر
* راه‌اندازی سرویس‌های Splunk
* ایجاد گواهی‌های پیش‌فرض
* ایجاد Indexهای پیش‌فرض

### ۸. بررسی رابط وب Splunk

رابط وب Splunk از طریق آدرس زیر باز شد:

```text
http://192.168.1.121:8000
```

ورود با حساب کاربری مدیر با موفقیت انجام شد.

## نکات کلیدی

* Splunk Enterprise با موفقیت روی Ubuntu Server نصب شد.
* راه‌اندازی اولیه پلتفرم برای اولین استفاده انجام شد.
* اولین حساب کاربری مدیر ایجاد شد.
* دسترسی به رابط وب Splunk با موفقیت تأیید شد.
* بستر SIEM برای مراحل بعدی، شامل دریافت لاگ‌ها و تحلیل رویدادها، آماده شد.

## مسیر آزمایش‌ها

⬅️ آزمایش قبلی: **بخش ۰۱ - آماده‌سازی Ubuntu Server برای Splunk**

➡️ آزمایش بعدی: **بخش ۰۳-۰۱ - نصب Universal Forwarder روی Windows 10**
