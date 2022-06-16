---
title: Vue使用问题记录
date: 2022-05-13 00:12:02
tags: "Vue"
categories: 经验分享
cover: /image/cloud.svg
---


## 1.Vuex中action调用错误

### uni-app中异步调用action的函数报错Uncaught (in promise) TypeError: yourAction is not a function!出现原因可能是不能异步调用（但action内部可以执行任意的同步和异步操作），故导致promise错误

{% codeblock %} this.yourAction(object) {% endcodeblock %}

使用全局调用即可

{% codeblock %}

this.$store.dispatch({
					type: 'yourAction',
					data: object
					})
 {% endcodeblock %}


参考文章：
1--[Vuex官方文档](https://uniapp.dcloud.io/tutorial/vue3-vuex.html)
2--[uView关于Vuex的文档](https://www.uviewui.com/components/vuexDetail.html)


## 2.在v-for循环中使用el-pagination实现分页

###   把v-for的数据dateList进行slice切割，从而实现假分页

```vue
 v-for="(item，index)  in dateList.slice((currentPage-1) * pagesize, currentPage * pagesize)"
```



```html
<el-pagination
current-change="handleCurrentChange"
current-page="currentPage"
page-size="pagesize"
background
small
layout="total,  prev, pager, next, jumper"
total="imgList"></el-pagination>
```

```vue
mounted() {
   this.imgList = this.dateList.length
 },
 methods: {
      handleSizeChange(val) {
        this.pagesize = val
        // console.log(`每页 ${val} 条`);
      },
      handleCurrentChange(val) {
          this.currentPage = val
        // console.log(`当前页: ${val}`);
      },
  }
```

