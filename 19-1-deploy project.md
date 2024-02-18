# `Deploy`
برای deploy کردن پروژه میبایست ابتدا مرحله فایل 19 را انجام داده سپس خروجی jar که در کنسول میبینیم را اجرا کنیم .

![image](https://github.com/milad6745/jenkins/assets/113288076/59466f49-3adf-46d8-aefc-c7be2d92537e)

```
/var/jenkins_home/workspace/maven01/maven-samples/single-module/target/single-module-project.jar
```
برای اجرا کردن این خروجی یه add build أیگه میکنیم و این اسکریپت را اینگونه اجرا میکنیم .

![image](https://github.com/milad6745/jenkins/assets/113288076/98795180-ccf8-4f67-bf97-a4fbe9215fcd)

دقت شود که به جای /var/jenkins_home/workspace/maven01  از $WORKSPACE استفاده شده است .


که مطابق شکل خروجی نمایش داده میشود.
![image](https://github.com/milad6745/jenkins/assets/113288076/49707f3c-11fc-4432-9852-ee01633bffca)




# `report directory`
مشاهده میشود در build ای که برای تست و اینستال انجام شد report directory  داخل این دایرکتوری قرار گرفته است که باهاش کار داریم .

![image](https://github.com/milad6745/jenkins/assets/113288076/34c8116a-4a6e-487d-9be5-0af67bc45a79)

مشاهده میشود که در مسیر زیر یک سری فایل Xml داریم .

```
cd /var/jenkins_home/workspace/maven01/maven-samples/single-module/target/surefire-reports
root@b6aac95e4b2b:/var/jenkins_home/workspace/maven01/maven-samples/single-module/target/surefire-reports# ls
TEST-com.example.TestGreeter.xml  com.example.TestGreeter.txt
```

حالا یک post build تعریف میکنیم و مسیر تمامی فایل های xml را بهش می دهیم و با * مشخص میکنیم که تامامی ریپورت ها را بخواند .

![image](https://github.com/milad6745/jenkins/assets/113288076/9200c052-f0d5-459c-8eac-76d5d0f3d2d0)



ومشاهده میشود که تمامی تست ها پاس شده است .

![image](https://github.com/milad6745/jenkins/assets/113288076/93ceed19-2fba-46fd-bc10-8008aab3eb84)



