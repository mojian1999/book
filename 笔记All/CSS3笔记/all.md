# CSS3



## 属性选择器

重点：    E[attr*="value"]

​	指定了属性名，并且有属性值，而且属值中包含了value

其他: 

​	    E[attr]只使用属性名，但没有确定任何属性值

​            E[attr="value"]指定属性名，并指定了该属性的属性值

​            E[attr~="value"]指定属性名，并且具有属性值，此属性值是一个词列表，并且以空格隔开，

​            其中词列表中包含了一个value词，而且等号前面的“〜”不能不写

​            E[attr^="value"]指定了属性名，并且有属性值，属性值是以value开头的

​            E[attr$="value"]指定了属性名，并且有属性值，而且属性值是以value结束的	

​	    E[attr|="value"]指定了属性名，并且属性值是value或者以“value-”开头的值（比如说zh-cn）

```css3
 p{height: 30px; border:1px solid red;}
		   p[name] {background: lightblue;}
		   p[name="test"]{color:green;}
		   p[name ~= "test"]{text-align:center ;}
		   p[name ^="te"]{font-size:36px;}
		   p[name $="1"]{text-align: right;}
		   p[name *="yy"]{text-decoration: line-through;}
		   p[name |="test"]{font-weight: bold;}
```

## 结构性伪类

重点 ：

p:nth-child(odd){background:red}         匹配奇数行  

p:nth-child(even){background:red}        匹配偶数行  

E:nth-of-type(n)  表示E父元素中的第n个子节点且类型为E , 在计算个数时只计算 类型为E的

其他：

E:nth-child(n)  E元素的父级的子节点的第n个,这个元素是 E可以显示效果，不是E就不显示效果

p:nth-child(2n){background:red}E:nth-last-child(n) 表示父元素中的第n个子节点从后向前计算

E:nth-last-of-type(n)表示E父元素中的第n个子节点，且类型为E,从后向前计算

E:empty 表示E元素中没有子节点。注意：子节点包含文本节点

```css3
p{height:30px; border:1px dotted #000;}
p:nth-child(3){background: lightblue;}
p:nth-child(odd){background: red;}
p:nth-child(even){background: green;}
p:nth-child(3n){color:#fff;} 
p:nth-child(3n+1){color:pink;}
p:nth-of-type(5){text-align:center;}
p:nth-last-of-type(2){text-decoration: line-through;}
p:empty{border:2px soild blue;}
```

## 伪类

E:target 表示当前的URL片段的元素类型，这个元素必须是E

E:disabled 表示不可点击的表单控件

E:enabled 表示可点击的表单控件

E:checked 表示已选中的checkbox或radio

E:first-line 表示E元素中的第一行

E:first-letter 表示E元素中的第一个字符

E::selection表示E元素在用户选中文字时

E:before 生成内容在E元素前

E:after 生成内容在E元素后

```CSS3
div{width:100px; height: 100px; background: blue; margin: 10px;}
div:target{background: pink;}
input:disabled{color:red;}
input:enabled{color:green;}
input:checked{color:green; width: 40px; height: 40px;}
.wz{borde:1px solid blue; padding:10px; margin: 10px;}
.wz:first-line{background: lightcoral;}
.wz:first-letter{color:blue;}
.wz::selection{color:blue; background: yellow;}
/*content before或者after的内容*/
.wz:before{content:"习大大新闻";font-size: 20px; font-weight: bold;}
.wz:after{content: "小节：建设社会主义新世界"; color:orange;}
```

## 三原色

- r  g  b  a颜色模式

​            红(0-255) 绿 蓝  透明(0-1)  

- hsla颜色模式

​           H：Hue(色调)。0(或360)表示红色，120表示绿色，240表示蓝色，也可取其他数值来指定颜色。取值为：0 - 360

​           S：Saturation(饱和度)。取值为：0.0% - 100.0%

​           L：Lightness(亮度)。取值为：0.0% - 100.0%

​           A：Alpha透明度。取值0~1之间。

```CSS3
body{background: url(../img/1.png);}
			div{width: 200px; height: 200px; background: rgba(255,0,0,0.5);
			color:rgba(0,255,255,0.5); font-size: 80px;border:50px solid rgba(0,0,255,0.5);
			}
```

## 浏览器前缀

​	-webkit-  ：	chrome 苹果

​	-moz-      : 	火狐浏览器

​	-ms-    	: 	IE浏览器

​	-o-      	: 	欧朋浏览器

### 文字阴影

- 格式：

text-shadow:     10px          10px        10px          yellow;

文字阴影          x轴偏移       y轴偏移    模糊距离      颜色

```CSS3
.box{font-size:80px; color:blue; text-shadow: 10px 10px 10px yellow;}

.box2{font-size:80px; color:blue; text-shadow: 10px 10px 10px yellow,20px 20px 20px green;}

.box3{font-size:80px; color:red; font-size:100px; font-weight:bold; text-shadow:2px 2px 0px white, 4px 4px 0px red;}

.box4{font-size:80px;color:white;margin-top:100px; font-size:100px; text-shadow:0 0 10px #fff, 0 0 20px #fff, 0 0 30px #fff, 0 0 40px #ff00de, 0 0 70px #ff00de, 0 0 80px #ff00de, 0 0 100px #ff00de, 0 0 150px #ff00de;}

.box5{font-size:80px;margin-top:100px;text-shadow: 0 0 20px #fefcc9, 10px -10px 30px #feec85, -20px -20px 40px #ffae34, 20px -40px 50px #ec760c, -20px -60px 60px #cd4606, 0 -80px 70px #973716, 10px -90px 80px #451b0e; font-family:Verdana, Geneva, sans-serif; font-size:100px; font-weight:bold; color:white;}

.mb{font-size:80px;  -webkit-text-stroke: 3px yellow;}
```

