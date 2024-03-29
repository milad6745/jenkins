# `parameter`

## `String parameter`

در اینجا یک پارامتر در محیط گلوبال از نوع string تعریف میکنیم .
```
pipeline {
    agent any
    parameters {
        string(name: "x", defaultValue: 'Milad')
    }
    stages {
        stage('Hello') {
            steps {
                echo "Hello $params.x"
            }
        
        }
    }
}
```

این کد یک Jenkins pipeline ساده را نشان می‌دهد که یک پارامتر رشته‌ای به نام "x" با مقدار پیش‌فرض "Milad" تعریف کرده و در یک مرحله به نام "Hello" از این پارامتر استفاده می‌کند. الگوی کلی این pipeline به صورت زیر است:

1. `agent any`:
  
   این نشان می‌دهد که فایل Jenkinsfile می‌تواند بر روی هر agentی که در دسترس است اجرا شود.

4. `parameters`:
  
 در این بخش، یک پارامتر با نام "x" به عنوان یک رشته (string) با مقدار پیش‌فرض "Milad" تعریف شده است.

7. `stages`:
  
 این بخش حاوی مراحل اصلی اجرای pipeline است.

10. `stage('Hello')`:
   
 یک مرحله به نام "Hello" تعریف شده است.

13. `steps`:
   
 در این بخش، مراحل اجرایی مرحله "Hello" قرار دارد.

16. `echo "Hello $params.x"`:
   
 با استفاده از دستور `echo`، پیام "Hello Milad" یا مقدار دلخواه وارد شده بر اساس مقدار پارامتر "x" چاپ می‌شود. 

به عبارت دیگر، این pipeline یک پیام خوشامد به نامی (که از طریق پارامتر "x" ارائه می‌شود) چاپ می‌کند. زمانی که این pipeline اجرا می‌شود، Jenkins از کاربر مقدار جدیدی برای پارامتر "x" بپرسد و سپس مرحله "Hello" اجرا شود.


### 'rebuild'
از دفعه اول به بعد وقتی میخواهیم دوباره بیلد کنیم بهمون یک صفحه نشان میدهد که میتوانیم پارامتر را عوض کنیم .
![image](https://github.com/milad6745/jenkins/assets/113288076/4279caf2-a5e8-4959-815b-af4458e71df3)

## `bolean parameter`

در اینجا یک پارامتر بولین مشاهده میکنیم 
```
pipeline {
    agent any
    parameters {
        string(name: "x", defaultValue: 'Milad')
        booleanParam(name: 'Enable', defaultValue: true)
    }
    stages {
        stage('Hello') {
            steps {
                echo "Hello $params.x"
                echo "this is $params.Enable"
            }
        
        }
    }
}
```
که پس از build کردن اینگونه نمایش داده میشود 
![image](https://github.com/milad6745/jenkins/assets/113288076/d0ce0b7b-43d0-409d-bbeb-97e3d3ccd9cc)

