---
title: Jetbrains系列软件
date: 2022-04-17 20:06:38
tags: 软件
categories: 资源分享
cover: /img/jetbrains.png
---
##  貌似Jetbrains系列都能激活

　　[点击进入](https://search.censys.io/)，搜索{% codeblock %}
services.http.response.headers.location: account.jetbrains.com/fls-auth  
{% endcodeblock %}
选择任意一个HTTP Status Code 302的，复制ip到软件激活界面即可，实测WebStorm有效。请勿滥用，条件允许还请支持正版！

　　若失效，点击此[备用站](https://www.shodan.io/)，或者fofa站，搜索fls-auth即可。