## 文字新添的样式

Direction 

 定义文字排列方式(全兼容)     Rtl 从右向左排列Ltr 从左向右排列

​	注意:要配合unicode-bidi 一块使用

​            

 Text-overflow 

​            定义省略文本的处理方式clip  

​            无省略号Ellipsis 

​            省略号 (注意配合overflow:hidden和white-space:nowrap一块使用)

```CSS3
.dir{width: 200px; height: 100px; border:1px solid blue; direction: rtl;
			unicode-bidi: bidi-override;
}

.slh{width: 300px; border:1px solid green; margin-top: 10px;
	text-overflow: ellipsis; overflow: hidden; white-space: nowrap;
 }
```

## 弹性盒模型

display:  -webkit-box; 盒子中的排列是 属于盒模型效果

​           	-webkit-box-direction:x轴的排列方向 reverse（从右向左） normal(从左向右)

​                -webkit-box-orient:y轴的排列方向  vertical 纵向排列   horizontal(水平排列) 

```CSS3
.box{
				height:100px; width: 90%; border:4px solid blue; display: -webkit-box;
				-webkit-box-direction:normal ;
				-webkit-box-orient:horizontal;
}
-webkit-box-ordinal-group:设置某一个小盒子的位置

.box div{
		height: 80px; 
		width: 80px; 
		background: yellow;
        border:1px solid red; 
 }
.box div:nth-of-type(2){-webkit-box-ordinal-group: 5;}
.box div:nth-of-type(3){-webkit-box-ordinal-group: 4;}
.box div:nth-of-type(4){-webkit-box-ordinal-group: 3;}
.box div:nth-of-type(5){-webkit-box-ordinal-group: 2;}
```

## 盒子阴影

 box-shadow:    10px       10px          10px                10px                   blue;

盒子阴影：      x轴偏移    y轴偏移    模糊程度        扩展阴影半径       阴影颜色

​                 

box-shadow:inset      10px           10px         10px         10px               blue;

盒子阴影：                 内部阴影    x轴偏移    y轴偏移    模糊程度     扩展阴影半径  阴影颜色

```CSS3
.box{width: 200px; height: 200px; border:1px solid red;box-shadow: 10px 10px 			10px 10px blue; }
			
			
.box1{width: 200px; height: 200px; border:1px solid red;box-shadow:inset 10px 			10px 10px blue; }
```

## 倒影

-webkit-box-reflect 倒影     right右侧    left左侧    below下边   above上边

-webkit-linear-gradient 线性渐变

```CSS3
body{background: #000;margin: 0; padding: 0;}
.img1{margin: 100px; -webkit-box-reflect: right;}
.img2{margin: 100px; -webkit-box-reflect: below;}
.img3{margin: 100px; -webkit-box-reflect: right 10px 
-webkit-linear-gradient(right,rgba(0,0,0,0.7)0, rgba(0,0,0,0) 70%);}
```

## 盒模型

标准盒模型：box-sizing: content-box;  width= width + padding*2+ border*2

怪异盒模型：box-sizing:border-box; width=width

```CSS3
.box{
				width: 100px;height:100px;background: blue;
			}
//标准盒模型
.box .in{
				box-sizing: content-box;
				width:80px;border:5px solid red; margin: 10px; padding:20px; height: 40px; background: yellow;
			}
//怪异盒模型			
.box1{
				width: 100px;height:100px;background: blue;
			}
			.box1 .in{
				box-sizing:border-box;
				width:80px;border:5px solid red; margin: 10px; padding:20px; height: 40px; background: yellow;
			}

```

## 分栏

column-width     栏目宽度

column-count     栏目列数

column-gap         栏目距离

column-rule         栏目间隔线

```CSS3
.fl{width: 800px; border:3px dotted pink;
			column-width: 180px; column-count:4;column-gap:10px;column-rule:1px dotted blue;}
```

-   媒体查询效果   media

  媒体查询作用：使用 一套html，多个css文件来适应不同的屏幕宽度大小，显示出最完美的样式

   ```CSS3
  <link href="css/01.css" rel="stylesheet" media=" screen and (min-width:800px)" />
  <link href="css/02.css" rel="stylesheet" media=" screen and (max-width:800px) and (min-width:600px)" />
  <link href="css/03.css" rel="stylesheet" media=" screen and (max-width:600px) " />
   ```

## 移动端视口

```html
<meta name="viewport" content="width=device-width"/>
```

面试题：

