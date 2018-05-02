## 1: SASS允许使用变量，所有变量以`$`开头

```
$bg : #ccc;　
div {
　color : $bg;
}
```
## 2：变量计算功能

```
body {
　padding: $var * 10%;
}
```
## 3: 样式嵌套

```
div span {
　　　　color : red;
　　}
```
可以写成下面这样的：

```
div {
　　span {
　　　　color:red;
　　　}
　}
```
次级属性也可以嵌套，例如`border-color`可以写成：

```
p {
　　border: {
　　　　color: red;
　　}
}
```
在嵌套的代码块内，可以使用&引用父元素。比如`a:hover`伪类，可以写成：

```
a {
　&:hover { color: #ffb3ff; }
}
```
## 4:代码重用

#### 4.1一个选择器可以去继承另一个选择器内部的代码，例如：

```
.class1 {
　　border: 1px solid #ddd;
}
.class2 {
　　@extend .class1;
　　font-size:120%;
}
```

#### 4.2 也可以直接去继承代码块，例如：

```
@mixin aaa {
　　float: left;
　　margin-left: 10px;
}
.abc {
　　@include aaa;
   font-size: 16px;
}
```
此时，我们用`@mixin` 去定义一个可以被重复注入的代码块，随后就可以用`@include` 使用这些代码块了
