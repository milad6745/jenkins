# `timeout
در اینجا ما میخواهیم زمان اجرای اسگریپت بیشتر از 10 ثانیه طول نکشد و اگر کشید از پایپ لاین خارج شود .

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                timeout(time: 10, unit: "SECONDS"){
                sleep(15)
                }
            }
        }
    }
}
```

![image](https://github.com/milad6745/jenkins/assets/113288076/3578c361-a860-4b13-ab2b-6f033521b829)