```
移动端布局需要注意的地方：
  1.需要使用 viewport
  2.使用 rem ，% 来适应所有的手机屏幕宽度
  3.使用rem时需要引入 flexible.js 插件，作用：获取不同手机的屏幕宽度，设置了不同的html节点的font-size的值
  4.将编辑器安装 rem2px的插件，能让编辑器自动将px值转为rem而不需要手动计算
  5.需要使用 flex布局
  注意：ui作图，市场上流行使用 iPhone 6,7,8 的宽度尺寸来作图 
```

## 圆角

border-radius  1-4个数字 / 1-4个数字

​	前面是水平，后面是垂直

```html
 <style>
    div{width: 100px; height: 100px; border:2px solid red; background: lightblue; margin: 20px;}
    .box{ border-radius: 10px;}
    .box1{ border-radius: 30%;}
    .box2{ border-radius: 10px 50px;}
    .box3{ border-radius: 10px 30px 50px;}
    .box4{ border-radius: 10px 20px 30px 50px;}
    .box5{ border-radius: 10px 20px 30px 40px / 20px 40px 60px 80px;}
  </style>
```

```html
<body>
  1.四个角都一样的写法
  <div class="box">1</div>
  <div class="box1">1</div>
  2.对角一样的写法
  <div class="box2">1</div>
  3. 3个：斜对角
  border-radius: 左上    右上&左下    右下
  <div class="box3">1</div>
  4. 4个：全部，顺时针
  border-radius: 左上    右上    右下    左下
  <div class="box4">1</div>
  5. 8个参数的效果
  <div class="box5">1</div>
```

## 边框

- 边框图片 border-image

  - border-image-source         引入图片
  - border-image-slice              边框向内偏移
  - border-image-width            边框宽度
  - border-image-repeat           图片排列的方式
    - round  平铺
    - repeat  重复
    - stretch   拉伸

  ```html
   <style>
      /*
      -webkit-border-image: url("../img/border.png") 0             10            stretch（拉伸）repeat(重复)  round(重复)
       边框背景              图片地址                 上下裁切的距离 左右裁切的距离  是否重复
      */
      .box{width: 300px; height: 100px; -webkit-border-image: url("../img/border.png") 0 10 repeat;
      text-align: center; line-height: 100px;color:red;}
      .box1{width: 300px; height: 100px; -webkit-border-image: url("../img/bt_blue.png") 0 10 stretch ;
        text-align: center; line-height: 100px;color:red;}
      .box2{width: 300px; height: 100px;border:10px solid pink;-moz-border-top-colors: red blue purple orange;
        text-align: center; line-height: 100px;color:red;-moz-border-left-colors: #f0f0f0; }
    </style>
  ```

  ```html
  <body>
    <div class="box">天涯何处无芳草</div>
    <div class="box1">天涯何处无芳草</div>
    <div class="box2">天涯何处无芳草</div>
  </body>
  ```

  ## 渐变效果

  linear-gradient

  ```html
  <style>
      div{width:200px; height: 100px; border:1px solid blue; margin:10px;}
      /* -webkit-linear-gradient(top, red,             green);
          线性渐变               方向,开始的渐变点的颜色，结束点的渐变点颜色
      */
      .box{
        background: -webkit-linear-gradient(top,red,green);
      }
      .box1{
        background: -webkit-linear-gradient(left top,red,green);
      }
      .box2{
        background: -webkit-linear-gradient(30deg,red,green); /*30deg 渐变的角度是30度*/
      }
      .box3{
        background: -webkit-repeating-linear-gradient(left,red 0,green 50px); /*-webkit-repeating-linear-gradient 循环渐变*/
      }
      .box4{
        background: -webkit-linear-gradient(left,red 0,green 50px,deeppink 50%,orange 200px); /**/
      }
      .box5{
        background: -webkit-linear-gradient(left,red 0,red 50px,pink 50px, pink 100px, purple 100px, purple 150px, blue 150px, blue 200px); /**/
      }
      .box6{
        background: -webkit-linear-gradient(left,rgba(255,0,0,0),rgba(255,0,0,1)),url("../img/1.jpg"); /*多背景中间用逗号分隔*/
      }
      .box7{
        width: 400px; height: 20px;
        background: -webkit-repeating-linear-gradient(30deg,green 0,green 10px,#fff 10px, #fff 20px);
        border-radius: 10px;
      }
    </style>
  </head>
  <body>
    1.从上到下，从红变绿
    <div class="box">1111</div>
    2.渐变方向发生变化，从红变绿
    <div class="box1">1111</div>
    <div class="box2">1111</div>
    3.循环渐变
    <div class="box3">1111</div>
    4.加入渐变点的位置
    <div class="box4">1111</div>
    5.跳变
    <div class="box5">1111</div>
    6.使用rgba，多背景
    <div class="box6">1111</div>
    7.进度条
    <div class="box7"></div>
  </body>
  ```

## 径向渐变

radial-gradient

