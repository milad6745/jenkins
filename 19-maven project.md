# `maven project`

میخواهیم یک پروژه Maven را در جنکینز اجرا کنیم .
نمونه پروژه را از لینک زیر استفاده کرده و در جنکینز کپی میکنیم .

(https://github.com/pistaacademy/maven_sample_project)

سپس یک جاب با لینک گیت زیر در جنکینز ایجاد میکنیم .

![image](https://github.com/milad6745/jenkins/assets/113288076/ac30edcd-803e-4a3d-ade6-ab0d4079df38)

سپس در قسمت Build Steps گزینه Invoke top-level Maven targets را انتخاب میکنیم . سپس در قسمت Goal میبایست هدفمان را از ایجاد این پایپ لاین بگوییم پیرو داکیومنت زیر :


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


![image](https://github.com/milad6745/jenkins/assets/113288076/9b2e2a69-4b3b-4043-854f-4efb6d10b50a)
