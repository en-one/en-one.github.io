---
title: 单元测试以及unittest
date: 2020-06-29 22:19:58
tags:
- 知识点
- 单元测试
- unittest 
---

<br>

### 【单元测试】
>    定义：
        &emsp;&emsp;单元测试是开发这编写的一小段代码，用于检验被测代码的一个很小的、很明确的功能是否正确。一个单元测试适用于判断某个特定条件下某个特定函数的行为
    注意：
        &emsp;&emsp;需要清楚的知道自己要测试的程序所预期的输入和输出，然后根据这个预期逻辑写case

### 【单元测试框架】
>    Unittest：
        &emsp;&emsp;Python内置的标准类库
    pytest  
        &emsp;&emsp;丰富灵活的测试框架、语法简单、结合allure生成炫酷的测试报告

### 【单元测试覆盖率】
>    代码覆盖率也被用于自动化测试和手工测试来度量测试是否全面的指标之一
    单元测试覆盖类型
        &emsp;&emsp;语句覆盖
            &emsp;&emsp;&emsp;&emsp;保证被测试的方法每一行代码都会被执行一遍
            &emsp;&emsp;&emsp;&emsp;运行测试用例时被击中的代码行为覆盖的语句
            &emsp;&emsp;&emsp;&emsp;漏洞：and或者or
        &emsp;&emsp;条件覆盖
            &emsp;&emsp;&emsp;&emsp;和判断类似，不过判断关注整个判定语句，而条件覆盖则关注某个判断条件
            &emsp;&emsp;&emsp;&emsp;漏洞：  测试用例指数级增长
        &emsp;&emsp;判断覆盖
            &emsp;&emsp;&emsp;&emsp;运行测试用例的过程被击中的为判定语句
            &emsp;&emsp;&emsp;&emsp;漏洞：大部分判定语句为多个逻辑组成的，仅判断整体的true或者false，忽略每个条件的取值情况
        &emsp;&emsp;路径覆盖
            &emsp;&emsp;&emsp;&emsp;覆盖所有可能执行的路径


### 【unittest】
>    setUpClass 所有测试用例执行前，最开始 @classmethod要加
    tearDownClass 最后，其余同上
    setUp 每个测试用例执行前都执行一遍
    tearDown 执行后
    跳过改测试用例 @unittest.skipIf(1+1==2,"跳过")
    unittest 测试断言

### 【unittest编写与规范】
>    测试模块首先impoort unittest
    测试类必须集成unittest.TestCase
    类名：最好Test开头 驼峰
    测试方法必须以test_开头

### 【unittest测试套件】
>    执行所有
        &emsp;&emsp;unittest.main() 
    加入容器中执行
        &emsp;&emsp;suite=unittest.TestSuite()
        &emsp;&emsp;suite.addTest(TestMethod("test_01"))
        &emsp;&emsp;suite.addTest(TestMethod("test_02"))
        &emsp;&emsp;unittest.TextTestRunner().run(suite)
    执行某个测试类
        &emsp;&emsp;suite1 = unittest.TestLoader().loadTestsFromTestCAse(TestSEearchq)
        &emsp;&emsp;suit = unittest.TestSuite(suite1)
        &emsp;&emsp;unittest.TextTestRunner().run(suite)
    
### 【测试用例执行国产】
>    写TestCase
    用TestLoader加载TestCAse到TestSuite
    用TextTESTRunner运行testSuite
    结果保存在TextTestResult中
    整个过程集成在unittest.main中