```html
 <style>
    div{width:200px; height:200px; border:1px solid red; border-radius: 50%}
    .box{background: -webkit-radial-gradient(red,green);}
    .box1{background: -webkit-radial-gradient(red,green,yellow,lightgoldenrodyellow);}
    .box2{background: -webkit-radial-gradient(50px           100px,red 0,green 20%,blue 50%,purple 100%);}
    /*                                        圆心点坐标的x轴，y轴*/
    .box3{background: -webkit-radial-gradient(50px           100px,circle,red 0,green 20%,blue 50%,purple 100%);}
    /*                                        圆心点坐标的x轴，y轴,  圆心的形状     */
    .box4{background: -webkit-radial-gradient(50px           100px,100px 20px,red 0,green 20%,blue 50%,purple 100%);}
    /*                                        圆心点坐标的x轴，y轴,  圆心的大小     */
    .box5{background: -webkit-radial-gradient(50px           100px,contain,red 0,green 20%,blue 50%,purple 100%);}
  </style>

</head>
<body>
  1.基础径向渐变效果
  <div class="box">1111</div>
  2.添加渐变点
  <div class="box1">1111</div>
  3.规定圆心形状
  <div class="box2">1111</div>
  <div class="box3">1111</div>
  4.规定圆心的大小
  <div class="box4">1111</div>
  5.特殊设定：最近端，最近角，最远端，最远角，包含或覆盖 (closest-side, closest-corner, farthest-side, farthest-corner, contain or cover)
  <div class="box5">1111</div>
</body>
```



## 遮罩

Mask-image       遮罩图片
Mask-position    遮罩位置
Mask-repeat       遮罩是否重复

```html
<style>
    div{width: 800px; height: 600px; border:1px solid red; background: url("../img/1.png");
    background-size: 100% 100%; -webkit-mask:url("../img/mask.png") no-repeat; transition: 2s;}
    /*transition：2s 动画执行时间是2s*/
    div:hover{-webkit-mask-position: 100% 100%;}
</style>
<body>
  <div>遮罩</div>
</body>
```

## 过渡效果

- transition-property   要运动的属性  （all || [attr] || none）  如果 运动属性没写，所有属性都具备动画效果
- transition-duration 运动时间
- transition-delay 延迟时间
- transition-timing-function 运动形式
- ease：（逐渐变慢）默认值
- linear：（匀速）  使用次数最多
- ease-in：(加速)
- ease-out：（减速）
- ease-in-out：（先加速后减速）
- cubic-bezier 贝塞尔曲线（ x1, y1, x2, y2 ）

```html
<style>
    .bb div{width: 100px; height: 100px; background: red;}
    .bb .box{transition-duration: 2s; transition-property: width; transition-delay: 5s;}
    .bb .box:hover{width: 600px; background: blue;}
    .bb .box1{transition: 2s      3s       width; margin-bottom: 30px;}
    /*                运行时间 延迟时间 运动属性*/
    /**/
    .bb .box1:hover{width: 600px; background: blue;}


    .box2{width: 800px;height: 400px; border:1px solid blue;}
    .box2 div{width: 100px; height:50px; margin-bottom: 10px; background: lightseagreen;}
    .box2 div:nth-of-type(1){transition: 2s ease;}
    .box2 div:nth-of-type(2){transition: 2s linear;}
    .box2 div:nth-of-type(3){transition: 2s ease-in;}
    .box2 div:nth-of-type(4){transition: 2s  ease-out;}
    .box2 div:nth-of-type(5){transition: 2s ease-in-out;}
    .box2 div:nth-of-type(6){transition: 2s cubic-bezier(0.2,0.8,0.3,0.7);}
    .box2:hover div{width: 700px;}
  </style>
</head>
<body>

  <div class="bb">
    1.过渡时间和运动属性
    <div class="box"></div>
    2.过渡效果，将属性写在一起
    <div class="box1"></div>
  </div>

  3.运动形式
  <div class="box2">
    <div>ease</div>
    <div>linear</div>
    <div>ease-in</div>
    <div>ease-out</div>
    <div>ease-in-out</div>
    <div>cubic-bezier</div>
  </div>
</body>
```

## 2D变换

- transform
  - rotate()   旋转函数  取值函数
    - deg  度数
    - Transfrom-origin  旋转的基点
  - skew()     倾斜函数   取值函数
    - skewX()
    - skewY()
  - scale()      缩放函数  取值  正数、负数和小数
    - scaleX()
    - scaleY()
  - translate()     位移函数
    - translateX()
    - translate()

