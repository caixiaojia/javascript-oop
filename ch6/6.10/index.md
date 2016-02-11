# 原型继承和属性拷贝的混合应用
1. 先通过原型继承克隆现存对象
1. 对其他对象使用属性拷贝的方式
function objectExtend(o,stuff){
    var n;
    function F(){};
    F.prototype = o;
    n = new F();
    n.uber =o;
    
    for(var i in stuff){
        n[i] = stuff[i]
        }
       return n;
 }