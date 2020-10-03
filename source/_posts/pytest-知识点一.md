---
title: pytest 知识点
date: 2020-07-13 22:16:24
tags:
- 知识点
- 测试开发
- pytest
---
<br>

### 【测试用例的识别】
>    测试文件
        &emsp;&emsp;test_*.py
        &emsp;&emsp;*_test.py
    用例识别
        &emsp;&emsp;Test*类包含的所有test_*的方法(测试类不能带有init方法)
        &emsp;&emsp;不在class中的所以test_*方法
    pytest 也可以执行unittest框架写的用例以及方法

 ### 【测试用例的运行】
 >   pytest /包名 执行包下所有用例
    pytest -v 打印详细运行日志信息
    pytest -s s 是带控制台输出结果，也是输出详细
    pytest -k "add" 匹配所有名称中包含add的用例， 可以使用and or not 等逻辑运算
    pytest -m [标记名]  @pytest.mark.[标记名] 将运行有标记名的测试用例
    pytest -x 文件名 一旦运行到报错就停止运行
    pytest -maxfile = [num] 错误带到num时停止运行
    pytest 文件名::(类名)::(方法名)


 ### 【pytest 框架结构】
 >   import pytest 类似的setup,teardown同样更灵活，l
    模块级(setup_module/teardown_module)模块始末，全局的（ 优先最高 ）
    函数级(setup_function/teardown_function)只对函数用例生效(不在类中)
    类级(setup_class/teardown_class)只在类中前后运行一次（在类中）
    方法级(setup_method/teardown_methond)开始于方法始末（在类中）
    类里面的（setup/teardown）运行在调用方法的前后
    setup_class() setup() teardown() setup() teardown() tear_down()
    类外面的叫函数 类里面的叫方法

### 【fixture】
>    在测试函数运行前后，由pytest执行的外壳函数。fixture是pytest用于将测试前后进行预备、清理工作的代码分理处核心测试逻辑的一种机制
    功能：
        &emsp;&emsp;定义传入测试中的数据集
        &emsp;&emsp;配置测试前系统的初始状态（类似setup）
>        &emsp;&emsp;为批量测试提供数据源
>
>    在方法上面加@pytest.fixture(autouse=True) 该方法作为login使用在下面
>     @pytest.make.usefixture("login")
>    此方法可作为变量传入其他方法，被调用
>
>    fixture里面有scope可以控制fixture终作用范围   session>moudle>class>function(默认)
>
>    也可以用require以及param 传参

### 【参数化parametrize】
>    可读性：
        &emsp;&emsp;ids： 增加可读性
        &emsp;&emsp;自定义id pytest.param(1,2,3,id="用例名")
    结合yaml实现参数化
        &emsp;&emsp;@pytest.mark.parametrize('a,b,result', yaml.safe_load(open("../datas/cal.yml")))(需要yaml为list最好)
        &emsp;&emsp;@pytest.mark.parametrize('a,b,result', [
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(1,1,2),
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(0.1,0.1,0.2),
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(1000,2000,3000),
            &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(-1,-1,-2)
        ])
    组合数据 笛卡尔积：
        &emsp;&emsp;@pytest.mark.parametrize('a' , [1,2,3])
        &emsp;&emsp;@pytest.mark.parametrize('b' , ['a', 'b'])
        &emsp;&emsp;使用a 和 b 将生成六组数据
    跳过: @pytest.mark.skip @pytest.mark.skipif
    存在未知问题：@pytest.mark.xfail

### 【yaml】
```js
    数据参数化
        list
          - 10
          - 20
        dict:字典
          by: id
          locator: name
      #嵌套，二维数组
        -
         - by: id
          - locator: name

```



