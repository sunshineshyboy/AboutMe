```
function a(){
  var i=0;
  function b(){
    alert(++i);
  }
  return b;
}
var c=a();
c();
```
`当函数a的内部函数b被函数a外的一个变量引用的时候，就创建了一个闭包。`  
`垃圾回收机制不会收回a所占用的资源，因为a的内部函数b的执行需要依赖a中的变量。`

```
function Counter(start){
    var count = start;
    return{
        increment:function(){
            count++;
        },
        get:function(){
            return count;
        }
    }
}
var foo =Counter(4);
foo.increment();
foo.get();  // 5
Counter 函数返回两个闭包，函数 increment 和函数 get。  
这两个函数都维持着对外部作用域 Counter 的引用，因此总可以访问此作用域内定义的变量 count。
```

`利用闭包，修改下面的代码，让循环输出的结果依次为1， 2， 3， 4， 5`
```
for (var i=1; i<=5; i++) { 
  setTimeout( function timer() {
      console.log(i);
  }, i*1000 );
}
```

```
for (var i=1; i<=5; i++) { 
  (function(i) {
      setTimeout( function timer() {
          console.log(i);
      }, i*1000 );
  })(i)
}
```

