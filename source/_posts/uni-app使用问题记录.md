---
title: uni-app使用问题记录
date: 2022-06-15 21:26:09
tags: uni-app 
categories: 经验分享
cover: /image/cloud.svg
---



## 1.uni-app页面之间传值方法
### 实现方法就是$emit加$on，关键在于要加<font color=red>定时器函数</font>
### 基于此，滚动或者有延迟的函数调用一定要加延时器，不然大概率会不生效，如uni.pageScrollTo

##### 最近在写一个v-for循环嵌套数组数据的页面，需要点击跳转到新页面并把相应item的index传过去再次v-for循环渲染（其实就是要传相应数组过去），考虑过vuex共享state，不过有点大材小用，后面main.js挂载$Bus监听，发现没有用。（其实uni本身有监听事件方法）搜索后发现原来是点击时会立即触发emit发送出去，而跳转的页面需要时间mounted从而导致数组为空[],解决方法就是延迟函数。

{% codeblock %} 
setTimeout(() => {
				uni.$emit("send", item.allImg)
				console.log(item.allImg)
			}, 500)
      {% endcodeblock %}

使用全局调用即可

{% codeblock %}

mounted() {
			uni.$on("send", (val) => {
				this.allImg = val
			})
		}
 {% endcodeblock %}


参考文章：
1--[uni-app页面之间传值方法--xuyq1226](https://blog.csdn.net/m0_46258282/article/details/109765718)