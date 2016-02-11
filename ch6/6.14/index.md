#小结

>实现继承分为两类:

1. 基于构造器的工作的模式
1. 基于对象工作的模式

>可以基于一下条件对这些模式进行分类

1. 是否使用原型
1. 是否执行属性拷贝
1. 两者都有

| 方法编号 | 方法名称 | 代码示例 | 所属模式 | 技术注解 |
|:-----:|:----:|----|:-----:|----|
| 1    | 原型链法(仿传统)    | Child.prototype = new Parent()    | 基于构造器工作模式;使用原型链模式    | ECMA标准继承机制提示:我们可以将方法和属性集中可重用的部分迁移到原型链中,将不可重用的设置为对象的自身属性    |
| 2    | 仅从原型继承法    | Child.prototype = Parent.prototype    | 基于构造器工作模式;原型拷贝模式    | 由于该模式在构建继承关系上不需要新建对象实例,效率上会有较好的表现,原型链查询也比较快,因为这里根本不存在链,缺点时,对于子对象修改会影响父对象    |
| 3    | 临时构造器法    | function extent(Child,Parent){var F=function(){};F.prototype = Parent.prototype; Child.prototype = new F(); child.prototype.constructor = Child;Child.uber = Parent.prototype;}    | 基于构造器工作模式;使用原型链进行    | 它只继承父对象的原型属性,对于父对象自身属性(也就是被构造器添加到this值中的属性)不予继承,该模式在YUI和Extjs等程序库中均有应用,该模式还为我们访问父对象提供了便利的方式    |
| 4    | 原型属性拷贝法    | function extend2(Child,Parent){var p = Parent.prototype; var c = Child.prototype;for(var i in p){c[i]=p[i];}c.uber = p;}    | 基于构造器工作模式;拷贝属性模式使用原型模式    | 将父对象原型中的内容全部转换成子对象原型属性;无需为继承单独创建对象实例(函数标示法对象,无名字);原型链本身也更短    |
| 5    | 全属性拷贝法(即浅拷贝法)    | function extendCopy(p){var c={};for(var i in p){c[i]=p[i];}c.uber = p;return c;}    | 基于对象工作模式;属性拷贝模式    | 非常简单化,在Firbug,jQuery以及Prototype.js早期版本中都有应用    |
| 6    | 深拷贝法    | 同上,只要遇到对象类型时候,重复调用上述函数即可    | 基于对象工作模式;属性拷贝模式    | 与5方法相同,但是所有对象都是基于值传递.在jQuery近期版本中被广泛使用    |
| 7    | 原型继承法    | function object(o){function f(){};F.prototype=o;return new F();}    | 基于对象的工作模式;使用原型链模式    | 丢开仿类机制,直接在对象之间构建继承关系,发挥原型固有优势    |
| 8    | 扩展与增强模式    | function objectPlus(o,stuff){var n; function F(){};F.prototype=o;n = new F();n.uber =o;for(var i in stuff){n[i]=stuff[i];}return n;}    | 基于对象工作模式,使用原型链模式,属性拷贝模式    | 该方法实际上是原型继承法和属性拷贝法的混合应用,它通过一个函数一次性完成对象的继承和扩展    |
| 9    | 多重继承法    | functin multi(){var n={},stuff,j=0,len=arguments.length;for(j=0;j<len;j++){stuff=arguments[j];for(var i in suff){n[i]=stuff[i];}}return n;}    | 基于对象的工作模式;属性拷贝模式    | 一种混合插入继承实现,会按照父亲元素出现的顺序一次对他们执行的属性进行全部拷贝    |
| 10   | 寄生继承法    | function parasite(victiom){var that = object(victim);that.more =1;return that;}    | 基于对象工作模式;使用原型链模式    | 该方法通过一个类似构造器的函数来创建对象;该函数会指向响应的对象拷贝,然后进行扩展,最后返回该拷贝    |
| 11   | 构造器借用法    | function Child(){Parent.apply(this,argumetns);}    | 基于构造器工作模式    | 该方法可以只继承父对象的自身属性,也可以和方法1结合使用,从圆形中继承相关内容.它便于我们子对象继承某个对象的具体属性|
| 12   | 构造器借用和属性拷贝    | function Child(){Parent.apply(this,argumetns);}extend2(Child,Parent);    | 使用构造器工作模式;使用原型链模式;属性拷贝模式    | 该方法是方法11和方法4结合体,允许我们不重复调用狗仔起的情况下继续继承自身属性和原型属性    |



