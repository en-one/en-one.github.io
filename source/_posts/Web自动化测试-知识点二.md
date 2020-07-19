---
title: Web自动化测试 知识点二
date: 2020-07-13 22:49:58
tags:
- 知识点
- 测试开发
- python
---
<br>

### 【动作链接ActionChains】
>   &emsp;action = ActionChains(self.driver)
    &emsp;将动作放入队列里执行
    &emsp;action.perform()
    &emsp;动作
    &emsp;&emsp; 点击    ·action.click(element_click)
    &emsp;&emsp; 右击    action.context_click(element_right_click)
    &emsp;&emsp; 双击    action.double_click(element_double_click)
    &emsp;&emsp; 移动     action.move_to_element(ele)
    &emsp;&emsp; 输入框填写     action.send_keys("josiah") 可用KEYS.Space 模拟空格以及其他操作

### 【滑动链接ActionChains】
>   &emsp;action = TouchActions(self.driver)
    &emsp;将动作放入队列里执行
    &emsp;action.perform()
    &emsp;动作
    &emsp;&emsp; 滑动  action.scroll_from_element(el, 0 ,10000).perform()

### 【页面跳转】
>    &emsp;获取下一个页面id,将当前页指到下一个目录页
    &emsp;&emsp; windows = self.driver.window_handles
    &emsp;&emsp; self.driver.switch_to_window(windows[-1])

### 【frame跳转】
>   &emsp;&emsp; driver.switch_to.frame("")  元素id或者默认index
>   &emsp;&emsp;  driver.switch_to.default_content()
>   &emsp;&emsp; driver.switch_to.parent_frame() 切换到父级frame

### 【执行script 脚本】
>   &emsp;&emsp; driver.execute_script("js代码")


### 【pageObject】
>  &emsp;原则解读
   &emsp;&emsp;方法意义
    &emsp;&emsp;&emsp;&emsp;用公共方法代表UI所提供的功能
    &emsp;&emsp;&emsp;&emsp;方法应该返回其他的PageObject或者返回用于断言的数据
    &emsp;&emsp;&emsp;&emsp;同样的行为不同的结果可以建模为不同的方法
    &emsp;&emsp;&emsp;&emsp;不要在方法内加断言
    &emsp;&emsp;字段意义
    &emsp;&emsp;&emsp;&emsp;不要暴露页面内部的元素给外部
    &emsp;&emsp;&emsp;&emsp;不需要建模UI内的所有元素


### 【刚开始编写用例顺序】
>   &emsp;&emsp;根据界面封装po类与方法，实现暂时设置为空
    &emsp;&emsp;编写用例
    &emsp;&emsp;实现page内的方法，与自动化框架开始结合
    &emsp;&emsp;调试
    &emsp;&emsp;创建base_page，把所有公共的方法进行封装

