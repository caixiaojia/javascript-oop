# 深拷贝
>和浅拷贝相同,只是在遍历时候判断是否是对象,如果是对象则进行对象内部的拷贝.

function deepCopy(p,c){
    var c = c|| {};
    for (var i in p){
        if(typeof p[i] === 'object'){
          c[i] = (p[i].constructor === Array)?[]:{};
             deeCopy(p[i],c[i]);
        
        }else{
            c[i]=p[i];
         }
    }
        return c;
}