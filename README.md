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



