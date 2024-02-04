#`create item`


در Jenkins، می‌توانید مراحل زیر را دنبال کنید:


ورود به پنل مدیریت Jenkins:
        وارد پنل مدیریت Jenkins شوید. برای این کار، به URL Jenkins خود بروید (معمولاً در آدرس http://localhost:8080/ قرار دارد) و به بخش "Manage Jenkins" بروید.


ساخت یک آیتم جدید (New Item):
        در صفحه مدیریت Jenkins، گزینه "New Item" یا "Create New Jobs" را انتخاب کنید.


تعیین نام و نوع آیتم:
        یک نام برای آیتم جدید خود وارد کنید (مثلاً "HelloWorld").
        نوع آیتم را انتخاب کنید، مثلاً "Freestyle project" یا "Pipeline" بسته به نوع پروژه‌ای که می‌خواهید ایجاد کنید.


تنظیمات آیتم (Job):
        در صفحه تنظیمات آیتم، بخش‌های مختلفی وجود دارد که شما می‌توانید تنظیمات مربوط به پروژه‌تان را انجام دهید.
        
```
        pipeline {
    agent any
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }
}
```
سپس Save میکنیم و Build میکنیم .

![image](https://github.com/milad6745/jenkins/assets/113288076/6cc743cd-e37f-4a5f-b7e3-25e2a7a8acb6)

مشاهده میکنیم که پایپ لاین اجرا شده است .


Pipeline step

![image](https://github.com/milad6745/jenkins/assets/113288076/546ae344-02e3-4d33-b0d2-7e50ec363213)
