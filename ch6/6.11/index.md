# 多重继承
> 利用属性拷贝的方法去扩展对象

founction multi(){
    var n ={},stff,j = 0, len = arguments.length;
    for(j=0;j<len,j++){
        stff = arguments[j];
        for(var i in stuff){
            n[i] = stuff[i];
        }
    }
    return n
}

