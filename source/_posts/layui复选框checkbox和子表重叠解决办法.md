---
title: layui复选框checkbox和子表重叠解决办法
date: 2020-06-09 14:53:11
tags:
- 知识点
- 前端
- layui
---



![t51IgJ.png](https://s1.ax1x.com/2020/06/09/t51IgJ.png)


代码如下:

```php
  cols: [[
                {type: 'checkbox', fixed: 'left'}
                , {field: 'account', title: '学号'}
                , {field: 'name', title: '姓名'}
                , {field: 'mobile', title: '手机号'}
                , {field: 'grade_name', title: '年级'}
            ]]
            ,
```

解决方法:
> 去掉fix字段, 如下：
> {type: 'checkbox'} 

> 修改layui源码CSS中z-index=-1，如下：
.layui-table-fixed { position: absolute; left: 0; top: 0; z-index: -1; }

---

- *借鉴文章* [链接](https://github.com/yelog/layui-soul-table/issues/33 )