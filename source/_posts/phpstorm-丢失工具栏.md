---
title: phpstorm 丢失工具栏
date: 2020-03-29 21:25:00
tags:
- 知识点
- windows
- ide
---
<br>

### 【在优化编辑器时，弄丢了ide主菜单栏!】
- 方法一： 修改配置文件
> 一般存在在路径c盘中 我的位置：C:\Users\Administrator\.PhpStorm2019.3\config\options    
> 修改 ui.lnf
```php
//使value值为true，若没有，则添加
<option name="SHOW_MAIN_MENU" value="true" />
//添加后，重启

```

- 方法二：快捷键设置
> 双击shft   
> 选择 view ，出现操作栏                            
> 恢复选择 appearance>main menu

<br>

 ### 【丢失项目栏】
 > 快捷键alt + 1