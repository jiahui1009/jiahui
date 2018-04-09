# Mini-Programs
汇总微信小程序常用的代码块及bug解决

----

### 关于 getUserInfo

此方法只能弹出一次用户授权窗口（非用户主动触发方式），测试的话可以在微信中删除对应的小程序。

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
-webkit-line-clamp: 2;

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

### 新增属性

- 自定义组件 外部样式类

	```
	/* 组件 custom-component.js */
	Component({
		externalClasses: ['my-class']
	})
	
	<!-- 组件 custom-component.wxml -->
	<custom-component class="my-class">这段文本的颜色由组件外的 class 决定</custom-component>

	```
	

### ES6 常用方法
- 复制数组

	```
	const a1 = [1, 2];
	// 写法一
	const a2 = [...a1];
	// 写法二
	const [...a2] = a1;
	
	```
	
- 合并数组
	
	```
	// ES5
	[1, 2].concat(more)
	Array.prototype.push.apply(arr1, arr2);
	
	// ES6
	[1, 2, ...more]
	arr1.push(...arr2);

	```
	
- 与解构赋值结合
	
	```
	// ES5
	a = list[0], rest = list.slice(1)
	// ES6
	[a, ...rest] = list	
	```

- 字符串

	```
	// ES5
	a = list[0], rest = list.slice(1)
	// ES6
	[a, ...rest] = list	
	```

