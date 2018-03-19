# javascript中构造函数的原型链
JS中对象的继承，也就是所谓的类的继承，一般有五种方式：

1：直接拷贝。将父对象的原型对象中的所有属性方法全部给子对象的原型拷贝一份就可以了。

```
function extend2(Child, Parent) {
    var p = Parent.prototype;
    var c = Child.prototype;
    for (var i in p) {
        c[i] = p[i];
    }
    c.uber = p;
}
```

2：将子对象的原型对象（prototype）指向父元素的实例对象

```
Cat.prototype = new Animal();

　　Cat.prototype.constructor = Cat;

　　var cat1 = new Cat("大毛","黄色");

　　alert(cat1.species); // 动物
```

3：将子对象的原型对象（prototype）指向父对象的原型对象（prototype）(这种情况下，你对子对象的原型对象的更改，会污染到父对象)

```
Cat.prototype = Animal.prototype;

　　Cat.prototype.constructor = Cat;

　　var cat1 = new Cat("大毛","黄色");

　　alert(cat1.species); // 动物
```

4：借助空对象作为中间人。让中间对象（构造函数）的原型对象指向父对象的原型对象，那么子对象只需要继承中间对象的实例对象就可以了。

```
　function extend(Child, Parent) {

　　　　var F = function(){};

　　　　F.prototype = Parent.prototype;

　　　　Child.prototype = new F();

　　　　Child.prototype.constructor = Child;

　　　　Child.uber = Parent.prototype;

　　}
```

5：在子对象的构造函数中，使用call或者apply去继承父对象的属性和方法。

```
　　function Cat(name,color){

　　　　Animal.apply(this, arguments);

　　　　this.name = name;

　　　　this.color = color;

　　}

　　var cat1 = new Cat("大毛","黄色");

　　alert(cat1.species); // 动物
```
