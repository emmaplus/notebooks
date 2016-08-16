# Memoization的定义

Memoization 是一种将函数返回值缓存起来的方法，Memoization 原理非常简单，就是把函数的每次执行结果都放入一个键值对(数组也可以，视情况而定)中，在接下来的执行中，在键值对中查找是否已经有相应执行过的值，如果有，直接返回该值，没有才 真正执行函数体的求值部分。很明显，找值，尤其是在键值对中找值，比执行函数快多了。现代 JavaScript 的开发也已经大量使用这种技术。

## 一个简单的使用memoization的例子

这是一个代码区块.

    function createXHRObject = function(){  
        //先把三个匿名函数缓存起来。     
        var methods = [     
            function(){return new XMLHttpRequest();},       
            function(){return new ActiveXObject("Msxml2.XMLHTTP");},        
            function(){return new ActiveXObject("Microsoft.XMLHTTP");}      
        ];      
        for(var i=0,len=methods.length;i<len;i++){  
            try{//这里用try catch来代替了条件判断，通常我不赞成这种写法   
                methods[i]();   
            }   
            catch(e){   
                continue;//如果报异常，则执行下一次循环   
            }   
            // 把createXHRObject 与能正常执行的匿名函数对应起来，再调用createXHRObject不用再检测浏览器了 
            createXHRObject = method[i];    
            return method[i];   
        }   
    }


