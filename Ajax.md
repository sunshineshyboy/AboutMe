# 原生Ajax: 

```javascript
window.onload = function(){
  var oBtn = document.getElementById('btn');
  oBtn.onclick = function(){
    if(window.XMLHttpRequest) // 非IE6浏览器。
        {
            var oAjax = new XMLHttpRequest(); // 创建ajax对象
        }
        else // IE6浏览器
        {
            var oAjax = new ActiveXObject("Microsoft.XMLHTTP"); // IE6浏览器创建ajax对象
        }
        oAjax.open("GET","a.txt?t='+new Date().getTime()",true);
        
         /* 
            Ajax的open（）方法有3个参数：1、method；2、url；3、boolean；
            参数1有get和post两个取值
            参数2表示什么就不用说了
            重点说下第3个参数：boolean的取值
            当该boolean值为true时，服务器请求是异步进行的，也就是脚本执行send（）方法后不等待
            服务器的执行结果，而是继续执行脚本代码；
            当该boolean值为false时，服务器请求是同步进行的，也就是脚本执行send（）方法后等待
            服务器的执行结果的返回，若在等待过程中超时，则不再等待，继续执行后面的脚本代码！
        */
        
        oAjax.send();
        oAjax.onreadystatechange=function()
        {
            /*
                oAjax.readyState : 浏览器和服务器，进行到哪一步了。
                0（未初始化）：还没有调用 open() 方法。
                1（载入）：已调用 send() 方法，正在发送请求。
                2 (载入完成）：send() 方法完成，已收到全部响应内容。
                3 (解析）：正在解析响应内容。
                4 (完成）：响应内容解析完成，可以在客户端调用。
            */    
            if(oAjax.readyState==4)
            {
            
            /*
                oAjax.status :
                200:
                304:
                404:
            */
                if(oAjax.status==200)//判断是否成功,如果是200，就代表成功
                {
                    alert("成功"+oAjax.responseText);//读取a.txt文件成功就弹出成功。后面加上oAjax.responseText会输出a.txt文本的内容
                }
                else
                {
                    alert("失败");
                }
            }else{
              alert("false");
            }
        };
  }
}
```
