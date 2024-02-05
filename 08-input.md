# `input`
در اینجا میخواهمیم از کاربر در حین انجام stage یک ورودی بگیرد . مثلا فلان اتفاق افتاده آیا ادامه بهد یا خیر

```groovy
pipeline {
    agent any
    stages {
        stage('User Input') {
            input {
                message "Do you want to continue?"
                ok "YES"
            }
            steps {
                echo "run project"
            }
            
        }
    }
}
```
![image](https://github.com/milad6745/jenkins/assets/113288076/ff00d642-9521-4a8b-b740-d95946d25288)


### `Example`
در این پایپ لاین در مرحله شروع step از ما یک Description میپرسد و پس از وارد کردن ان وارد مرحله بعدی میشود .
```
pipeline {
    agent any
    stages {
        stage('User Input') {
            steps {
                input(
                    message: 'Enter a description about yourself',
                    parameters: [
                        text(name: 'USER_DESCRIPTION', defaultValue: '', description: 'Description')
                    ]
                )
                echo "User description"
            }
        }
    }
}
```
![image](https://github.com/milad6745/jenkins/assets/113288076/301c4191-8753-43c8-b399-7e21bdff2bbe)
