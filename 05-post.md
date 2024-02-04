# `POST`
بخش post در Jenkins Pipeline یک بخش اختیاری است که اجازه می‌دهد تا اقداماتی پس از اجرای pipeline انجام شوند بر اساس نتیجه حاصل از اجرای pipeline. این بخش شامل چند بلوک است که هرکدام بر اساس وضعیت خاصی از pipeline اجرا می‌شوند.

در بخش post، می‌توانید از بلوک‌هایی مانند always، success، failure و ... استفاده کنید. نحوه استفاده از این بخش به صورت زیر است:

در این پایپ لاین گفته شده که اگر فیلد داد این کار را کن و اگر موفق اجرا شد این کار را کن و در هر صورت (always) این پیام را نشان بده .

ش
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
            post {
                always {
                    echo 'This will always run'
                }
                failure { 
                    echo 'This will run only if the pipeline fails'
                }
                success {
                    echo 'this will susccessfully run this pipeline'
                }
            } 
        }
    }
}
```
