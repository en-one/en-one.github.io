---
title: Web自动化测试 知识点一
date: 2020-07-13 22:49:50
tags:
- 知识点
- 测试开发
- python
---
<br>
### 【Seleium 测试用例编写】
>    &emsp;导入依赖
        &emsp;&emsp;from selenium import webdriver
     &emsp;创建driver
        &emsp;&emsp;self.driver = webdriver.Chrome()
        &emsp;&emsp;self.driver.get("https://work.weixin.qq.com/wework_admin/frame#index")
     &emsp;执行自动化步骤
     &emsp;断言

### 【三种等待】
>   直接等待
        &emsp;time.sleep(3)
    隐师等待
        &emsp;self.driver.implicitly_wait(3)
            &emsp;&emsp;轮训(默认0.5)查找 ,时间结束没出现就抛出异常
            &emsp;&emsp;缺点 全局的
   显式等待
        &emsp;webDriverWAit
            &emsp;&emsp;在代码中定义条件，当条件发生时才继续2执行代码(代码可为自定义函数，早定义函数一定要有参数)
            &emsp;&emsp;轮训(默认0.5)判断，条件成立，执行下一步，否则继续等待 直到超过设置的最长时间
            ```python
                #eg:每0.5轮询wait函数 返回true 则执行下一句
                def wait(x):#wait 默认传一个函数
                    return self.driver.find_element(By.XPATH, '//*[@title="有了新帖的活动主题"]')
                WebDriverWait(self.driver, 10).until(wait)
                self.driver.find_element(By.XPATH, '//*[@title="在最近的一年，一月，一周或一天最活跃的主题"]').click()
            ```
                
### 【web控件定位-xpath】
xpath:

         /	定位到孩子。
        //	定位到子子孙孙。
        //* 选取文档中多有节点
        @	选取属性。
        $x('//*[@id="s_tab"]//a[1]') 选取id为s_tab下的第一个a表情

&emsp;css selector：(常用语手机中嵌套的webview)

       . class
       # id
        * 所有元素
        div,p div和p元素
        div p div内部所有p(相当于//)
        div>p div的儿子元素p(相当于/)
        div+p div之后的p
        P:nth-child(2) 选择淇父元素第二个子元素的所有p
        $(#s_tab a:nth-child(2)) 表示a 的父元素下第二个标签
   ```python
 #点击 self.driver.find_element(By.ID, 'kw').click()
    #输入框输入 self.driver.find_element(By.ID, 'kw').send_keys("josiah") 
```
