برای اجرای یک stage خاص فقط در برنچ مستر (master)، می‌توانید از متغیرهای محلی در Jenkins Pipeline به نام `BRANCH_NAME` یا `CHANGE_BRANCH` استفاده کنید. در زیر یک مثال از چگونگی این کار آمده است:

```groovy
pipeline {
    agent any
    
    stages {
        stage('Mystage') {
            when {
                expression { return BRANCH_NAME == 'master' }
            }
            steps {
                echo 'Running the stage only on the master branch...'
            }
        }

    }
}
```

در این مثال، `when` با استفاده از `expression` بررسی می‌کند که آیا متغیر `BRANCH_NAME` برابر با 'master' است یا نه. اگر این شرط برقرار باشد، مرحله مشخص شده اجرا می‌شود، و در غیر این صورت، نادیده گرفته می‌شود.

توجه داشته باشید که `BRANCH_NAME` می‌تواند توسط Jenkins به عنوان متغیری در اختیار شما قرار گیرد که نام برنچ فعلی را نشان می‌دهد. این متغیرها بسته به تنظیمات Jenkins ممکن است تغییر کنند، لذا بهتر است مستندات Jenkins خود را بررسی کنید یا با مدیر Jenkins خود تماس بگیرید تا اطمینان حاصل کنید که نام متغیر درست استفاده شده است.
