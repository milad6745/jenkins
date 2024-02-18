# `maven project`

میخواهیم یک پروژه Maven را در جنکینز اجرا کنیم .
نمونه پروژه را از لینک زیر استفاده کرده و در جنکینز کپی میکنیم .

(https://github.com/anshulc55/Jenkins_Upgradev3.git)

سپس یک جاب با لینک گیت زیر در جنکینز ایجاد میکنیم . به دلیل اینکه پروژه پابلیک است نیاز به credential ندارد.

![image](https://github.com/milad6745/jenkins/assets/113288076/1442ecb1-7688-4624-95eb-01ad0b111c67)




سپس در قسمت Build Steps گزینه Invoke top-level Maven targets را انتخاب میکنیم . 
سپس در قسمت Goal میبایست هدفمان را از ایجاد این پایپ لاین بگوییم پیرو داکیومنت زیر 


![image](https://github.com/milad6745/jenkins/assets/113288076/2c93b749-ca8c-4f9f-8d42-f988ec7240d3)

به دلیل اینکه فایل pom.xml در روت پروژه قرار ندارد مسیر آنرا میدهیم .


![image](https://github.com/milad6745/jenkins/assets/113288076/76d0c804-0dc9-4a43-938c-95645c4fdaa4)



## ``A Build Lifecycle is Made Up of Phases``
Each of these build lifecycles is defined by a different list of build phases, wherein a build phase represents a stage in the lifecycle.

For example, the default lifecycle comprises of the following phases (for a complete list of the lifecycle phases, refer to the Lifecycle Reference):

`validate` - validate the project is correct and all necessary information is available

`compile` - compile the source code of the project

`test` - test the compiled source code using a suitable unit testing framework. These tests should not require the code be packaged or deployed

`package` - take the compiled code and package it in its distributable format, such as a JAR.

`verify` - run any checks on results of integration tests to ensure quality criteria are met

`install` - install the package into the local repository, for use as a dependency in other projects locally

`deploy` - done in the build environment, copies the final package to the remote repository for sharing with other developers and projects.

These lifecycle phases (plus the other lifecycle phases not shown here) are executed sequentially to complete the default lifecycle. Given the lifecycle phases above,
this means that when the default lifecycle is used, Maven will first validate the project, then will try to compile the sources, run those against the tests, package the binaries (e.g. jar)
run integration tests against that package, verify the integration tests, install the verified package to the local repository, then deploy the installed package to a remote repository.

![image](https://github.com/milad6745/jenkins/assets/113288076/37799710-7668-498a-a19e-dc5ce3b116f2)

## `result`
سپس پروژه را بیلد میکنیم و در قسمت کنسول مشاهده میکنیم که پروژه با موفقیت انجام شده است .

![image](https://github.com/milad6745/jenkins/assets/113288076/59466f49-3adf-46d8-aefc-c7be2d92537e)


