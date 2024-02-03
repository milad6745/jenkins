##`system configure`

Dashboard > Manage Jenkins > System


- Generic Webhook Trigger Whitelist 

برای وایت لیست کردن دسترسی به jenkins


- excuter

معالد رانر در گیت لب . بسته به منابع که داریم میتونیم افزایش بدهیم .
وقتی پایپ لاین اجرا میشه واقعن باید در جایی اجرا شود .
در Jenkins، مفهوم "Executor" به اجرا کننده‌هایی اشاره دارد که وظیفه اجرای جاب‌ها (Jobs) یا پروسه‌های اجرایی را بر عهده دارند. Executors مسئول اجرای بندهای مختلف کاری در Jenkins هستند و هر یک از آنها یک فرآیندهای اجرایی (process) مجزا را در سیستم می‌نمایند.



Dashboard > Manage Jenkins > Nodes >  Built-In Node > Configure

داخل کانفیگ bultin Node همان نودی که داخلش هستیم، میتوانیم لیبل بزنیم که فلان لیبل ها را فقط اجرا کن - چون مستر نود ما هست .





Dashboard > Manage Jenkins > Nodes

در Jenkins، مفهوم "Node" به محیط یا سروری اشاره دارد که وظیفه اجرای بندهای کار (Job) را بر عهده دارد. هر Node می‌تواند دارای یک یا چندین Executor باشد که به صورت همزمان بر روی آن اجراها انجام شود. 
این نودها به صورت مجازی یا فیزیکی در ساختار شبکه Jenkins قرار می‌گیرند و می‌توانند بر روی یک سرور محلی یا سرورهای از راه دور (remote) باشند.
در جنکینز دو نوع نود Master , Slave داریم .
ما Node هایمان را میتوانیم در Cloud هم ایجاد کنیم Ec2 - Kuber - Docker , ...


Dashboard > Manage Jenkins > Tools
ددر اینجا tools هایی که الان نصب است میتوانیم کانفیگ کنیمم.
مثل انسیبل - داکر - kubernetes - teraform - ...