```html
 <style>
    /*旋转*/
    .outer{width: 200px; height:200px; border:1px solid #000; margin: 20px;}
    .outer .box{width: 100px; height: 100px; margin: 50px; background: blue; transition: 0.5s;}
    .outer:hover .box{transform: rotate(720deg);}
    /*                变换效果  : 旋转   720度*/
    /*倾斜*/
    .outer1{width: 200px; height:600px; border:1px solid #000; margin: 20px;}
    .outer1 .box{width: 100px; height: 100px; margin: 50px; background: blue; transition: 0.5s;}
    .outer1:hover .box{transform:skewX(30deg);}/*x轴倾斜*/
    .outer1 .box2{width: 100px; height: 100px; margin: 50px; background: blue; transition: 0.5s;}
    .outer1:hover .box2{transform:skewY(30deg);}/*y轴倾斜*/
    .outer1 .box3{width: 100px; height: 100px; margin: 50px; background: blue; transition: 0.5s;}
    .outer1:hover .box3{transform:skew(15deg,15deg);}/*x,y轴都倾斜*/

    /*缩放*/
    .outer2{width: 200px; height:600px; border:1px solid #000; margin: 20px;}
    .outer2 .box{width: 100px; height: 100px; margin: 50px; background: blue; transition: 0.5s;}
    .outer2:hover .box{transform:scaleX(0.5);}/*x轴缩放*/
    .outer2 .box2{width: 100px; height: 100px; margin: 50px; background: blue; transition: 0.5s;}
    .outer2:hover .box2{transform:scaleY(0.5);}/*y轴缩放*/
    .outer2 .box3{width: 100px; height: 100px; margin: 50px; background: blue; transition: 0.5s;}
    .outer2:hover .box3{transform:scale(0.5,0.5);}/*x,y轴都缩放*/

    /*位移*/
    .outer3{width: 200px; height:600px; border:1px solid #000; margin: 20px;}
    .outer3 .box{width: 100px; height: 100px; margin: 50px; background: blue; transition: 0.5s;}
    .outer3:hover .box{transform:translateX(200px);}/*x轴位移*/
    .outer3 .box2{width: 100px; height: 100px; margin: 50px; background: blue; transition: 0.5s;}
    .outer3:hover .box2{transform:translateY(100px)}/*y轴位移*/
    .outer3 .box3{width: 100px; height: 100px; margin: 50px; background: blue; transition: 0.5s;}
    .outer3:hover .box3{transform:translate(100px,100px);}/*x,y轴都位移*/
  </style>
</head>
<body>
  1.旋转
  <div class="outer">
    <div class="box">旋转</div>
  </div>
  2.倾斜
  <div class="outer1">
    <div class="box">x轴倾斜</div>
    <div class="box2">y轴倾斜</div>
    <div class="box3">xy轴倾斜</div>
  </div>
  3.缩放
  <div class="outer2">
    <div class="box">x轴缩放</div>
    <div class="box2">y轴缩放</div>
    <div class="box3">xy轴缩放</div>
  </div>
  4.位移
  <div class="outer3">
    <div class="box">x轴位移</div>
    <div class="box2">y轴位移</div>
    <div class="box3">xy轴位移</div>
  </div>
</body>
```

## 旋转基点

transform-origin   默认中心位置

left right bottom top    也可以指定具体的像素

```CSS
<style>
    /*默认的基点是div的中心位置
    基点设置可以是 px % left、right、bottom、top
    */
    .box{width: 400px;height: 400px;border:1px solid #000;}
    .box div{width: 100px; height: 100px; background: blue; transition: 2s; transform-origin:200% 200%; border-radius: 50%;}
    .box:hover div{transform: rotate(360deg) scale(0.1);}

    .box1{width: 400px;height: 600px;border:1px solid #000;}
    .box1 .n1{width: 100px; height: 100px; background: blue; transition: 2s;  }
    .box1:hover .n1{transform: translateX(100px) scale(0.5);}
    .box1 .n2{width: 100px; height: 100px; background: yellow; transition: 2s;  }
    .box1:hover .n2{transform:  scale(0.5) translateX(100px);}
  </style>
</head>
<body>
  1.基点操作
  <div class="box">
    <div></div>
  </div>
  2.执行顺序对动画结果是有影响
  <div class="box1">
    <div class="n1"></div>
    <div class="n2"></div>
  </div>
</body>
```

## 过渡完成事件

```html
<head>
  <meta charset="UTF-8">
  <title>过渡完成事件</title>
  <style>
    .box{width: 100px; height: 100px; background: blue; transition: 2s;}
    /*.box:hover{width: 400px;}*/
  </style>
</head>
<body>
  <div class="box" id="bb"></div>
  <script>
    //window.onload 这样写法可以避免错误，当dom的节点还没加载完，调用了该内容
    window.onload = function(){
      //1.定义变量
      var oDiv = document.getElementById('bb');
      //2.绑定事件
      oDiv.onclick = function(){
        oDiv.style.width = 400+'px';
      }
      //3.过渡完成事件
      /*
      obj dom节点
      fn 函数
      * */
      /*transitionend、webkitTransitionEnd 动画执行结束时触发的事件*/
      function addEvent(obj,fn){
        obj.addEventListener('transitionend',fn,false);
        obj.addEventListener('webkitTransitionEnd',fn,false);
      }
      addEvent(oDiv,function(){
        alert('动画结束了！');
      })


    }

  </script>
</body>
```

## 3D变化效果

- transform-style (preserve-3d)   建立3D空间
- Perspective        景深
- Perspective-origin          景深基点
- Transform   新增函数

