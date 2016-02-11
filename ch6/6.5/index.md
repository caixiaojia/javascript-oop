# 属性拷贝
>两个构造器之间的,平级别,将parent的属性拷贝到child之中

function copy2(child,parent){
    c = child.prototype;
    p = child.prototype;
    for (arr in p){
        c[arr] = p[arr];
        }
     c.uber = p;
    }
    