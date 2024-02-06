# `Archive`

با این دستور میتوانیم Archive کنیم . ابتدا یک فایل میسازیم و سپس آن را آرشیو میکنیم .
```
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo hi > test'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: '**/**'
        }
    }
}
```

```
view in http://192.168.72.222:8080/job/userby/61/artifact/test/*view*/
```
