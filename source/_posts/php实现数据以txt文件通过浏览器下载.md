---
title: php实现数据以txt文件通过浏览器下载
date: 2019-04-20 18:20:10
tags:
- PHP
- 数据下载

---

> 使用php在后台查询数据，然后通过接口将数据·以文件的格式通过浏览器下载。
> <!--more-->

1.代码
```php
     //处理文件名
     $ua = $_SERVER["HTTP_USER_AGENT"];  
     $filename = "中文文件名.txt";  
     $encoded_filename = urlencode($filename);  
     $encoded_filename = str_replace("+", "%20", $encoded_filename); 
	 //header头设置
     header("Content-Type: application/octet-stream");    
     if (preg_match("/MSIE/", $_SERVER['HTTP_USER_AGENT']) {
       header('Content-Disposition:  attachment; filename="' .$encoded_filename . '"');    
     } else if (preg_match("/Firefox/",$_SERVER['HTTP_USER_AGENT']))    { 
     header('Content-Disposition: attachment;filename*="utf8' .  $filename . '"');    
     } else {    
    header('Content-Disposition: attachment; filename="' .  $filename . '"');    
     }
     //输出函数到下载的文件中
     echo $ur;
```

2.相关内容

> *php header()函数*

```php
"Content-type:application/octet-stream"
```

> 只能提交二进制，而且只能提交一个二进制，如果提交文件的话，只能提交一个文件,后台接收参数只能有一个，而且只能是流（或者字节数组）

```php
header('Content-Disposition: attachment;filename*="utf8' .  $filename . '"'); 
```

> 当你在响应类型为application/octet- stream情况下使用了这个头信息的话，那就意味着你不想直接显示内容，而是弹出一个"文件下载"的对话框，接下来就是由你来决定"打开"还是"保存" 了



参考文章：

- <https://blog.csdn.net/oQiWei1/article/details/62432315>
- <https://blog.csdn.net/lxc939134342/article/details/50291349>