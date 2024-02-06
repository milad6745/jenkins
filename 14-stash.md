
# `stash`
دستورات `stash` و `unstash` در Jenkins Pipeline برای آرشیو و بازیابی (Unstash) فایل‌ها به منظور انتقال آنها بین مراحل (stages) مختلف در یک Pipeline استفاده می‌شوند. این دستورات مفید هستند زمانی که نیاز به انتقال فایل‌ها (مثلاً فایل‌های سورس یا توابع تست) از یک مرحله به مرحله دیگر دارید.

در ادامه یک مثال از استفاده از `stash` و `unstash` در یک Jenkins Pipeline آورده شده است:

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // مرحله اول: آرشیو کردن فایل‌ها با stash
                script {
                    // آرشیو کردن فایل‌های سورس با stash
                    stash includes: 'src/**', name: 'myStash'
                }
            }
        }

        stage('Test') {
            steps {
                // مرحله دوم: بازیابی فایل‌ها با unstash
                script {
                    // بازیابی فایل‌های آرشیو شده با unstash
                    unstash 'myStash'
                    
                    // انجام تست‌ها یا هر عملیات دلخواه دیگر
                    sh 'ls -lah src/'
                }
            }
        }
    }
}
```

در این مثال:

1. در مرحله "Build"، فایل‌های موجود در دایرکتوری `src/` با دستور `stash` آرشیو شده و با نام `myStash` در Jenkins ذخیره می‌شوند.

2. در مرحله "Test"، فایل‌های آرشیو شده با دستور `unstash` بازیابی می‌شوند و می‌توانید عملیات‌های مورد نظر (مثلاً انجام تست‌ها) را انجام دهید.

به یاد داشته باشید که نام stash باید در مراحل مختلف یکسان باشد تا بتوانید فایل‌ها را بازیابی کنید.


## `Example`

این عملیات‌ها را در مراحل متوالی انجام دهید. در ادامه یک مثال از استفاده از `stash`، `unstash` و حذف (delete) در Jenkins Pipeline آورده شده است:

```groovy
pipeline {
    agent any
    stages {
        stage('Create and Stash File') {
            steps {
                script {
                    // ایجاد یک فایل به نام test.txt
                    writeFile file: 'test.txt', text: 'Hello, Jenkins!'
                    
                    // آرشیو کردن فایل با stash
                    stash includes: 'test.txt', name: 'myStash'
                }
            }
        }

        stage('Read Stashed File') {
            steps {
                script {
                    // بازیابی فایل آرشیو شده با unstash
                    unstash 'myStash'

                    // خواندن محتوای فایل
                    def fileContent = readFile 'test.txt'
                    echo "Content of the file: ${fileContent}"
                }
            }
        }
    }

    post {
        always {
            // حذف stash در پست (post)
            cleanWs()
        }
    }
}
```

در این مثال:

1. در مرحله "Create and Stash File"، یک فایل به نام `test.txt` ایجاد شده و سپس با دستور `stash` آرشیو شده و با نام `myStash` در Jenkins ذخیره می‌شود.

2. در مرحله "Read Stashed File"، فایل آرشیو شده با دستور `unstash` بازیابی می‌شود و محتوای آن فایل خوانده می‌شود.

3. در بخش `post` با دستور `cleanWs` محل ذخیره‌سازی فایل‌های Workspace پاک می‌شود. این دستور برای حذف فایل‌های موقتی و تمیز کردن Workspace استفاده می‌شود.

   ![image](https://github.com/milad6745/jenkins/assets/113288076/387692ba-092f-4beb-a597-c95adc016ad0)
که در اینجا وقتی میخواهیم  دو باره بیلد را ریستارت کنیم و ایتیج Create and Stash File را اسکیپ میکنیم میبینیم که چون در پست حذف شده است این ارور داده میشود که فایل موجود نیشت .

دستورات stash و unstash در Jenkins Pipeline برای مدیریت فایل‌ها (artifacts) در طول مراحل مختلف یک Pipeline مورد استفاده قرار می‌گیرند. این دستورات به شما این امکان را می‌دهند که فایل‌های مورد نیاز را بین مراحل مختلف انتقال دهید.