```html
<head>
  <meta charset="UTF-8">
  <title>3D变换效果</title>
  <style>
    /*
    -webkit-transform-style: preserve-3d; 表示外层里面的内容都可以是3d效果
    perspective:景深，景深越大3d效果越不明显，越小3d效果越明显
    transform: rotateX(180deg) X轴旋转
    */
    .box{width: 100px; height: 100px; padding: 100px; border:5px solid blue;margin: 10px auto;
      -webkit-transform-style: preserve-3d; perspective: 100px; }
    .box div{width: 100px; height: 100px; background: yellow; transition: 3s;}
    .box:hover div{transform: rotateX(180deg)}

    .box1{width: 100px; height: 100px; padding: 100px; border:5px solid blue;margin: 10px auto;
      -webkit-transform-style: preserve-3d; perspective: 100px; }
    .box1 div{width: 100px; height: 100px; background: yellow; transition: 3s;}
    .box1:hover div{transform: rotateY(180deg)}

    .box2{width: 100px; height: 100px; padding: 100px; border:5px solid blue;margin: 10px auto;
      -webkit-transform-style: preserve-3d; perspective: 100px; }
    .box2 div{width: 100px; height: 100px; background: yellow; transition: 3s;}
    .box2:hover div{transform: rotateZ(180deg)}

    .box3{width: 100px; height: 100px; padding: 100px; border:5px solid blue;margin: 10px auto;
      -webkit-transform-style: preserve-3d; perspective: 100px; }
    .box3 div{width: 100px; height: 100px; background: yellow; transition: 3s;}
    .box3:hover div{transform: translateZ(-40px);}
  </style>
</head>
<body>
1、X轴旋转
<div class="box">
  <div>X轴旋转效果</div>
</div>
2、Y轴旋转
<div class="box1">
  <div>Y轴旋转效果</div>
</div>
3、Z轴旋转
<div class="box2">
  <div>Z轴旋转效果</div>
</div>
4、Z轴位移
<div class="box3">
  <div>Z轴位移效果</div>
</div>
</body>
```

## animation 动画

关键帧：keyFrames

​	只需指明开始与结束状态，过程由计算机自动计算

格式：

​	@keyframes  动画名称（此为标识符）{

​	from（开始状态）；

​	to（结束状态）；

}	

```html
<head>
  <meta charset="UTF-8">
  <title>动画效果基础</title>
  <style>
    /*
     animation: 2s          toMove;
     动画效果   动画持续时间  动画要调用的关键帧的名字
    */
    div:nth-of-type(1){width: 100px; height: 100px; background: blue; animation: 2s toMove;}
    /* @keyframes  关键帧
    form 开始帧
    to   结束帧
    */
    @keyframes toMove {
      form{width:100px;}
      to{width: 600px;}
    }

    div:nth-of-type(2){width: 100px; height: 100px; background: green; animation: 2s toMove1;}
    @keyframes toMove1 {
      0%{width:100px;}
      50%{background:red;width:600px}
      100%{width: 300px; background:yellow;}
    }

    div:nth-of-type(3){width: 100px; height: 100px; background: green; animation: 2s toMove2 2;}
    @keyframes toMove2 {
      0%{width:100px;}
      50%{background:red;width:600px}
      100%{width: 300px; background:yellow;}
    }
    /*animation: 2s      toMove3  infinite;
      动画效果 ：动画时间  动画名称 动画循环次数是无限次
    */
    div:nth-of-type(4){width: 100px; height: 100px; background: green; animation: 2s toMove3 infinite;}
    @keyframes toMove3 {
      0%{width:100px;}
      50%{background:red;width:600px}
      100%{width: 300px; background:yellow;}
    }
    /*animation: 2s      2s      toMove3  infinite;
      动画效果 ：动画时间 延迟时间 动画名称  动画循环次数是无限次
        */
    div:nth-of-type(5){width: 100px; height: 100px; background: green; animation: 2s 2s toMove4 infinite;}
    @keyframes toMove4 {
      0%{width:100px;}
      50%{background:red;width:600px}
      100%{width: 300px; background:yellow;}
    }

    /*animation: 2s      2s      toMove3  infinite           linear;
     动画效果 ：动画时间 延迟时间 动画名称  动画循环次数是无限次  运动形式是匀速
       */
    div:nth-of-type(6){width: 100px; height: 100px; background: green; animation: 2s 2s toMove5 infinite linear;}
    @keyframes toMove5 {
      0%{width:100px;}
      50%{background:red;width:600px}
      100%{width: 300px; background:yellow;}
    }
  </style>

</head>
<body>
  1.基础动画 from to
  <div></div>
  2.基础动画 百分比
  <div></div>
  3.运动多次 ，
  <div></div>
  无限次
  <div></div>
  4.动画延迟
  <div></div>

  5.动画形式 和过渡效果是一样的  linear匀速
  <div></div>
</body>
```

## animate 动画

- 调用动画

  animate-name

  animate-duration

