---
title: js 使超链接变灰失效
date: 2020-06-16 14:14:16
tags:
- 知识点
- 前端
- js
---
1.需求
~~~
报名已截止的活动，修改按钮灰色，不可点击
~~~

2.实现方式
```yaml
//需要变灰的按钮添加 class的动态变量 edit_grey

- {model: btn, type: link, hide_label: false, content: " 修改", class_name: "{{edit_grey}}"}
```
~~~js
//通过css设置超链接 变灰以及不可点击

window.onload = function getGrey() {
    setTimeout(getGrey,2)//④
    var edit_object = document.getElementsByClassName("edit_grey");
    for (x in edit_object) {
        edit_object[x].style = "color:grey;pointer-events: none;"
    }
}
~~~
3.效果

![NFP4Fe.png](https://s1.ax1x.com/2020/06/16/NFP4Fe.png)

4.遇到问题

> 频繁以及快速刷新造成edit_object不能找到对应变量，添加一个两秒的定时器再度调用

5.注意
> 对应按钮修改css后，记得修改对应接口
    

