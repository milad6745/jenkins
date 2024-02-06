
# `retry`
وقتی میخواهیم یک اسکریپت برای تعداد بار مشخص تکرار شود تا موقعی که به جواب برسد و از برنامه خارج شود از retry استفاده میکنیم .
در اینجا سه ثانیه منتظر میماند و سپس دوباره اسکریپت را اجرا میکند.

```
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                retry(5) {
                    sleep(3)
                    sh 'false'
                }
            }
        }
    }
}
```

![image](https://github.com/milad6745/jenkins/assets/113288076/f63124f2-4bc1-4a76-855f-a059365f5702)