- 可选属性

  - animation-timing-function  动画运动形式

  - linear  匀速。

  - ease  缓冲。

  - ease-in  由慢到快。

  - ease-out  由快到慢。

  - ease-in-out  由慢到快再到慢。

  - cubic-bezier(number, number, number, number)：  特定的贝塞尔曲线类型，4个数值需在[0, 1]区间内e

  - animation-delay  动画延迟

    - 只是第一次

  - animation-iteration-count  重复次数

    - infinite为无限次

  - animation-direction  反转

    动画是否重置后再开始播放

    - alternate  动画直接从上一次停止的位置开始执行
    - normal  动画第二次直接跳到0%的状态开始执行


  ```html
  <head>
    <meta charset="UTF-8">
    <title>播放-暂停</title>
    <style>
      div:nth-of-type(1){width: 100px; height: 100px; background: blue; animation: 2s toMove;}
      /*鼠标移上，暂停动画   animation-play-state: paused; 暂停*/
      div:nth-of-type(1):hover{animation-play-state: paused;}
      @keyframes toMove {
        form{width:100px;}
        to{width: 600px;}
      }
    </style>
  </head>
  <body>
  <div></div>
  </body>
  ```

  ```html
  <head>
    <meta charset="UTF-8">
    <title>走口子</title>
    <style>
      .box{width: 400px; height: 400px; border:2px solid deeppink; position: relative; }
      .box div{width:40px; height: 40px; background: orangered; position: absolute; top:0; left:0;
      animation: 2s move infinite linear; animation-direction: alternate;}/*动画重置的效果*/
      @keyframes move {
        0%{}
        25%{top:0; left:360px;}
        50%{top:360px; left:360px;}
        75%{top:360px; left:0;}
        100%{top:0;left:0;}
      }
  
    </style>
  
  </head>
  <body>
    <div class="box">
      <div></div>
    </div>
  </body>
  ```



  ## 无缝滚动

  ```html
  <head>
    <meta charset="UTF-8">
    <title>无缝滚动</title>
    <style>
      html,body,div,ul,li{padding:0;margin:0;}
      ul,li{list-style: none;}
      .box{width: 500px; height: 100px; border:2px solid blue; position: relative;margin: 100px auto;overflow: hidden; }
      .box ul{position: absolute; left:0;top:0; width: 200%;  animation: 2s move infinite linear;}
      .box ul li{float: left; width: 98px; height: 98px; border:1px solid #fff; line-height: 98px; text-align: center;
      font-size: 30px; background: yellow;}
      @keyframes move {
        from{left:0;}
        to{left:-500px;}
      }
    </style>
  </head>
  <body>
    <div class="box">
      <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
        <li>5</li>
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
        <li>5</li>
      </ul>
    </div>
  </body>
  ```

  # Flex  弹性布局

  开启：display：flex

  ​	    display ：-webkit-flex  （safari用）

    采用flex布局的元素，成为Flex容器，它的所有子元素自动成为容器成员，称为Flex项目

  - 水平的主轴和垂直的交叉轴
  - 主轴的开始位置（与边框的交叉点）叫做main start，结束位置叫做cross end
  - 项目默认沿主轴排列，单个项目占据的主轴空间叫做main size，占据的交叉周空间叫做cross size

  ```html
  <head>
    <meta charset="UTF-8">
    <title>flex基础</title>
    <style>
      /*display: flex;  在外层设置 flex 表示内层元素是弹性布局 。弹性布局默认 是横向，
      内容不需要 float ,也不需要 clear
      display: -webkit-flex;针对于 苹果浏览器的
      display:inline-flex; 针对于行内元素的 span  a  i img ...
      */
      .box{width: 800px; height: 400px; border:1px solid blue; display: flex;}
      .box div{width: 100px; height: 100px;}
      .box div:nth-of-type(1){background: red; }
      .box div:nth-of-type(2){background: green; }
      .box div:nth-of-type(3){background: yellow; }
    </style>
  </head>
  <body>
    <div class="box">
      <div>1111</div>
      <div>222222222</div>
      <div>3333333333</div>
    </div>
  </body>
  ```


## 容器的属性

- flex-direction  属性决定主轴的方向

  - row(默认值)：主轴为水平方向，起点在左端
  - row-reverse：主轴为水平方向，起点在右端
  - column：主轴为垂直方向，起点在上方
  - column-reverse：主轴为垂直方向，起点在下方

  ```html
  <head>
    <meta charset="UTF-8">
    <title>flex基础-主轴方向排列</title>
    <style>
      .box{width: 800px; height: 400px; border:1px solid blue; display: flex;
      flex-direction:column-reverse;}
      .box div{width: 100px; height: 100px;}
      .box div:nth-of-type(1){background: red; }
      .box div:nth-of-type(2){background: green; }
      .box div:nth-of-type(3){background: yellow; }
    </style>
  </head>
  <body>
    <div class="box">
      <div>1111</div>
      <div>222222222</div>
      <div>3333333333</div>
    </div>
  </body>
  ```

- flex-wrap    属性定义主轴的换行

  - nowrap（默认）：不换行
  - wrap      :   换行
  - wrap-reverse   ： 反向换行

  ```html
  <head>
    <meta charset="UTF-8">
    <title>flex基础-是否换行</title>
    <style>
      .box{width: 60%; height: 400px; border:1px solid blue; display: flex;
      flex-direction:row; flex-wrap: wrap-reverse;}
      .box div{width: 100px; height: 100px; background: yellow; margin: 10px; border:1px solid #000;}
    </style>
  </head>
  <body>
    <div class="box">
      <div>1111</div>
      <div>222222222</div>
      <div>1111</div>
      <div>222222222</div>
      <div>3333333333</div>
      <div>1111</div>
      <div>222222222</div>
      <div>3333333333</div>
      <div>1111</div>
      <div>222222222</div>
      <div>3333333333</div>
      <div>3333333333</div>
    </div>
  </body>
  ```

