# 'trigger from webhook'
ما میخواهیم پایپ لاینی بنویسیم که توسط webhook اجرا شود و بدون استفاده از محیط گرافیکی :
در مرحله اول پایپ لاینمون را مینویسیم .
در اینجا ما یک دلیل برای وب هوک و یک وکن تعریف میکنیم که بتوانیم از خارج از وب کنسول جنکینز آن را صدا بزنیم .

```
pipeline {
    agent any
    triggers {
        GenericTrigger(
            causeString: "running from webhook",
            token: "ABCDEFG"
        )    
    }            
    stages {
        stage('User Input') {
            steps {
                echo "User description"
            }
        }

    }
}
```

که پس از اجرا کردن در یک سرور لینوکسی
```
curl -I http://192.168.72.222:8080/generic-webhook-trigger/invoke?token=ABCDEFG
HTTP/1.1 200 OK
Date: Mon, 05 Feb 2024 19:20:00 GMT
X-Content-Type-Options: nosniff
Content-Type: application/json;charset=utf-8
Content-Length: 170
Server: Jetty(10.0.18)
```

![image](https://github.com/milad6745/jenkins/assets/113288076/feb0769a-9471-4322-9e58-12d959021831)
