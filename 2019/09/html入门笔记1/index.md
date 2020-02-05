# HTML入门笔记1


## HTML之父
* 1990年左右诞生
* 李爵士（Tim Berners-Lee）发明了WWW，同时发明了HTML，HTTP，URL
* 目的是网上冲浪
## HTML起手式
```html
<!DOCTYPE html>	<!--文档类型 -->
<html lang="zh-CN"><!--可以把lang改成en -->
<head>
    <meta charset="UTF-8"><!--文件的字符编码啊 -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no"><!--禁用缩放，兼容手机-->
    <meta http-equiv="X-UA-Compatible" content="ie=edge"><!--告诉IE使用最新内核 -->
    <title>Document</title><!--标题 -->
</head>
<body>
</body>
</html>
```
## 常用的表章节标签
1. h1~h6：表示标题，从大到小
2. section:用来表示章节
3. article：用来表示文章
4. p：用来表示段落
5. header：表示头部
6. footer：表示脚步
7. main:表示主要内容
8. aside：表示旁边内容
9. div:表示划分
    


## 全局属性(所有元素都有的属性)

* class 
* contenteditable:可以使任何一个元素可编辑
* hidden：隐藏元素
* id：尽量不使用，因为有重复id不报错；可以直接用id.style.border='xxx'修改样式
* style
* tabindex：控制tab键选中的顺序(从小到大的顺序，0表示最后，-1表示不选)
* title：显示完整的内容


## 常用的内容标签
* ol+li(ordered list+list item)
* ul+li(unordered list+list item)
* dl+dt+dd
* pre(preview的缩写)
* hr
* br(break的缩写)
* a(anchor的缩写)
* em(emphasis的缩写)
* strong
* code
* q(quote的缩写)
* blockquote




