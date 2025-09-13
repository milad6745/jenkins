

## 1. تعریف Node

در Jenkins، وقتی می‌گیم **Node** منظورمون ماشینیه (سیستم یا سرور) که Jenkins می‌تونه روی اون Jobها یا Pipelineها رو اجرا کنه.

* **Master (یا Controller)**: همون Jenkins اصلیه که کارهای مدیریتی، زمان‌بندی و تقسیم وظایف رو انجام می‌ده.
* **Agent (یا Slave قدیمی)**: همون Nodeهای اضافی هستن که برای اجرای Jobها استفاده می‌شن.

به زبان ساده:
👉 Jenkins Master مثل مدیر پروژه‌ست، و Nodeها مثل کارگرهایی هستن که کار واقعی (Build, Test, Deploy) رو انجام می‌دن.

---

## 2. چرا از Node استفاده می‌کنیم؟

* برای **تقسیم بار کاری** (Load Balancing).
* برای **اجرای Job روی سیستم‌های مختلف** (مثلاً ویندوز، لینوکس یا مک).
* برای **مدیریت منابع** (مثلاً یک Node فقط برای تست، یکی برای Build).
* برای **اجرای موازی** چند کار هم‌زمان.

---

## 3. انواع Node

1. **Built-in Node**: همون Jenkins Master که به صورت پیش‌فرض Job رو اجرا می‌کنه.
2. **Remote Node (Agent)**: ماشینی جدا که به Jenkins وصل می‌شه.

---

## 4. روش‌های تعریف Node در Jenkins

برای تعریف یک Node جدید در Jenkins باید مراحل زیر رو انجام بدی:

### مرحله ۱: رفتن به تنظیمات Nodeها

* وارد Jenkins بشو.
* از منوی اصلی برو به:

  ```
  Manage Jenkins > Nodes and Clouds > New Node
  ```

### مرحله ۲: ایجاد Node جدید

* اسم Node رو بده (مثلاً: `Linux-Build-Agent`).
* گزینه‌ی **Permanent Agent** رو انتخاب کن.
* روی **OK** بزن.

### مرحله ۳: تنظیم مشخصات Node

تو فرم باز شده این اطلاعات رو وارد کن:

* **Description**: توضیح کوتاه درباره‌ی Node.
* **# of executors**: تعداد Jobهایی که هم‌زمان روی این Node می‌تونن اجرا بشن.
* **Remote root directory**: دایرکتوری روی سیستم Node که Jenkins فایل‌هاشو اونجا میریزه.
* **Labels**: برچسب برای انتخاب این Node توی Jobها (مثلاً `linux`, `docker`, `test`).
* **Launch method**: روش اتصال به Node

  * `Launch agent via SSH` → رایج‌ترین روش، باید SSH روی Node فعال باشه.
  * `Launch agent via Java Web Start` (قدیمی، کمتر استفاده می‌شه).
  * یا دستی (در صورت خاص).

### مرحله ۴: ذخیره و اتصال

* بعد از ذخیره، Jenkins تلاش می‌کنه با SSH یا روش انتخابی به Node وصل بشه.
* اگه همه‌چی درست باشه، وضعیت Node سبز می‌شه و آماده استفاده‌ست.

---

## 5. استفاده از Node در Pipeline

وقتی Node تعریف شد، می‌تونی توی Jenkinsfile مشخص کنی که Job روی کدوم Node اجرا بشه:

```groovy
pipeline {
    agent { label 'linux' }   // اجرا روی Node با برچسب linux
    stages {
        stage('Build') {
            steps {
                echo "Building on Linux Node..."
            }
        }
    }
}
```

---

## 6. نکات مهم

* همیشه برای پروژه‌های بزرگ چندتا Node داشته باش.
* با Labelها کار رو مرتب کن (مثلاً `windows`, `linux`, `docker`).
* منابع Node (RAM, CPU) رو متناسب با Jobها تنظیم کن.
* مطمئن شو که روی Nodeها ابزارهای لازم (Java, Git, Docker و...) نصب شده باشن.

---

