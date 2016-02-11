# 对象之间的继承(浅拷贝)
> 文本表示法和构造器之间,用for in循环直接将对象的属性拷贝到一个文本标示法的对象中,然后返回,对象之间的继承只有拷贝
>这种拷贝属性如果是对象的话实际在传递指针,属于浅拷贝;
function extendCopy(p){
    var a ={};
    for ( arr in p){
    a[arr] = p[arr]
    }
    return a;
}