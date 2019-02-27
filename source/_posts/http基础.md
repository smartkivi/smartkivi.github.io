---
title: http基础
date: 2019-02-27 04:17:06
categories: 
- 前端学习
tags:
- 协议
---
一、http请求

（1）组成：

第一部分：动词 路径 协议/版本

动词：GET/POST/PUT/PATCH/DELETE

路径包含查询参数（但不包括锚点）

第二部分：请求头部，紧接着请求行（即第一行）之后的部分，用来说明服务器要使用的附加信息

从第二行起为请求头部，HOST将指出请求的目的地.User-Agent,服务器端和客户端脚本都能访问它,它是浏览器类型检测逻辑的重要基础.该信息由你的浏览器来定义,并且在每个请求中自动发送等等

第三部分：空行，请求头部后面的空行是必须的

即使第四部分的请求数据为空，也必须有空行。

第四部分：请求数据也叫主体，可以添加任意的其他数据。

（2）查看

1、F12打开开发者工具

2、输入网址（带https）

3、打开第一个数据包（含有该网址域名），点击request-header

4、点击view source，即可查看

二、http响应

（1）组成

第一部分：状态行，由HTTP协议版本号， 状态码， 状态消息 三部分组成。

第二部分：消息报头，用来说明客户端要使用的一些附加信息

第二行和第三行为消息报头，

Date:生成响应的日期和时间；Content-Type:指定了MIME类型的HTML(text/html),编码类型是UTF-8

第三部分：空行，消息报头后面的空行是必须的

第四部分：响应正文，服务器返回给客户端的文本信息。

（2）查看

1、F12打开开发者工具

2、输入网址（带https）

3、打开第一个数据包（含有该网址域名），点击response-header

4、点击view source，即可查看

三、curl命令使用

curl  [选项] ”网址“

选项参数：

-A/--user-agent 设置用户代理发送给服务器

-b/--cookie cookie字符串或文件读取位置

-c/--cookie-jar 操作结束后把cookie写入到这个文件中

-C/--continue-at 断点续转

-D/--dump-header 把header信息写入到该文件中

-e/--referer 来源网址-f/--fail 连接失败时不显示http错误

-o/--output 把输出写到该文件中

-O/--remote-name 把输出写到该文件中，保留远程文件的文件名

-r/--range 检索来自HTTP/1.1或FTP服务器字节范围

-s/--silent 静音模式。不输出任何东西

-T/--upload-file 上传文件

-u/--user 设置服务器的用户和密码

-w/--write-out [format] 什么输出完成后

-x/--proxy 在给定的端口上使用HTTP代理

-#/--progress-bar 进度条显示当前的传送状态
