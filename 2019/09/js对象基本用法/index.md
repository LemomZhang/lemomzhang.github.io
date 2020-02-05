# JS对象基本用法

### 对象基础

- 定义：

	<span style='color:red'>无序</span>数据集合

	<span style='color:red'>键值对</span>的集合

- 写法：

	```javascript
	let obj={'name':'lemom', 'age':18}
	let obj = new Object({'name':'lemom'
	})
	cosole.log({'name':'lemom', 'age':18})
	```

- 细节

	<span style='color:red'>键名是字符串</span>，不是标识符，可包含任意字符

	引号可省略，省略后只能写标识符（引号省略了键名依然是字符串）

	> <span style='color:red'>Object.keys(obj)可以得到obj的所有key</span>

- 变量作属性名

	```javascript
	let p1 = 'name'
	let obj={p1 : 'lemom'} //属性名为'p1'
	let obj={[p1] : 'lemom'} //属性名为'name'
	```

	对比：不加 [ ] 的属性会自动变成字符串；加了[ ]则会当做变量求值，值不是字符串会自动变成字符串 

### 对象的隐藏属性

- JS中每个对象都有一个隐藏属性，存储着共有属性组成的对象的二地址

	，这个组成的对象就叫做<span style='color:red'>原型</span>，也就是说隐藏属性存着原型的地址

- 示例

	```javascript
	var obj={}
	obj.toString()
	//因为 obj的隐藏属性对应的对象上有toString()，所以该方法不会报错
	```

### 对象的增删改查

#### 删除属性

- delete obj.xxx 或 delete obj['xxx']

	区别：obj.xxx=undefined，此时只是删除属性值，<span style='color:red'>delete则是删除属性名和属性值</span>

- 判断属性名是否在对象中（不区分自身与共有属性）

	'xxx' in obj  返回boolean

- 不能用 obj.xxx===undefined 来判断属性名是否存在，应该用（ <span style='color:red'>'xxx' in obj && obj.xxx===undefined</span> ）

#### 查看所有属性

- 查看自身所有属性

	Object.keys(obj)

- 查看自身 和 共有属性

	console.dir(obj)

- 判断一个属性是否是自身属性

	obj.hasOwnProperty('toString')

- 两种方法查看属性值：

	1. 中括号：obj['key']

	2. 点语法：obj.key

		> <span style='color:red'>注意：obj[key]  key在此处为变量，表示的是字符串</span>
		>
		> obj.name !== obj[name]
		>
		> obj.name === obj['name']

#### 原型

- 每个对象都有原型，原型里存着对象的共有属性
- <span style='color:red'>obj.__ proto __</span>存着这个原型对象的地址
- 对象的原型也是对象，所以原型也有原型，包含着所有对象的共有属性，是<span style='color:red'>对象的根</span>
- 原型的原型是 <span style='color:red'>null</span>

#### 修改或增加属性

- 直接赋值

	```javascript
	let obj={name:'lemom'}
	obj.name='lemom2'
	obj['name']='lemom22'
	obj['na'+'me']='lemom222'
	let key = 'name'
	obj[key] = 'lemom223'
	```

- 批量赋值

	Object.assign(obj,{age:18, gender:'male'})

> 无法通过自身属性<span style='color:red'>修改原型属性</span>
>
> 如：obj.toString = 'xxx' 只是修改自身属性，不会影响原型上的属性。
>
> 但可以通过以下方式修改或增加原型属性：
>
> ```javascript
> obj.__proto.toString='xxx' //但不推荐这种方式
> Object.prototype.toString='xxx' //推荐此方式
> ```
>
> <span style='color:red'>一般不要修改原型</span>

- 修改隐藏属性（原型）( __ proto __)

	```javascript
	let obj = {name:'lemom'}
	let common ={kind:'human'}
	obj.__proto__ = common
	```

	推荐使用 Object.create() 方法

	```javascript
	let common ={kind:'human'}
	let obj = Object.create(common)
	obj.name='lemom'
	//先修改原型，再添加自身属性
	```

	
