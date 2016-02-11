# 将继承封装成函数
>两个构造器之间的,父子链
function extend(child,parent){//child是文本标示法,或者实例,而parent则是一个构造器
    var F =function();
    F.prototype = new parent();
    child.prototype = new F();
    child.prototype.constructor = child;
    child.prototype.uber = child.prototype
}

以上也是YUI哭在实现继承时候所用的方法