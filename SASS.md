1: SASS允许使用变量，所有变量以$开头

```
$bg : #ccc;　
div {
　color : $bg;
}
```
2：变量计算功能

```
body {
　padding: $var * 10%;
}
```
3: 样式嵌套

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
次级属性也可以嵌套，例如border-color可以写成：

```
p {
　　border: {
　　　　color: red;
　　}
}
```
在嵌套的代码块内，可以使用&引用父元素。比如a:hover伪类，可以写成：

```
a {
　&:hover { color: #ffb3ff; }
}
```
