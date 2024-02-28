# `jenknis tomcat Deploy`

در این پست، قصد داریم به مرور مراحل مورد نیاز برای پیکربندی جنکینز و تامکت (Tomcat) و دستیابی به ادغام پیوسته (Continuous Deployment) و یکپارچه‌سازی پیوسته (Continuous Integration) بپردازیم. نحوهٔ استقرار جنکینز و تامکت.

قصد داریم ببینیم چگونه کد را از مخزن مدیریت کد منبع GitHub استخراج کرده و آن را در سرور برنامه تامکت (کانتینر سرویس‌دهی Servlet) استقرار دهیم. این شامل تمام پیکربندی‌های مورد نیاز در انتهای جنکینز و تامکت است.

هدف نهایی ما ادغام جنکینز و تامکت و نحوهٔ استقرار برنامه در تامکت با استفاده از جنکینز می‌باشد. استقرار جنکینز و تامکت.


## `پیکربندی و نصب تامکت (Tomcat)`


```
apt install wget unzip default-jdk
wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.86/bin/apache-tomcat-9.0.86-windows-x64.zip
unzip apache-tomcat-9.0.86-windows-x64.zip
mkdir /opt/tomcat
cp -rp apache-tomcat-9.0.86-windows-x64 /opt/opmcat
```

## change port tomcat
```
cd /opt/tomcat/apache-tomcat-9.0.86/conf#
nano server.xml
 <Connector port="9090" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443"
               maxParameterCount="1000

cd cd /opt/tomcat/apache-tomcat-9.0.86/bin#
chmod +x *
./startup.sh
```


## `Update Roles and User credentials - Configuring Tomcat Security`

بروید به دایرکتوری $CATALINA_HOME/conf و فایل tomcat-users.xml را پیدا کنید.

فایل را با ویرایشگر مورد علاقه‌تان مانند VI یا nano باز کنید و خطوط زیر را درست قبل از آخرین خط اضافه کنید:

```xml
<user username="tomcatmanager" password="password" roles="manager-gui"/>
<user username="deployer" password="password" roles="manager-script"/>
```

در اینجا دو نام کاربری به نام‌های tomcatmanager و deployer ایجاد می‌کنیم. حساب deployer برای استقرار فایل WAR از طریق HTTP استفاده می‌شود.

کاربر tomcatmanager مبتنی بر manager-gui برای مدیریت برنامه وب مدیر را در http://<نام‌میزبان>:8080/manager استفاده خواهد شد.

توجه*: اگر از نسخه ۸ به بالاتر از تامکت استفاده می‌کنید، مراحل فعال‌سازی برنامه مدیر ممکن است متفاوت باشد. در صورت بروز مشکل، به مستندات نسخه‌ی خاص محصول مراجعه کنید.

حالا ما با سرور برنامه تامکت (سرویس گیرنده Servlet) آماده هستیم و آن آماده است که از جنکینز متصل شود.

## `Make Sure you have Git and Maven installed`

در رابط کاربری جنکینز، به بخش "Manage Jenkins" بروید، سپس به قسمت "Global Tool Configuration" جنکینز بروید.

توجه*: اگر گزینه "Manage Jenkins" را نمی‌بینید، باید با مدیر خود مشاوره کنید. این ممکن است به دلیل مجوزهای ناکافی باشد.

## `Install Deploy to Container Plugin.`
"Manage Jenkins" -> "Manage Plugins" -> "Available" -> "Deploy to Container Plugin"

![image](https://github.com/milad6745/jenkins/assets/113288076/d117c9cf-9ecf-441b-8774-87dae49308f8)


"Jenkins Tomcat"

توجه*: برای مرحله بعدی، یک کار Maven را به عنوان انتخاب خود انتخاب کرده‌ایم. شما همچنین می‌توانید یک پروژه Free Style ایجاد کنید و از Gradle یا Ant به عنوان ابزار ساخت استفاده کنید.



## `Create and Configure a Maven Job with Source Code Management (Github)`


"New Item" -> "Maven Project"

در بخش پیکربندی، در زیر "Source Code Management"، آدرس مخزن Github/BeanStalk/Gitlab خود را وارد کنید.

برای تست، می‌توانید از یک برنامه نمونه به نام "Tomcat Maven App" از مخزن عمومی Github ما استفاده کنید.

شما می‌توانید از این مخزن GITHUB استفاده کنید

روی دکمه "Add" کنار با منوی کشویی اطلاعات اعتبار وارد شده و نام کاربری و گذرواژه مخزن SCM خود را وارد کنید. وقتی ذخیره شد، این اطلاعات برای شما در منوی کشویی قابل انتخاب خواهد بود.

پس از انتخاب اعتبارهای معتبر، چند ثانیه منتظر بمانید. اگر هر گونه پیام خطا با رنگ قرمز مشاهده کنید، این به معنای عدم موفقیت اتصال به مخزن SCM است. آدرس یا اطلاعات اعتبار را بررسی کرده و دوباره تلاش کنید.

![image](https://github.com/milad6745/jenkins/assets/113288076/d3fc3df8-39c2-4289-8bbe-4d7320ea1e54)


## ` Configure the Post-build Action and Specify the Tomcat Server Details`

کشیده و به پایین بروید و به بخش "Post-build Actions" بروید.

روی دکمه "Add post-build action" کلیک کنید.

در گزینه‌های موجود، روی "Deploy war/ear to container" کلیک کنید.

پارامترهای مورد نیاز برای افزونه را پر کنید. از تصویر صفحه به عنوان مرجع استفاده کنید.

مسیر Context را که برنامه در آن نصب شود، انتخاب کنید. این باعث تغییر نام فایل WAR قبل از استقرار در سرور می‌شود و در نتیجه ریشه محل برنامه تغییر می‌کند.

آدرس URL تامکت: http://[نام‌میزبان سرور تامکت]:[پورت اصلی HTTP]/


![image](https://github.com/milad6745/jenkins/assets/113288076/feef0393-dee4-41b9-8d1d-d2f5ebdb2526)

## `Build jenkins Job`
Execute the Job you have created by clicking on the Build Now button

![image](https://github.com/milad6745/jenkins/assets/113288076/082024c1-fda2-4236-8a83-d561ce5761ea)




## `Test Application`


پس از اتمام استقرار و اجرای موفقیت‌آمیز کار جنکینز بدون مشکل (یا حداقل این گمان را می‌کنم)، بیایید برنامه خود را تست کنیم.

در مورد من، URL باید به شکل زیر باشد:

http://192.168.0.107:8081/TomcatMavenApp



![image](https://github.com/milad6745/jenkins/assets/113288076/f3512a72-c1ae-4103-80f0-67abdbff9ff7)



