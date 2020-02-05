# JQuery基本操作

# jQuery 获取元素
```
$(document) //选择整个文档对象
$('#myId') //选择ID为myId的网页元素
$('div.myClass') // 选择class为myClass的div元素 
$('input[name=first]') // 选择name属性等于first的input元素
```
# jQuery 链式操作
原理:每一步的jQuery操作，返回的都是一个jQuery对象，所以不同操作可以连在一起。
```
$('div') //找到div元素
.find('h3') //选择其中的h3元素
.eq(2) //选择第3个h3元素
.html('Hello'); //将它的内容改为Hello
```
# jQuery 创建元素
把新元素直接传入jQuery的构造函数
```
$('<p>Hello</p>');
$('<li class="new">new list item</li>');
$('ul').append('<li>list item</li>');
```
# jQuery 移动元素
提供两组方法，来操作元素在网页中的位置移动。
一组方法是直接移动该元素，另一组方法是移动其他元素，使得目标元素达到想要的位置。
```
//第一种方法是使用.insertAfter()，把div元素移动p元素后面：
$('div').insertAfter($('p'));
//第二种方法是使用.after()，把p元素加到div元素前面：
$('p').after($('div'));
```
其他4对操作方法如下：

> .insertAfter()和.after()：在现存元素的外部，从后面插入元素

> .insertBefore()和.before()：在现存元素的外部，从前面插入元素

> .appendTo()和.append()：在现存元素的内部，从后面插入元素

> .prependTo()和.prepend()：在现存元素的内部，从前面插入元素

# jQuery 修改元素的属性
使用同一个函数，来完成取值（getter）和赋值（setter）
```
$('h1').html(); //html()没有参数，表示取出h1的值
$('h1').html('Hello'); //html()有参数Hello，表示对h1进行赋值
```
常见取值和赋值
```
.html() 取出或设置html内容
.text() 取出或设置text内容
.attr() 取出或设置某个属性的值
.width() 取出或设置某个元素的宽度
.height() 取出或设置某个元素的高度
.val() 取出某个表单元素的值
```
删除元素使用.remove()和.detach()。

两者的区别在于，前者不保留被删除元素的事件，后者保留，有利于重新插入文档时使用。
