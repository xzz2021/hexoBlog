---
title: docker使用问题记录
date: 2022-04-23 11:24:06
tags:
categories: 经验分享
cover: /img/docker.svg
---
### mysql版本密码验证方式不同,出现报错ER_NOT_SUPPORTED_AUTH_MODE
  因为docker下监听的不是localhost而是容器内的ip，所以<code>ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'zxc123';</code>里需要去掉@'localhost',(注意mysql命令需要带分号)，然后workbench直接执行以下命令，或者/bin/bash进入容器<code>mysql -u root -p</code>

<br>

> ALTER USER 'root' IDENTIFIED WITH mysql_native_password BY 'zxc123';
> FLUSH PRIVILEGES;

<br>

