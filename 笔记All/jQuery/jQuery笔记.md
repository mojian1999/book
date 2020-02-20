# `jQuery`

`jQuery`是一个快速、简洁的`JavaScript`框架，是继Prototype之后又一个优秀的`JavaScript`代码库（或`JavaScript`框架）。`jQuery`设计的宗旨是“write Less，Do More”，即倡导写更少的代码，做更多的事情。它封装`JavaScript`常用的功能代码，提供一种简便的`JavaScript`设计模式，优化HTML文档操作、事件处理、动画设计和Ajax交互。

`jQuery`的核心特性可以总结为：具有独特的链式语法和短小清晰的多功能接口；具有高效灵活的css选择器，并且可对CSS选择器进行扩展；拥有便捷的插件扩展机制和丰富的插件。jQuery兼容各种主流浏览器

##### 选择元素

`$()`:获取对象、节点

``css()`：设置样式

```javascript
//获取对象
var oBox = $('#box');
//设置颜色
oBox.css('color','yellow');
```

##### 函数化

- 事件
- `html()` 文本内容

```javascript
oBox.click(function(){
    //3.修改内容   html() 相当于js中的innerHTML
    oBox.html("我是修改过的内容");

});
```

##### 取值与赋值的关系

- `attr()`:属性
- `val()`:值

```javascript
$('#txt').attr('class','ccc')
$('#txt').val("新内容");
```

##### 预加载

```javascript
$(function(){});
```

##### 选择器

###### 通用选择

- ` *`  ：默认样式

```javascript
$('*').css({"margin":0,"padding":0});
```

###### 层级选择

- ` > ` : 找到子级节点
- `+ `：找到下一个兄弟节点     
-  `~ ` ：找到这个节点下面的所有该类型节点

```javascript
$('#box').find("> ul li").css('font-size','36px');
//找下一个兄弟节点,该dom节点的下一个div节点
$('#myul+div').css('border','1px solid red');
//找到这个dom节点的下面的所有该类型的dom节点
$('#myul~div').css('border','1px solid red');
```

######  基本筛选

- `:animated`：有动画触发的
- `:eq()`：索引
- `:even`：偶数行
- `:odd`：奇数行
- `:first`：第一个
- `:last`：最后一个
- `:gt()`：大于某个索引的
- `:it()`：小与某个索引的

```javascript
<body>
    <ul>
    <li>111111</li>
<li>2222</li>
<li>33333</li>
<li>44444</li>
</ul>
<script type="text/javascript">
    $(function(){
    //按照下标来选择dom节点
     $('li').eq(2).css('background','pink');
     $('li:eq(1)').css('font-size','30px');
     $('li:even').css('color','red');//偶数行
    $('li:odd').css('color','green');//奇数行
    $('li:first').css('color','red');
    $('li:last').css('color','green');
    $('li:gt(2)').css('color','yellow');//大于某个下标
    $('li:lt(1)').css('color','blue');//小于  下标的
    $(document).click(function(){
        $('li').eq(1).animate({'height':'200px'},2000);
        $('li:animated').css('background','orange');//有动画的触发


    })
})
</script>
</body>
```

###### 内容筛选

- `:contains()`：内容为.....的时候可以选中
- `:empty`：内容为空时可以选中
- `:parent`：有父级节点的可以选中

```javascript
//:contains  内容为***的时候可以选中
$('div:contains(1111)').css('background','blue');
//:empty  内容为空时可以选中
$('div:empty').css('background','yellow');

