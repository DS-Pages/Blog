---
title: Ktor 使用外部配置文件
date: 2025-04-02T19:33:27+08:00
lastmod: 2025-04-02T19:33:27+08:00
# avatar: avatar.jpg
# authorlink: https://author.site
cover: ktor_icon.png
# images:
#   - ktor_icon.png
categories:
  - 教程
tags:
  - Kotlin
  - Ktor
# nolastmod: true
---
 
<!--more-->

# 教程

如果你使用 EngineMain 启动服务器，Ktor 会自动在 `resources` 目录里寻找 `application.*` 格式的文件，目前只支持 `.conf` 和 `.yml` 格式，所以会寻找 `application.conf` 和 `application.yml`

但是，实际部署的时候配置是不固定的，所以需要使用外部的配置文件，方便用户配置端口，数据库信息等

Ktor 的官方文档中也有提及如何使用外部配置文件（命令行参数）  
https://ktor.io/docs/server-configuration-file.html#command-line

But！官方文档中提及的命令行参数方法示例是这样的  
`java -jar sample-app.jar -config=anotherfile.conf`

然而在某些时候会出现以下错误  
`Neither port nor sslPort specified. Use command line options -port/-sslPort or configure connectors in application.conf`

这个错误是因为没有正确读取到配置文件，因为读取参数的时候把 `anotherfile.conf` 分割开了，导致程序收到是 `-config=anotherfile` ，后面的`.conf`丢掉了

只需要给 `application.conf` 加上引号就可以了，变成 `"application.conf"`，示例改为  
`java -jar sample-app.jar -config="anotherfile.conf"`