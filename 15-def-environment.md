در Jenkins Pipeline (Jenkinsfile)، `def` یک کلمه کلیدی استفاده می‌شود برای تعریف متغیرها (variables) یا توابع (functions). این کلمه به شما اجازه می‌دهد تا یک نام و یک مقدار (برای متغیرها) یا یک نام و یک بلوک کد (برای توابع) را مشخص کنید.



در این مثال، یک تابع به نام `myFunction` بدون پارامتر تعریف شده است. در بلوک تابع می‌توانید دستورات متفاوتی اضافه کنید.

از `def` معمولاً در Jenkins Pipeline برای تعریف متغیرها و توابع در سطح اسکریپت یا یک بخش از کد استفاده می‌شود. این کلمه نه تنها برای متغیرها و توابع کلی سطح اسکریپت بلکه می‌تواند در بلوک‌های محدودتر مانند بلوک‌های `script` نیز استفاده شود.

مثال:

```groovy
pipeline {
    agent any
    stages {
        stage('Example') {
            steps {
                script {
                    def localVar = 'Local variable'
                    echo "Local Variable: ${localVar}"
                }
            }
        }
    }
}
```

در این مثال، `def` برای تعریف یک متغیر محلی (`localVar`) درون بلوک `script` استفاده شده است.


# `environment`

با این کار متغیرمان را در محیط گلوبال تعریف کردیم تا بتوانیم در تمامی stage ها ازش استفاده کنیم و محدود به یک stage نباشد .
```
pipeline {
    agent any
    environment {
        globalVar = 'Global variable'
    }

    stages {
        stage('Example') {
            steps {
                script {
                    echo "Global Variable: ${globalVar}"
                }
            }
        }
    }
}
```
