##`متغیر محلی`

در اینجا یک متغیر محلی تعریف کردیم


```
pipeline {
    agent any
    environment {
        Name = "Milad"
    }
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('hi') {
            steps {
                echo 'Hello Name'
            }
        }
    }
}
```

##`متغیر محیطی`
حال ما میخواهیم برای یکی از استیج هایمان یک متغیر تعریف کنیم . دقت شود که در صورتی که برای یک استیج متغیر تعریف میکنیم برای ایتیج دیگر قابل استفاده نمیباشد .

```
pipeline {
    agent any
    stages {
        stage('Hello') {
            environment {
                Name = "Milad"
                }
            steps {
                echo "Hello $Name"
            }
        
        }
    }
}
```
