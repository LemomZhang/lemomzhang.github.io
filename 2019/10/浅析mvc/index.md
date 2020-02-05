# 浅析MVC

## MVC 三个对象
`MVC`是一种架构模式，它将应用抽象为3个部分：模型（数据）、视图、控制器（分发器）。

`MVC`包括三类对象，将他们分离以提高灵活性和复用性。

M：模型model用于封装与应用程序的业务逻辑相关的数据以及对数据的处理方法，会有一个或多个视图监听此模型。一旦模型的数据发生变化，模型将通知有关的视图。
```
const model = {
    //数据
    data: ''
    //初始化
    init(){}
    //方法
    save(){}
    update(){}
}
```
V：视图view是它在屏幕上的表示，描绘的是model的当前状态。当模型的数据发生变化，视图相应地得到刷新自己的机会。
```
const view = {
    init() {}
    template: '<h1>hello</h1'>   //视图渲染
}
```
C：控制器controller定义用户界面对用户输入的响应方式，起到不同层面间的组织作用，用于控制应用程序的流程，它处理用户的行为和数据model上的改变。
```
const controller = {
    view: null,
    model: null,
    init(view, model){
        this.view = view
        this.model = model
        this.bindEvents()
    }
    render(){
        this.view.querySelector('name').innerText = this.model.data.name
    },
    bindEvents(){}
}
```
## EventBus
EventBus是一种设计模式，主要用于组件或对象间的通信简化
EventBus包含很多方法，如：on方法用来监听事件，trigger方法用来触发事件
```
const model = {
    data: {
        i: come from somewhere
    }，
    update(data) {
        Object.assign(model.data, data)
        eventBus.trigger('model:updated')   //触发 model:updated 事件
    }
}
const controller = {
    //初始化方法
    init() {
        //初始化渲染
        view.render(model.data.i)
        eventBus.on('model:updated', () => {    //监听 model:updated 方法并渲染更新页面
            v.render(model.data.i)
        })
    },

}
```
## 表驱动编程
所谓表驱动法(Table-Driven Approach),简单讲是指用查表的方法获取值。

假设我们要把一个数字的数组按星期几的形式输出，那么我们可能这样做：
```
let arr=[2,5,6,3]
let newArr =[]
arr.forEach(item=>{
  if(item===1){
    newArr.push('星期一')
  }else if(item===2){
    newArr.push('星期二')
  }else if(item===3){
    newArr.push('星期三')
  }else if(item===4){
    newArr.push('星期四')
  }else if(item===5){
    newArr.push('星期五')
  }else if(item===6){
    newArr.push('星期六')
  }else{
    newArr.push('星期日')
  }
})
console.log(newArr)
```
如上这样可能写很多类似的代码，如果用表驱动法可以这样做：
```
const week={
  1:"星期一",
  2:"星期二",
  3:"星期三",
  4:"星期四",
  5:"星期五",
  6:"星期六",
  7:"星期日"
}
arr.forEach(item=>{
  newArr.push(week[item])
})
console.log(newArr)
```
由此可看出，使用表驱动可以简化代码，使结构更加简洁清晰
## 模块化理解
首先假如没有模块化，引入外部文件是这样的:
```
<script src="jquery.js"></script>
<script src="main.js"></script>
<script src="a.js"></script>
<script src="b.js"></script>
<script src="c.js"></script>
```
所有js文件都放在了一起，而且这些文件的顺序也不能出错，如jquery需要先引入，才能在其他的文件中使用jquery，缺点如下：
* 污染全局作用域
* 维护成本高
* 依赖关系不明显

ES6使用 import 关键字引入模块，通过 exprot 关键字导出模块使用模块化：
```
//方法一：导出需要的数据
var arr=[]
var str='haha'
export {
	arr,str
}
import {arr,str} from './info.js'
//方法二：让导入者自己命名
export default function (){
	console.log("ooooo")
}
import myFunc from './info.js'
//方法三：定义时直接导出
export var num = 100
export function mul(num1,num2){
    return num1+num2
}
//导入全部模块
import * as aaa from './info.js'
console.log(aaa.属性)
```