//:parent  有父级节点的可以选中
$('span:parent()').css('background','green');
```

###### 可见度筛选

- `：hidden` ：隐藏的可以使用
- `:visible`：显示的节点可以选中

```javascript
$('div:hidden').css('background','orange');
$('div:visible').css('background','orange');
```

###### 子元素筛选

- `:first-child`：其父节点的第一个子元素的所有指定元素

- `:last-child`：其父节点的最后一个子元素的所有指定元素

- `:first-of-type`：其父元素的第一个子元素该标签的所有该标签

- `:last-of-type`：其父元素的最后一个子元素该标签的所有该标签

- `:nth-child()`：属于其父元素的指定第几个子元素的所有该标签

- `:nth-of-type()`：属于其父元素的指定第几个子元素的所有该标签

- `:only-child`：属于其父元素的唯一子元素的所有指定标签

- `:only-of-type`：属于其父元素的特点类型的唯一子元素的所有该元素

```javascript
//对于div的子元素从第一个元素开始数起， 如果第一个不是span,表示没找到这个dom节点
$('div span:first-child').css('background','pink');
//对于div的子元素从第一个span开始数起
$('div span:first-of-type').css('background','blue');
```

###### 表单筛选

- `:button`：所有类性为`button`的 `input` 元素

- `:checkbox`：所有类性为`checkbox`的 `input` 元素

- `:radio`：所有类性为`radio`的 `input` 元素

- `:checked`：所有选中的复选框选项

- `:disabled`：所有禁用的元素

- `:enabled`：所有启用的元素

- `:selected`：所有选中的下拉列表

```javascript
$('input:checkbox').css({'width':'50px',"height":"50px"});
$('input:radio').css({'width':'30px',"height":"30px"});
$('input:checked').css({'width':'100px',"height":"100px"});
```

###### 筛选方法

- `filter()` ：所有指定类名的该元素
- `not()`：所有不是指定类型的该元素
- `has()`:所有包含有指定元素的元素
- `is`：判断元素是否为指定元素

```javascript
//返回带有类名"intro"的所有<p>元素
$("p").filter(".intro")
//返回不带有类名 "intro" 的所有 <p> 元素
$("p").not(".intro")
//选取所有包含有 <span> 元素在其内的 <p> 元素
$("p:has(span)")
//如果 <p> 的父元素是 <div> 元素，弹出提示信息
if ($("p").parent().is("div")) {
    alert("p 的父元素是 div");
}
```

##### 属性选择器

- [ = ]  ：拥有此属性的
- [ ^= ]：以此开头的
- [ $= ]：以此结束的
- [ *= ]：有此

```javascript
<body>
    <div class="b1 b2">我是div</div>
<div class="b1" id="box">我是div1</div>
<div class="b2">我是div2</div>
<div class="b2b2">我是div3</div>
<div class="b2_333">我是div4</div>
<div class="b2-ccc">我是div5</div>
<script type="text/javascript">
    $(function(){
    //[class="b1 b2"]  拥有这个class属性的这样的div
    $('div[class="b1 b2"]').css('background','blue');
    //^  以***开头的样式
    $('div[class^="b2"]').css('color','yellow');
    //[$=]  以*** 结束
    $('div[class$="b2"]').css('font-size','34px');
    //[*=]  有***
    $('div[class*="b2"]').css('text-align','center');
    //单引号中 再有引号的话,需要写双引号
})
</script>
</body>
```

##### 链式操作

在同一行里面，写多个交互或动作，称为链式操作

```javascript
$('#box').html('hello world').css({"width":"100px","height":"100px","background":"lightblue"}).click(function(){
    $(this).css('color','yellow');
});
```

##### 容错处理

- 使用`jQuery`选择器不仅比使用传统的`getElementById()`和`getElementsByTagName()`函数简洁得多，而且还能避免某些错误。

- `jQuery`获取网页中不存在的元素也不会报错。

##### class操作

- `addClass()` 添加一个节点
- `removeClass()` 删除一个节点
- `toggleClass` 添加/删除 切换

```javascript
//增加
$oBtn1.click(function(){
    $oDiv.addClass('color');
});
//减少
$oBtn2.click(function(){
    $oDiv.removeClass('green');
});
//点一次增加,再点一次减少
$oBtn3.click(function(){
    $oDiv.toggleClass('red');
})
```

##### 显示和隐藏

- `show()`  显示
- `hide()` 隐藏
- `toggle()` 显示/隐藏 切换

```javascript
$oBtn1.click(function(){
    $oDiv.show();
});
//隐藏
$oBtn2.click(function(){
    $oDiv.hide();
});
//显示或隐藏
$oBtn3.click(function(){
    $oDiv.toggle();
});
```

##### 索引

- `eq()` 该为jq的索引

##### 节点的选择

- `first()`：第一个节点
- `last()`：最后一个节点
- `slice()`：区间，索引来查找，不包括后面的值
- `children()`：子节点
- `find()`：查找规定的子元素类型

```javascript
$('span').first().css('background','red');

