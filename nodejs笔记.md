# 什么是Node.js
简单的说 Node.js 就是运行在服务端的 JavaScript。

Node.js 是一个基于Chrome JavaScript 运行时建立的一个平台。

Node.js是一个`事件驱动`I/O`服务端``JavaScript环境`，基于Google的V8引擎，V8引擎执行Javascript的速度非常快，性能非常好。

[解释看这里](https://www.ibm.com/developerworks/cn/opensource/os-nodejs/index.html)

# Node.js应用
## 分为三个部分
1. **引入required模块**
使用require指令来载入，如
```
var http = require("http")
```
2. **创建服务器**
```
http.createServer(function (request,response){   //创建服务器

    //发送HTTP头部
    //HTTP状态值：200：OK
    //内容类型：text/plain
    response.writeHead(200,{'Content-Type':'text/plain'});

    //发送响应数据"Hello World!"
    response.end('Hello World!\n');
}).listen(8888);    //绑定8888端口

    //终端打印如下信息
    console.log('Service running at http://127.0.0.1:8888/');
```

3. **接收请求与响应请求**

# 语法
实际上还是JavaScript


# 回调函数
**Node.js以部变成的直接体现就是回调**

回调函数一般作为函数的最后一个参数出现，例如
```
//定义：callback是回调函数名
function func1(value1,value2,callback){}

//使用：回调函数可以是匿名函数，也可以是已经定义好的函数
a.func1(value1,value2,function(err,data){
    //此处是匿名回调函数
})
```