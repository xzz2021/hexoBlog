---
title: elementUI使用记录
date: 2022-05-25 23:02:10
categories: 经验分享
tags: elementUI
cover: /image/start.svg
---

## 1.在v-for循环中使用el-pagination实现分页

  ### 把v-for的数据dateList进行slice切割，从而实现假分页

##### 

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

{% flink %}
- class_name: 参考文章
  link_list:
    - name: Ace_壹
      link: https://blog.csdn.net/weixin_38797742/article/details/115161767
      avatar: https://jerryc.me/img/avatar.png
      descr: v-for中用elementUI实现分页
{% endflink %}