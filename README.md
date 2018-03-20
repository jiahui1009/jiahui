# Mini-Programs
汇总微信小程序常用的代码块及bug解决

----

### 获取上个页面的数据

```oc

let pages = getCurrentPages();

if (pages.length > 1) {
	let  page = pages[pages.length - 1]; //当前页面
	let prevPage = pages[pages.length - 2]; // 上个页面
	prevPage.route === 'pages/cardsShop/cardsShop'
}

通过 page 可以拿到 data, func route ...     
     
```

### setData 修改数组中的某一项的值

```

var price = 'goods['+index+'].price'
this.setData({
   [price]:'changed data'
})
    
```

### text 超出 view 处理

```oc
display: block;
word-break: keep-all; /* 不换行 */
white-space: nowrap; /* 不换行 */
overflow: hidden; /* 内容超出宽度时隐藏超出部分的内容 */
text-overflow: ellipsis;

width: 78vw;
text-align: center;

```

### 格式化时间

```

// 卡片中的资讯时间格式化
for (let i = 0; i < data.contents.length; i++) {
	for (let j = 0; j < data.contents[i].items.length; j++) {
		data.contents[i].items[j].pub_date = util.formatTime(data.contents[i].items[j].pub_date, true)
	}
}

```

### 常用的API

wx.on 开头的 API 是监听某个事件发生的API接口，接受一个 CALLBACK 函数作为参数。当该事件触发时，会调用 CALLBACK 函数。

- onTabItemTap 监听 `TabBarItem`  点击事件


	```
	onTabItemTap(res) {
    	// 回到顶部，刷新数据
   	 	wx.pageScrollTo({
     		scrollTop: 0,
    	});
    	this.loadHomeUnreadData(true);
  },
	```






