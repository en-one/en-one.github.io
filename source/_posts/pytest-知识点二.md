---
title: pytest 知识点增补
date: 2020-07-13 22:17:21
tags:
- 知识点
- 测试开发
- pytest
---
<br>

### 【自动化测试用例的设计基本原则】
>    变动小、尽量页面不要经常变动
    每一条测试用例尽量简单、尽量去覆盖一个基本的功能
    尽量不要有关联(可以吧资源放在setup里面)

### 【yield】
>    替代return 返回数据
    会回调用teardown 但是return 不会

### 【pytest常用插件】
>    第三方插件大多是改写装饰器，装饰器(>2)太多会有冲突
    【用例依赖】
        &emsp;&emsp;@pytest.mark.dependency(name='cart)
        &emsp;&emsp;@pytest.mark.dependency(depends=["cart"]) //cart可为pytestmark定义的依赖名 也可以为方法名

>    【pytest 执行顺序】
        &emsp;&emsp;pip install pytest-ordering 解决用例顺序
        &emsp;&emsp;@pytest.mark.run(order=2)
    【pytest 多线程】
        &emsp;&emsp;pip install pytest-xdist
        &emsp;&emsp;pytest -n 3

### 【conftest.py 】
>    常用：
        &emsp;&emsp;文件名不可以更换
        &emsp;&emsp;pytest用例会自动导入
        &emsp;&emsp;与用例在同一个package，会先查找同一目录级别下，然后向外
        &emsp;&emsp;文件存放一些公用方法
    用于定制化
        &emsp;&emsp;使用函数pytest_collection_modifyitems，命令要使用collect
        &emsp;&emsp;解决编码问题
        &emsp;&emsp;修改测试用例顺序
### 【pytest.ini】
>    pytest的主配置文件 一般放在项目工程目录里
    不能使用任何中文符号
    指定pytest的运行方式
        &emsp;&emsp;python_files 检测文件的规则
        &emsp;&emsp;python_classes 检测类的规则
        &emsp;&emsp;python_functions 检测函数的规则
>        &emsp;&emsp;addopts= -vs 改写运行时参数

### 【allurej基础】
>    java开发 可以集成到jenkins 轻量级、灵活的、支持多语言的测试报告工具

>    加上feature后
    feature 一个功能 大的模块
    story 一个功能或者模块下的不同场景，分之功能
    父子关系

>    @allure.feature("父模块")
    @allure.story("子模块")

>   pytest test_feature_story.py --allure-features '登录模块'   //只运行父模块
    pytest test_feature_story.py --allurl-stories '登陆成功' //只运行zi模块

>   运行整个
>   pytest test_feature_story.py --alluredir=.\result\6
    allure serve .\result\6\