- flex-flow   属性是flex-direction是属性和flex-wrap属性的简写形式，默认值是row nowrap

  ```html
  <head>
    <meta charset="UTF-8">
    <title>flex基础-是否换行</title>
    <style>
      .box{width: 60%; height: 400px; border:1px solid blue; display: flex;
      /*flex-direction:row; flex-wrap: wrap-reverse;*/
      flex-flow: column wrap;
      }
      .box div{width: 100px; height: 100px; background: yellow; margin: 10px; border:1px solid #000;}
    </style>
  </head>
  <body>
    <div class="box">
      <div>1111</div>
      <div>222222222</div>
      <div>1111</div>
      <div>222222222</div>
      <div>3333333333</div>
      <div>1111</div>
      <div>222222222</div>
      <div>3333333333</div>
      <div>1111</div>
      <div>222222222</div>
      <div>3333333333</div>
      <div>3333333333</div>
    </div>
  </body>
  ```

- justify-content   属性定义了主轴的对齐方式

  - flex-start（默认值）：左对齐
  - flex-end ：右对齐
  - center  ：居中
  - space-between  ：两端对齐，项目之间的间隔都相等
  - space-around  ： 每个项目两侧的间隔相等

  ```html
  <head>
    <meta charset="UTF-8">
    <title>主轴对齐方式</title>
    <style>
      .box{width: 80%; margin: 0 auto; border:1px solid green; display: flex;
      justify-content:space-around;}
      .box div{width: 100px; height: 100px; background: deeppink; margin:  0 10px;}
  
    </style>
  </head>
  <body>
    <div class="box">
      <div>1111</div>
      <div>222</div>
      <div>333</div>
      <div>444</div>
      <div>555</div>
    </div>
  
  </body>
  ```

- align-items   属性定义了项目在交叉轴上的对齐方式

  - flex-start：交叉轴的起点对齐
  - flex-end：交叉轴的终点对齐
  - center：交叉轴的中点对齐
  - baseline：项目的第一行文字的基线对齐
  - stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器

  ```html
  <head>
    <meta charset="UTF-8">
    <title>交叉轴对齐方式</title>
    <style>
      /*
      align-items: 交叉轴的对齐方式
      flex-start 顶端对齐
      flex-end   底部对齐
      center     居中对齐
      baseline   按照文字的底部对齐
      stretch    如果 item 设置的高度是auto，会撑开所有的纵向空间
      */
      .box{width: 80%; height: 600px; border:1px solid blue; margin: 0 auto; display: flex;
      align-items:center; justify-content: center; flex-wrap: wrap;
      }
      .box div{width: 100px; height: 100px; background: green;}
      .box div:nth-of-type(3){font-size: 30px;}
      .box div:nth-of-type(5){font-size: 60px;}
    </style>
  </head>
  <body>
  <div class="box">
    <div>1111</div>
    <div>222</div>
    <div>333</div>
    <div>444</div>
    <div>555</div>
    <div>1111</div>
    <div>222</div>
    <div>333</div>
    <div>4555544</div>
    <div>555</div>
    <div>1111</div>
    <div>2222222</div>
    <div>333</div>
    <div>444</div>
    <div>555</div>
  </div>
  
  </body>
  ```

- align-content  设置堆叠伸缩的对齐方式

  - flex-start：与交叉轴的起点对齐
  - flex-end ：与交叉轴的终点
  - center：与交叉轴的中点对齐
  - space-between：与交叉轴两端对齐，轴线之间的间隔平均分配
  - space-around：每根轴线两侧的间隔都相等
  - stretch（默认值）：轴线占满整个交叉轴

  ```html
  <head>
    <meta charset="UTF-8">
    <title>堆叠伸缩对齐方式</title>
    <style>
      /*
      align-content:堆叠伸缩对齐方式  （交叉轴）
       flex-start:从起点开始
       flex-end  :从终点开始
       center    :居中
       space-between:两端对齐
       space-around:剩余空间平均分配
       stretch   :当item高度为auto时，会占满整个交叉轴方向
      */
      .box{width: 80%; height: 600px; border:2px solid yellow; display: flex; flex-wrap: wrap;
      align-content:stretch;}
      .box div{width: 100px; height:auto; background: pink; margin: 10px;}
    </style>
  </head>
  <body>
  <div class="box">
    <div>1111</div>
    <div>222</div>
    <div>333333</div>
    <div>444</div>
    <div>555</div>
    <div>1111</div>
    <div>222</div>
    <div>333</div>
    <div>4555544</div>
    <div>555</div>
    <div>1111</div>
    <div>2222222</div>
    <div>333</div>
    <div>444</div>
    <div>555</div>
  </div>
  </body>
  ```


## 项目（简单说就是元素）的属性

- order   定义项目的排列顺序。
  - 数值越小，排列越靠前，默认为0 
- flex-grow  定义项目的放大比列去分配剩余空间
  - 默认为0，既如果存在剩余空间，也不放大。
  - 如果容器没有剩余空间，则无效
- flex-shrink   定义了项目的缩小比列
  - 默认为1，既如果容器空间不足，项目将缩小。
  - 0代表空间不足时不缩小
- flex-basis        设置弹性盒伸缩基准值
  - 定义了在分配多余空间之前，项目占据的主轴空间（main size），放大或压缩时按照此基准值运算
  - 默认值为auto，既小牧的本来大小
- flex		是flex-grow，flex-shrink和flex-basis的简写，默认值为0   1  auto。

- align-self     允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性
  - 默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch