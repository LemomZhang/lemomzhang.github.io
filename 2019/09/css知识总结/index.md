# CSS 知识总结

# CSS发明
> CSS首先由赖先生（Hakon Wium Lie）提出

# CSS的牛X之处
* 层叠样式表
  1. 样式层叠：可以多次对用已选择器进行样式声明
  2. 选择器层叠：可以用不同选择器对同一个元素进行样式声明
  3. 文件层叠：可以用多个文件进行层叠
* 重要版本
  1. CSS2.1(2004~2011年)使用最广泛的版本(IE支持)
  2. CSS3(1999年开始起草)现代版本，分模块(IE8部分支持)
   
> 支持的浏览器以及特性可去caniuse.com

# CSS语法
```
/*语法一：*/
选择器{
    属性名：属性值;
}

/*语法二：at语法*/
@charset "UTF-8";
@import url(2.css);
@media (min-width:100px) and (max-width:200px){
    语法一
}
```
# 重要概念
1. 文档流Normal Flow
2. 块，内联，内联块
3. margin合并
4. 两种盒模型(border-box,content-box)
# 浏览器渲染原理
**步骤**：

1. 根据HTML构建HTML树
2. 根据CSS构建CSS树
3. 将两颗树合并成一颗渲染树
4. Layout布局(文档流，盒模型，计算大小和位置)
5. Paint绘制(把边框颜色，文字颜色，阴影等画出来)
6. Compose合成(根据层叠关系展示画面)


# CSS动画的两种做法
1. transition(过渡)
> 一般配合transform(变形)使用

> 作用：补充中间帧

> 语法：transition:属性名 时长 过渡方式 延迟
> (left 200ms linear)

>可以用逗号分隔两个不同属性，如(transition:left 200ms,top 400ms)，可以用all代替所有属性，如(transition:all 200ms)
2. animation

    缩写语法：时长|过渡方式|延迟|次数|方向|填充模式|是否暂停|动画名;
```css
.eye{
    animation: 4s linear 0s infinite alternate move_eye;
}
@keyframes move_eye { from { margin-left: -20%; } to { margin-left: 100%; }  }

/*@keyframes还可以是百分数*/
```



