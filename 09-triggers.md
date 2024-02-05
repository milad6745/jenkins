
### `triggers`
حالا ما میخواهیم بدون استفاده از محیط گرافیکی کرون را فعال کنیم از triggers استفاده میکنیم .
```
pipeline {
    agent any
    triggers {
        cron "* * * * *"
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
پس از آن مشاهده میکنیم که در قسمت گرافیکی بعد از اولین بار build کردن خودش کرون را قرار میدهد .

![image](https://github.com/milad6745/jenkins/assets/113288076/1590b59e-5878-4431-ab12-9ff2001ca640)
