# 浅析Vue两个版本

## Vue完整版和非完整版的区别

|              | Vue完整版                    | Vue非完整版                   |
| ------------ | ---------------------------- | ----------------------------- |
| 特点         | 有compiler                   | 没有compiler                  |
| 视图         | 写在HTML里或写在template选项 | 写在render函数里用h来创建标签 |
| cdn引入      | vue.js                       | vue.runtime.js                |
| webpack引入  | 需要配置alias                | 默认使用非完整版              |
| @vue/cli引入 | 需要额外配置                 | 默认使用非完整版              |

> 经总结一般使用非完整版，配合vue-loader和vue文件
> vue-loader可以把vue文件里的html转换为h函数

---
template在完整版中使用:
方法一：写在构造函数中
  ```js
  new Vue({
      el:'#app',
      template:'<div>hi</div>'  //会自动渲染在绑定#app的页面中
  })
  ```
  
方法二：写在template标签里
  ```js
  <div id="app">
    <template id="tem"><h3>模板</h3></template>
  </div>
  <script>
    new Vue({
        el:'#app',
        template:"#tem"
    })
  </script>
  ```

方法三：写在script标签里
  ```js
  <script type="x-template" id="tem">
    <h3>我是模板</h3>
  </script>
  <script>
    new Vue({
        el:'#app',
        template:"#tem"
    })
  </script>
  ```

render的使用:
方法一：
  ```js
  new({
      el:'#app',
      render:createElement=>createElement('div',['HelloVue'])
  })
  ```
  
方法二：向render函数传入配置对象
```js
var app={
    template:'<div>{{name}}</div>',
    data(){
        return {
            name:'jack'
        }
    }
}

new Vue({
    el:'#app',
    render:createElement=>createElement(app)
})
```

方法三：
```js
var app={
    render:createElement=>createElement('div',['HelloVue'])
}

new Vue({
    el:'#app',
    render:createElement=>createElement(app)
})
```
