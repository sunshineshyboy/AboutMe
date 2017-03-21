>  
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
当函数a的内部函数b被函数a外的一个变量引用的时候，就创建了一个闭包。
```
