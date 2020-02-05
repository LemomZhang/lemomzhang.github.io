# HTML常用标签


### a标签

* 属性

	href：

	​    值为网址：//google.com

	​	值为路径：/a/b/c或a/b/c或index.html或./index.html

	​	值为伪协议：

	1. javascript:xxx;

	   2. mailto:邮箱

	   3. tel:手机号

		值为id:

		跳转到指定id为xxx的元素部分:href=#xxx	

	target：指定在哪个窗口打开

	download：大部分不支持

	rel=noopener：为了防止一个BUG

* 作用

	1. 跳转外部页面
	2. 跳转内部锚点
	3. 跳转到邮箱或电话等

---

### img标签

 * 作用：发出get请求，展示一张图片

 * 重要属性：

	alt : 加载图片失败的提示

	height / width / src

* 事件：

	onload : 图片加载成功时会调用

	onerror : 图片加载失败时会调用，作用是可替换一张正常的图片代替加载失败的情况

* 响应式：

	max-width : 100%

---

### table标签

* 主要包含三部分：thead , tbody , tfooter

* 三部分中分别可以用 tr 和 td 写内容

* 默认的table样式会比较丑，所以一般设置两个属性：

	```javascript
	border-collapse:collapse; //合并表格
	border-spacing: 0; //不需要空隙
	```

---

 #### 小记：书山有路勤为径，学海无涯苦作舟




