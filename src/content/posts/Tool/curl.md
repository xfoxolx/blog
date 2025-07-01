---
title: curl の Usage
published: 2024-07-01
description: "curl用法"
tags: ["Tool","curl"]
category: Tool
draft: false
---

## cURL Usage

### What is cURL?

:::note
`cURL`（Client for URLs）是一个开源的命令行工具和库，用于通过各种网络协议（如HTTP、HTTPS、FTP、SFTP等）与服务器进行数据传输.
:::

### getting Started

```sh
curl https://example.com
# 获取网站HTML代码
curl -L http://example.com
# 处理网站重定向自动跟随获取HTML
curl -O https://example.com/image.jpg
# 直接保存文件不修改文件名
curl -o ./mypic.jpg https://example.com/image.jpg
# 保存文件并修改文件名
curl -C - -O https://example.com/bigfile.zip
# 大文件断点续传下载
curl -F "file=@/path/to/yourfile.txt" https://example.com/upload
# 上传文件到服务器
curl -v -include \
    --form key1=value1 \
    --form upload=@localfilename URL
# 多文件上传
curl "https://www.{example,w3,iana}.org/index.html" --output "file_#1.html"
# 多个域下载文件
curl -s http://url/myscript.sh
# s 静默下载脚本
curl -sSL https://get.rvm.io | bash
# sS同时使用失败时显示信息，遵循重定向。管道传递给bash执行。
curl -sSL https://example.com/script.py | python3 - --arg1 value1
# 传参
```

:::tip
你可以通过管道将对应可执行文件传输给对应的解释器
:::

```sh
curl -I https://example.com
# 查看网站返回响应头
curl -v https://example.com
# 查看详细的请求和响应信息
curl -k https://example.com
# 忽略证书问题
curl -X POST -d "username=abc&password=123" https://example.com/login
# -X POST：指定用 POST 方法 -d 附上信息。向服务器发送POST请求
curl -H "Authorization: Bearer your_token" https://api.example.com
# 自定义请求头(比如密钥授权、API)
curl -u username:password http://example.com/
# 基本认证
```