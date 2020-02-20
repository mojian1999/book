# ajax



Ajax  是指一种创建交互式[网页](https://baike.baidu.com/item/%E7%BD%91%E9%A1%B5/99347)应用的网页开发技术。

Ajax = 异步 [JavaScript](https://baike.baidu.com/item/JavaScript) 和 XML 或者是 HTML（[标准通用标记语言](https://baike.baidu.com/item/%E6%A0%87%E5%87%86%E9%80%9A%E7%94%A8%E6%A0%87%E8%AE%B0%E8%AF%AD%E8%A8%80/6805073)的子集）。

Ajax 是一种用于创建快速动态网页的技术。

Ajax 是一种在无需重新加载整个网页的情况下，能够更新部分网页的技术。

-----------------



----- 创建对象/打开需要访问的ajax地址/发送请求/给ajax的对象绑定一个对象，等待返回正确的数据/接收数据/浏览器渲染

1.打开浏览器吗，发送请求

- 创建http请求对象

2.向地址栏输入地址

- open 打开url地址对应的页面

- 请求方式：get     post
  - 区别
    - get的传输的数据是写在url地址栏的？后边的；
    - post传输的数据是通过请求头部发送到后台的
    - post方式更安全
    - get方式传输的数据量比较少
    - post方式的传输量比较大

3.回车提交

4.等待服务器返回数据，并接收处理

- 写当数据状态发生改变时触发的是事件

5.判断返回的状态是否正常

6.渲染

7.将字符串转JSON数据

```javascript
<script>
			window.onload = function(){
				console.log(13);
				//1.获取元素
				var oBtn = document.getElementById('btn');
				var oCon = document.getElementById('con');
				//2.帮定事件
				oBtn.onclick = function(){
					//3.获取后台数据
					var xhr = new XMLHttpRequest();
					xhr.open('get','yingyuan.php',true);
					xhr.send();
					xhr.onreadystatechange = function(){
						if(xhr.readyState == 4){
							if(xhr.status == 200){
								var data = xhr.responseText;
								console.log(data);//string  
								
								var json = JSON.parse(data);
								console.log(json);
								
								//for循环渲染
								var cinemas = json.data.cinemas;//影院的数组
								var str = '';
								console.log(json.data.cinemas.length);
								for(var i = 0;i<cinemas.length;i++){
									str += `<p>区名：${cinemas[i].districtName},影院名称:${cinemas[i].name}</p>`;
									
								}
								oCon.innerHTML = str;
							}
						}
					}
					
				}
				
			} 
			</script>
```



## AJAX状态码

1- AJAX状态值与状态码区别
AJAX状态值是指，运行AJAX所经历过的几种状态，无论访问是否成功都将响应的步骤，可以理解成为AJAX运行步骤。如：正在发送，正在响应等，由AJAX对象与服务器交互时所得；使用“ajax.readyState”获得。（由数字1~4单位数字组成）
AJAX状态码是指，无论AJAX访问是否成功，由HTTP协议根据所提交的信息，服务器所返回的HTTP头信息代码，该信息使用“ajax.status”所获得；（由数字1XX,2XX三位数字组成，详细查看RFC）
这就是我们在使用AJAX时为什么采用下面的方式判断所获得的信息是否正确的原因。

if(ajax.readyState == 4 && ajax.status == 200) { putData(ajax.responseText);}

2- AJAX运行步骤与状态值说明
在AJAX实际运行当中，对于访问XMLHttpRequest（XHR）时并不是一次完成的，而是分别经历了多种状态后取得的结果，对于这种状态在AJAX中共有5种，分别是。
0 - (未初始化)还没有调用send()方法
1 - (载入)已调用send()方法，正在发送请求
2 - (载入完成)send()方法执行完成，
3 - (交互)正在解析响应内容
4 - (完成)响应内容解析完成，可以在客户端调用了
对于上面的状态，其中“0”状态是在定义后自动具有的状态值，而对于成功访问的状态（得到信息）我们大多数采用“4”进行判断。



3-AJAX状态码说明



1**：请求收到，继续处理
2**：操作成功收到，分析、接受
3**：完成此请求必须进一步处理
--4**：请求包含一个错误语法或不能完成
5**：服务器执行一个完全有效请求失败
100——客户必须继续发出请求
101——客户要求服务器根据请求转换HTTP协议版本
--200——交易成功
201——提示知道新文件的URL
202——接受和处理、但处理未完成
203——返回信息不确定或不完整
204——请求收到，但返回信息为空
205——服务器完成了请求，用户代理必须复位当前已经浏览过的文件
206——服务器已经完成了部分用户的GET请求
300——请求的资源可在多处得到
301——删除请求数据
302——在其他地址发现了请求数据
303——建议客户访问其他URL或访问方式
304——客户端已经执行了GET，但文件未变化
305——请求的资源必须从服务器指定的地址得到
306——前一版本HTTP中使用的代码，现行版本中不再使用
307——申明请求的资源临时性删除
400——错误请求，如语法错误
401——请求授权失败
402——保留有效ChargeTo头响应
403——请求不允许
--404——没有发现文件、查询或URl
405——用户在Request-Line字段定义的方法不允许
406——根据用户发送的Accept拖，请求资源不可访问
407——类似401，用户必须首先在代理服务器上得到授权
408——客户端没有在用户指定的饿时间内完成请求
409——对当前资源状态，请求不能完成
410——服务器上不再有此资源且无进一步的参考地址
411——服务器拒绝用户定义的Content-Length属性请求
412——一个或多个请求头字段在当前请求中错误
413——请求的资源大于服务器允许的大小
414——请求的资源URL长于服务器允许的长度
415——请求资源不支持请求项目格式
416——请求中包含Range请求头字段，在当前请求资源范围内没有range指示值，请求也不包含If-Range请求头字段
417——服务器不满足请求Expect头字段指定的期望值，如果是代理服务器，可能是下一级服务器不能满足请求
500——服务器产生内部错误
501——服务器不支持请求的函数
502——服务器暂时不可用，有时是为了防止发生系统过载
503——服务器过载或暂停维修
504——关口过载，服务器使用另一个关口或服务来响应用户，等待时间设定值较长
505——服务器不支持或拒绝支请求头中指定的HTTP版本

## 跨域

跨域：域名或者子域名，或者ip地址或者端口号不一样，导致的数据获取不到

前端有一个同源保护政策（同域保护政策）

- 前端
  - jsonp    
    - 不能支持post方式
  - 项目打包之前可以使用proxy
- 后端
  - 设置头部信息
    - 不安全
  - 服务器代理

-----------------------

利用script来解决跨域

```javascript
<script type="text/javascript">
    //jsonp的原理,script标签的src属性具有跨域的能力

    window.onload = function(){
    var oBtn = document.getElementById('btn');
    var oCon = document.getElementById('con');

    oBtn.onclick = function(){
        //创建script标签
        var oScript = document.createElement('script');
        oScript.src = 'https://sp0.baidu.com/5a1Fazu8AA54nxGko9WTAnF6hhy/su?wd=前端&cb=JSON_yy';
        //将oScript 放到 header中
        var oHeader = document.getElementsByTagName('head')[0];
        oHeader.appendChild(oScript);

    }
} 

function JSON_yy(data){
    console.log(data);
    var mydata = data.s;
    var str ="";
    for(var i = 0;i<mydata.length;i++){
        str += `<p>${mydata[i]}</p>`;
    }
    document.getElementById('con').innerHTML = str;
}

</script>
```



#### get的非表单的提交方式

如果是没有form的表单方式提交数据，在open函数里面打开想要访问的ajax地址

```javascript
//一.创建ajax对象
var xhr = new XMLHttpRequest();
//二.使用open函数打开 想要访问的ajax地址
xhr.open('get','get.php?user='+user+'&pwd='+pwd,true);
//三.发送请求
xhr.send();
//四.给ajax的对象绑定一个事件,等待返回正确的数据
```

####　post的非表单提交方式

以post方式提交表单的时候，必须设置post的头部信息，以固定形式设置请求头

```javascript
var xhr = new XMLHttpRequest();
//二.使用open函数打开 想要访问的ajax地址
xhr.open('post','post.php',true);
//三.发送请求
//post 设置头部信息
xhr.setRequestHeader("Content-Type","application/x-www-form-urlencoded");//设置请求头
xhr.send('user='+user+'&pwd='+pwd);
```