//last
$('span').last().css('background','green');

//slice  区间 小标从0开始,不包括最后面的值  [2,5)
$('span').slice(2,5).css('background','blue');

//children 子节点
$('ul').children().css('color','lightblue');

//find  查找子元素  必须规定查找的子元素是什么类型
$('ul').find('li').css('background','pink');
```

- `prev()` ：上一个
- `next()`：下一个
- `prevAll()`：下面所有
- `nextAll( )`：上面所有
- `siblings()`：兄弟节点

```javascript
<body>
    <div id="box">dsfdsf</div>
<span>11111</span>
<span>222</span>
<span>333</span>
<p>p1</p>
<div>呀呀呀呀呀呀晕晕晕晕晕</div>
<span>11111</span>
<span>222</span>
<p>p2</p>
<span>11111</span>
<span>222</span>
<p>p3</p>
<script type="text/javascript">
    $(function(){
    //next 下一个  紧挨着p的下一个元素
    $('p').next('span').css('background','red');

   //prev 上一个
  $('p').prev('span').css('background','green');

    //nextAll  p下面的所有span
  $('p').nextAll('span').css('background','yellow');

    //prevAll  p上面的所有span
  $('p').prevAll('span').css('background','blue');
    //siblings 兄弟节点 
  $('#box').siblings('p').css('color','orange');

    </script>
    </body>
```

- `parent()`：父级节点
- `parents()`：所有父级
- `closest()`：最近的节点

```javascript
<body>

    <ul class="bb">
        <li class="bb">111111111111<span>选择</span></li>
            <li>222 <span>选择</span></li>
                <li class="bb">333 <span>选择</span></li>
                    <div>4444 <span>选择</span></div>
                        </ul>
<script type="text/javascript">
    $(function(){
    //parent 选择父级
    $('span').parent().css('background','lightblue');
    //span 的所有父级
    $('span').parents().css('background','yellow');
    //closest 最近的节点
    $('span').eq(0).closest('.bb').css('background','green');
})
</script>
</body>
```

##### 创建节点

在`$()`里面添加标签名或者属性

```javascript
$span = $('<span>何时了</span>');
```

##### 添加节点

- `insertBefore( )`   `before()`    在某个标签的前面添加节点
- `insertAfter()`   `after()`     在某个标签的后面添加节点    
- `appendTo()`     `append()`	       在摸个标签的里面的最后面添加
- `prependTo()`      `prepend()`     在某个标签里面的最后面添加

##### 节点操作

- `remove()`：删除节点
- `clone()` ：克隆节点

```javascript
$('#b2').remove();
var newSpan = $('#b1 span').clone();
```

##### 索引

`index()`:查找索引

```javascript
console.log($('div').index());
```

##### 遍历

`each()`

```javascript
<script type="text/javascript">
    $('li').each(function(i,elem){
    //i 下标
    //elem dom 元素
    console.log(this);
    console.log($(this));//$(this)  $(elem) 一样
    if(i%2 == 0){//偶数
        $(elem).css('background','lightblue');
    }else{
        $(elem).css('background','yellow');
    }
    return true;
    //return false;循环只执行一次,下面的循环会中断
})
</script>
```

##### 包装对象

- `wrap()`：在原有标签外面再加一层
- `wrapAll()`：将所有的选中标签放一起，再在外层添加一层标签，会改变整个结构
- `wrapInner()`：将原有标签的里面再添加一层标签
- `unwrap()` ：去掉选中节点的父级标签

```javascript
//包装对象
$('span').wrap('<p>');//在原有标签的外面再加一层标签

//整体包装
$('span').wrapAll('<p>');

$('span').wrapInner('<li>');//在原有标签的里面再添加一层标签

$('span').unwrap();//去掉dom节点的外层标签
```

##### JQ转原生JS

`get( )`

```javascript
$('video').get(0).play()
```

##### 元素的尺寸

- `width()`  
- `height()`
- `innerWidth()`
- `innerHeight()`
- `outerWidth()`
- `outerHeight()`

```javascript
console.log($('#box').width());//width
console.log($('#box').height());//height
console.log($('#box').innerWidth());//width+padding*2
console.log($('#box').innerHeight());//height+padding*2
console.log($('#box').outerWidth());//width+padding*2+border*2
console.log($('#box').outerHeight());//height+padding*2+border*2
console.log($('#box').outerWidth(true));//width+padding*2+border*2+margin*2
console.log($('#box').outerHeight(true));//height+padding*2+border*2+margin*2
//可视区的宽高
console.log($(window).width());
console.log($(window).height());

//文档的宽高
console.log($(document).width());
console.log($(document).height());
```

##### 滚动距离

`scrollTop()`:纵向 滚动距离

`scrollLeft()`：横向滚动距离

```javascript
$(document).scrollTop(300);
$(document).scrollLeft(400);
```

##### 元素距离

- `offset()`
  - left
  - top
- `position` (不会识别本身的`margin`值)
  - left
  - top

```javascript
console.log($('#div1').offset().top);
console.log($('#div1').offset().left);
console.log($('#div1').position().top);
console.log($('#div1').position().left);
```

##### 找父级位置

`offsetParent()`

```javascript
console.log($('#div2').offset().left - $('#div2').offsetParent().offset().left);
```

##### 事件

- `on()` ：开启事件
- `off()`：关闭事件

```javascript
$('button').on('click mouseover',function(){
    console.log(666);
    //关闭
    $('button').off();
});
```

##### event事件

- `which`：按键码
- `target`：节点本身

```javascript
$('#box').on('click',function(ev){
    console.log(ev);
    console.log(ev.pageX);// 点击的点与文档的左侧的距离
    console.log(ev.pageY);//点击的点与文档的上部的距离
    console.log(ev.clientX);//点与可视区的 左侧的距离
    console.log(ev.clientY);//点与可视区的 上部的距离
    console.log(ev.target);//dom  节点本身

})

$(document).on('keydown',function(ev){
    console.log(ev.which);//按键码

})
```

- `stopPropagation()`

```javascript
<body>
    <div id="div1">111
		<div id="div2">222
			<div id="div3">333</div>
		</div>
	</div>
<script type="text/javascript" src="../js/jquery-3.4.1.js"></script>
<script type="text/javascript">
    $(function(){
    //对三个div绑定点击事件
    $('#div1').on('click',function(){
        console.log(1111111111);

    });
    $('#div2').on('click',function(ev){
        console.log(222222222);
        ev.stopPropagation();//阻止冒泡

    });
    $('#div3').on('click',function(){
        console.log(3333333);

    });

})
</script>
```



- `preventDefault()`
- `return false`

   ```javascript
   var oUl = $('ul');
   $(document).on('contextmenu',function(ev){
    console.log('右键菜单触发了');
    //获取点击的那个点的坐标
    var x = ev.clientX;
    var y = ev.clientY;
    oUl.css('top',y);
    oUl.css('left',x);
    oUl.css('display','block');
    // 阻止默认事件
    //ev.preventDefault();
    return false;
   });
   ```

//点击左键隐藏
$(document).on('click',function(){
​    oUl.css('display','none');

})
   ```

##### 事件委托

- `delegate()`
  - `ev.delegateTarget`
  - `undelegate()`

​```javascript
	
//使用委托
$('ul').delegate('li','click',function(ev){
    $(this).css('background','blue');

    //取消委托
    $(ev.delegateTarget).undelegate();
});
// //创建新li  委托,可以拥有原来li绑定的事件
var oLi = $('<li>aaaaaaaaaaa</li>');
$('ul').append(oLi);//新添加的节点不具备原来li绑定的事件

})
   ```

##### 事件的主动触发

`trigger()`

```javascript
$('#btn').on('click',function(){
    //2. 新建li  
    var oLi = $('<li>');
    //将txt框中的内容赋值给li   
    oLi.html($('#txt').val());
    //3.将li添加到ul
    $('ul').append(oLi);

})
$(document).on('keydown',function(ev){
    if(ev.which == 13){
        //主动触发 按钮点击事件
        $('#btn').trigger('click');
    }
})
```

##### 事件命名空间

```javascript
//给div绑定点击事件
$('#div1').on('click.a2',function(){
    console.log(124);
});
//*****.a1 命名空间
$('#div1').on('click.a1',function(){
    console.log(666);
});
```

##### 工具方法

- `$.type()`：判断数据类型
- `$.isFunction()`：判断是否是函数类型
- `$.isNumber()`：判断是否是数值类型
- `$.isArray()`：判断是否是数组类型
- `$.isWindow()`：判断是否是window对象
- `$.isEmptyObject()`：判断该对象是否为空
- `$.isPlainObject()`：判断对象是否是纯粹的对象

```javascript
console.log($.type(a));
console.log($.isFunction(a))
console.log($.isPlainObject(aaa))
console.log($.isPlainObject(new Object()));//true
```

##### 工具方法2

- `$.parseJSON()`：将字符串转为json对象
- `$.parseHTML()`：将字符串转 html 
- `$.parseXML()`：将字符串转 XML
- `$.isMXLDoc()`： 判断是否是 xml的节点类型

```javascript
//1.$.parseJSON 将字符串转为json对象
var a = '{"name":"lili"}';
var myjson = $.parseJSON(a);
console.log(myjson);

//2.将字符串转 html 
var b = '<div>3333333</div>';
var c = $.parseHTML(b);//转为jquery的dom节点
console.log(c);

//3.$. parseXML()  将字符串转 XML
var d = '<?xml version="1.0" encoding="utf-8"?><hello>helloworld!</hello>';
var e = $.parseXML(d); 
console.log(e);

//4.$. isXMLDoc()  判断是否是 xml的节点类型
console.log($.isXMLDoc(e));
console.log($.isXMLDoc(d));
```

##### ajax工具方法

`$.ajax()`

```javascript
$.ajax({
    url:'post.php',//访问的url地址
    type:'post',//ajax提交方式
    data:{user:$('input').eq(0).val(),pwd:$('input').eq(1).val()},//传递的数据
    dataType:"text",//数据的返回类型  text  json  jsonp  xml  
    success:function(data){//成功的回调
        console.log(666);
        console.log(data);
    }
})
```

`$.get()`

```javascript
//1.参数:url,成功的回调函数
 $.get('test.json',function(data){
 	console.log(data);
 	//2.渲染到页面上
 	$('#con').html(data.id+":"+data.name+"-"+data.age);
 });
```

`$.getJSON()`

```javascript
$.getJSON('test.json',function(data){
    console.log(data);
    //2.渲染到页面上
    $('#con').html(data.id+":"+data.name+"-"+data.age);
});
```

`$.post()`

```javascript
//将数据提交到后台
$.post(
    'post.php',//url地址
    {"user":$('input').eq(0).val(),"pwd":$('input').eq(1).val()},//给后台的传参
    function(data){//成功的回调函数
        console.log(data);
        //渲染
        $('#con').html(data);
    });
```

###### 跨域

Jsonp(JSON with Padding) 是 json 的一种"使用模式"，可以让网页从别的域名（网站）那获取资料，即跨域读取数据。

为什么我们从不同的域（网站）访问数据需要一个特殊的技术( JSONP )呢？这是因为同源策略。

同源策略，它是由 Netscape 提出的一个著名的安全策略，现在所有支持 JavaScript 的浏览器都会使用这个策略。

----------------------

PHP配置文件的callback属性

```php
<?php
header('Content-type: application/json');
//获取回调函数名
$jsoncallback = htmlspecialchars($_REQUEST ['jsoncallback']);
//json数据
$json_data = '["customername1","customername2"]';
//输出jsonp格式的数据
echo $jsoncallback . "(" . $json_data . ")";
?>
```

`javascript属性`

```javascript
//调用ajax
$.ajax({
    url:'http://127.0.0.1/ajax/getNews.php',//访问的url地址
    type:'get',//ajax提交方式
    data:{user:$('input').eq(0).val(),pwd:$('input').eq(1).val()},//传递的数据
    dataType:"jsonp",//数据的返回类型  text  json  jsonp  xml
    jsonp:"callback",//jsonp的格式  ,需要后台支持
    success:function(data){//成功的回调
        console.log(666);
        console.log(data);
    }
})
})	
```

##### 继承

`$.extend()`：深拷贝

```javascript
//拷贝一层
var a = {"name":"lili"};
 var b = {};
 $.extend(b,a);
 b.name="华兴";
 console.log(a);
 console.log(b);

//拷贝多层
var a = {"name":"lili","xinxi":{"age":20,"sex":"男","tt":{"a":1,"b":2}}};
var b = {};
$.extend(true,b,a);//深拷贝多层
b.xinxi.sex="女";//  
b.xinxi.tt.b = 5;
console.log(a);
console.log(b);


```

##### this指向

`$.proxy()`：改变this指向

```javascript
$(document).on('click',function(){
    setTimeout($.proxy(function(){
        console.log($(this));//document
   $(this).find('body').css('background','blue');
    },this),300);

})
```

##### 显示隐藏动画

分别是显示、隐藏、显示隐藏切换！

- `show()`、`hide()`、`toggle()`  ：正常的显示隐藏无特效
- `fadeIn()`、`fadeOut()`、`slideToggle()`：慢慢淡化
- `slideDown()`、`slideUp()`、`slideToggle()`：上移下移

参数等级：`fast` | `normal` | `slow`

```javascript
//显示
$('input').eq(0).on('click',function(){
    $('#box').show();
    $('#box').fadeIn();//opacity 从 0-1效果
    $('#box').slideDown('slow');
})
//隐藏
$('input').eq(1).on('click',function(){
    $('#box').hide();
    $('#box').fadeOut();
    $('#box').slideUp('slow');//从下向上收起
})
//切换
$('input').eq(2).on('click',function(){
    $('#box').toggle();
    $('#box').fadeToggle();
    $('#box').slideToggle('slow');
})			
```

##### 开启动画

`animate()`：动画效果

```javascript
$('input').on('click',function(){
    //给div做运动效果
    //参数   :        需要更改的css样式,运动时间,运动形式,运动完成后执行的函数
    $('#con').animate({width:"400px"},2000,'linear',function(){
        alert(666);
    });
})
```

`delay()`：延长时间

```javascript
$('input').on('click',function(){
    //给div做运动效果
    //参数   :        需要更改的css样式,运动时间,运动形式,运动完成后执行的函数
    $('#con').animate({width:"400px"},2000,'linear',function(){
        console.log(666);
    });
    
    //delay 延迟多长时间
 $('#con1').delay(2000).animate({width:"400px"},2000,'linear').delay(2000).animate({height:"400px"},2000,'linear');
})
```

##### 停止动画

`stop()`：暂停

`finish()`：停止

```javascript
//开始
$('input').eq(0).on('click',function(){
    $('#box').animate({width:600},3000);

})
//暂停
$('input').eq(1).on('click',function(){
    $('#box').stop();

})
//停止
$('input').eq(2).on('click',function(){
    $('#box').finish();//动画不在进行,直接结束点

})
```

### `jQuery`中模板引擎

`jQuery`系的`MVVM`框架

```javascript
//模板
<script type="text/x-jsrender" id="j-specCard">
    <table>
    <tr>
    <td>Name: {{:name}}</td>
<td>Age: {{:age}}</td>
</tr>
</table>
</script>
//逻辑
(function(jq, g) {
    //传入一个简单对象
    var data = {
        'name': 'alice',
        'age': 18
    },
        //获取模板
        jsRenderTpl = $.templates('#j-specCard'),
        //末班与数据结合
        finalTpl = jsRenderTpl(data);

    $('.box').html(finalTpl);
})(jQuery, window);
```

### MVVM

`MVVM`是`Model-View-ViewModel`的简写。它本质上就是`MVC` 的改进版。`MVVM` 就是将其中的View 的状态和行为抽象化，让我们将视图 `UI` 和业务逻辑分开。当然这些事` ViewModel` 已经帮我们做了，它可以取出` Model `的数据同时帮忙处理 `View `中由于需要展示内容而涉及的业务逻辑。微软的`WPF`带来了新的技术体验，如`Silverlight`、音频、视频、`3D`、动画，这导致了软件`UI`层更加细节化、可定制化。同时，在技术层面，`WPF`也带来了 诸如`Binding`、`Dependency Property`、`Routed Events`、`Command`、`DataTemplate`、`ControlTemplate`等新特性。`MVVM（Model-View-ViewModel）`框架的由来便是`MVP（Model-View-Presenter）`模式与`WPF`结合的应用方式时发展演变过来的一种新型架构框架。它立足于原有`MVP`框架并且把`WPF`的新特性糅合进去，以应对客户日益复杂的需求变化。

### 单元测试

前端单元测试是一项很重要对项目组成部分，特别是对于JavaScript这样弱类型语言。顾名思义，就是对软件对某块单元进行测试，只有很好地完成单元测试，才能更好地进一步完成集成测试、功能测试等等。

----------------

###### 测试驱动开发

TDD：Test-driven development：测试驱动开发

- 设计理念是通过单元测试来推动设计开发流程
- 从代码角度触发，能更好地解决某个单元本身的问题

###### 行为驱动开发

BDD：Behavior-Driven Development：行为驱动开发

- 设计理念是通过预期行为以构建功能模块，推动设计开发流程
- 从用户的角度来看，能更好的解决需求和开发脱节问题

----------------------------

###### 测试开发工具

- Node assert
  - assert是Node自带的一个断言工具，有10多个断言测试的函数
    - 特点是小，Node自带，方便在Node环境使用
- Mocha
  - 是现在最流行的JavaScript测试框架之一
    - 在浏览器和Node环境都能使用
    - 不含断言和仿真，需要选择相应工具，这也造就了它灵活的特点
- Karma   
  - 前身是Testacular
    - 是一个测试runner，它需要测试框架，比如Karma+Mocha结合使用
    - 支持多语言、多浏览器、仿真
    - 支持对测试文件变化的监听（可配置）

```javascript
<script>
    //单元测试
    QUnit.test("hello test",function(assert){
    //断言个数
    assert.expect(8);

    //断言
    assert.ok(1== '1');//true 
    assert.ok(1==='1');//false

    //对值进行比较
    var a = 123;
    assert.equal(a,1234);
    assert.equal(a,123);
    assert.equal($.type(a),'number');

    //dom 节点的操作
    $('#div1').css('width','200px');
    assert.equal($('#div1').css('width'),'100');
    assert.equal($('#div1').css('width'),'200px');
    assert.ok([]==[]);
});
</script>
```

### Mobile

- 是创建移动web应用程序的框架
- 适用于所有流行的智能手机和平板电脑
- 使用HTML5和CSS3通过尽可能少的脚本对页面进行布局

```javascript
<script>

    //引用 swiper插件  更优的选择
    $(function(){
    var iNow = 0;// 轮播 初始值

    //向左滑动
    $('#div1').on('swipeleft',function(){
        if(iNow !=4){
            iNow++;	
        }

        $(this).find('ul').animate({left:-iNow*375});	
    });

    $('#div1').on('swiperight',function(){
        if(iNow !=0){
            iNow--;
        }
        $(this).find('ul').animate({left:iNow*375});
    })

})

</script>
</head>
<body>
    <!--首页-->
<!--data-theme 主题  a,b,c-->
<div id="index" data-role="page" data-theme="b">
    <!--头部-->
<div data-role="header">
    <h1>前端课程</h1>
</div>
<!--内容-->
<div data-role="content">
    <ul data-role="listview"><!--列表-->
<li><a href="#">html5</a></li>
    <li><a href="#">css3</a></li>
        <li><a href="#jq">jquery</a></li>
            </ul>
</div>
<div id="div1">
    <ul>
    <li><img src="../img/1.jpg" /></li>
<li><img src="../img/2.jpg" /></li>
<li><img src="../img/3.jpg" /></li>
<li><img src="../img/4.jpg" /></li>
<li><img src="../img/5.jpg" /></li>
</ul>
</div>
<div data-role="footer">
    <ul data-role="navbar">
        <li><a href="#">首页</a></li>
            <li><a href="#">关于我们</a></li>
                <li><a href="#">联系我们</a></li>
                    </ul>
</div>
</div>
<!--二级页面-->
<div id="jq" data-role="page">
    <div data-role="header">
        <h1>jquery知识</h1>
<a href="#index" class="ui-btn-right" data-icon="arrow-l" data-iconpos="notext">返回</a>
</div>
<div data-role="content">
    <ul data-role="listview">
        <li><a href="#index" data-role="button" data-inline="true" data-rel="dialog">第一季</a></li>
            <li><a href="#">第二季</a></li>
                <li><a href="#">第三季</a></li>
                    </ul>
</div>
<div data-role="footer">
    <ul data-role="navbar">
        <li><a href="#">首页</a></li>
            <li><a href="#">关于我们</a></li>
                <li><a href="#">联系我们</a></li>
                    </ul>
</div>
</div>
</body>
```

### JQ—UI

jQuery UI 是建立在 jQuery JavaScript 库上的一组用户界面交互、特效、小部件及主题

```javascript
<script type="text/javascript">
    $(function(){
    $('input').eq(0).on('click',function(){
        //$('#div1').animate({width:400,height:400},1000,'easeOutBounce');//easeOutBounce
        $('#div1').addClass('box',1000,'linear');

        //$('#div1').show('drop',2000);
    })
    $('input').eq(1).on('click',function(){
        //$('#div1').animate({width:400,height:400},1000,'easeOutBounce');//easeOutBounce
        $('#div1').removeClass('box',1000,'linear');

        //$('#div1').show('drop',2000);
    })

})
</script>
```

- 动画

```javascript
$('input').on('click',function(){
    //显示
    //$('#div1').show(1000);
    //参数：  显示效果,显示时间
    //$('#div1').show('explode',1000);
    //方向
    //参数：  显示效果, 显示方向,显示时间
    //$('#div1').show('slide',{direction:'right'},1000);

    //toggle 点一次显示,再点一次隐藏
    //$('#div1').toggle('slide',{direction:'right'},1000);

    //effect  可以多次点击显示
    $('#div1').effect('shake',{direction:'right'},1000);
})
```

- 拖放

```javascript
<script>
    $(function(){

    $('#div1').draggable({
        axis:'x',//只能在x轴上拖动
        cursor:'move',// 改变鼠标的样式
        handle:'span'//是不是作用于span才有效果
    })

    $( "#div1" ).draggable();
    // var onoff = true;
    // $('input').on('click',function(){
    // 	if(onoff){
    // 		//拖动
    // 		$( "#div1" ).draggable();
    // 		//$('#div1').draggable('instance').disable();
    // 	}else{
    // 		//$('#div1').draggable();
    // 	}
    // 	onoff = !onoff;
    // })

})
```

