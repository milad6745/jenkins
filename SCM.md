
**پروژه Flask:**

ابتدا فایل های زیر را ایجاد کرده و سپس به git push میکنیم .

1. **فایل app.py:**
   ```python
   from flask import Flask

   app = Flask(__name__)

   @app.route('/')
   def home():
       return 'Hello, this is a simple Flask app!'

   if __name__ == '__main__':
       app.run(debug=True)
   ```

2. **فایل requirements.txt:**
   ```
   Flask==2.1.0
   ```

3. **فایل tests/test_app.py:**
   ```python
   from app import app
   import pytest

   @pytest.fixture
   def client():
       with app.test_client() as client:
           yield client

   def test_home(client):
       response = client.get('/')
       assert b'Hello, this is a simple Flask app!' in response.data
   ```

4. **ساختار دایرکتوری:**
   ```
   myflaskapptests/
   ├── app.py
   ├── requirements.txt
   ├── tests/
   │   └── test_app.py
   ```
سپس در جنکینز یک پایپ لاین ایجاد کرده و لینک گیت مان را میدهیم .

2. **تنظیم Jenkins:**
   - ایجاد یک Job جدید در Jenkins.
   - تنظیم SCM (Git) برای پروژه.
   - انتخاب "Pipeline script from SCM" در بخش "Pipeline" و تنظیم مخزن Git و Jenkinsfile.


![image](https://github.com/milad6745/jenkins/assets/113288076/b5a7a4f8-8d20-45c8-8923-f10f9060a86d)


کردنشیالمان همان نام کاربر و پسورد گیت است که در صورتی که پروژه provate باشد نیاز است تا آن را اعمال کنیم .
