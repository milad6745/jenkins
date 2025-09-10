

مثال ساده:

```groovy
pipeline {
    agent any

    stages {
        stage('Run Bash Script') {
            steps {
                sh '''
                    echo "Starting script..."
                    date
                    ls -l
                    echo "Script finished!"
                '''
            }
        }
    }
}
```

🔹 نکته‌ها:

* داخل `sh ''' ... '''` می‌تونی هر دستور لینوکسی یا اسکریپت bash بذاری.
* برای دستورات تک‌خطی هم می‌تونی بنویسی:

```groovy
sh 'echo "Hello from bash"'
```

---

مثال با اجرای فایل اسکریپت:
فرض کنیم توی ریپوی خودت یه فایل به اسم `myscript.sh` داری.

`myscript.sh`:

```bash
#!/bin/bash
echo "Hello from myscript.sh"
```

پایپ‌لاین Jenkins:

```groovy
pipeline {
    agent any

    stages {
        stage('Execute Script File') {
            steps {
                sh 'chmod +x myscript.sh'
                sh './myscript.sh'
            }
        }
    }
}
```

---
