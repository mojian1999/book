# Html

## 文档声明

文档模式，主要影响css的展示，在有些情况下也会影响js的解析执行

- 混杂模式
- 标准模式
- 准标准模式

## charset 字符集

告诉浏览器按照那种编码字符集来显示

```html
<head>
    <!-- 
        charset : 设置字符集,告诉浏览器按照哪种编码字符集来显示
        
        meta 是自结束标签
     -->
    <meta charset="UTF-8">
    <!-- 设置网页描述 -->
    <meta name="description" content="全国领先的某某">
    <!-- 设置关键字 -->
    <meta name="keywords" content="web前端,java培训">
    <!-- 请求重定向 -->
    <!-- <meta http-equiv="refresh"	content="5;url=http://www.baidu.com"/> -->
    <title>Document</title>
</head>
<body>
    <h1>我是一个标题</h1>
</body>
```

## 常用标签

h1~h6：标题      块级标签 

p：段落    块级标签

br：换行/自结束

hr：生成一条水平线

## 实体

&nbsp：空格

&lt：<

&gt:>

&copy:版权

## 图片标签

img：图片

src：图片来源

alt：图片未显示，则用alt的文字显示，主要给搜索引擎用

#### 图片分类  

jpg，jpeg：  普通图片  色彩丰富，细节多

png：可以透明

gif：动态图片

svg：base64图片，优点是小，一般10内图片

#### 链接  

href :跳转的路径

- target

  - _blank 在一个新的标签页打开

  -  _self 默认值, 在当前窗口中刷新
  -  _parent

#### 描点

- 设置锚点, 通过id指定

- href 设置锚点id的值 id="title"

- 可以在当前页面锚点 href="#title"

- 也可以跳转到其它页面的锚点 href="./08_链接标签.html#title"



# CSS

css cascading style sheets  层叠样式表

- 美化页面
- 布局
- 动画

#### css选择器

- 元素选择器/标签选择器     标签名 {}

- 类选择器         .类名 {}
  -  可以重复使用
  -  一个class属性可以使用多个值, 用 空格 隔开

- id选择器    #id {}
  -  id 值在一个网页中是唯一的

#### 后代选择器

- 祖先  后代 {}
- 父子选择器 
  - 父 > 子 {}
- 兄弟选择器
  - E~F
  - F元素必须要和E元素同级别

- 相邻选择器
  - E + F{}
  - 只能找到E元素，后面的第一个F

## 伪类

：before                  : 在被选元素之前添加内容

- 用content来设置被插入的内容

：link  			：未访问之前

：visited			：访问之后  

：hover			：鼠标悬停

：active             	：鼠标在点击与释放之前发生的事件

：focus			：获得焦点的样式

(visited不能写在hover和active之后，否则会导致hover和active失效)

#### 伪对象

：：first-letter	：设置对象内第一个字符的样式

：：first-line		：设置对象内第一行的样式

：：selection	：设置对象被选择时的样式

：：placeholder	：设置文本框的样式

#### 属性选择器

- 元素[属性名] 匹配元素中有属性名的

-  元素[属性名="属性值"] 匹配元素中属性名=属性值的元素

- 元素[属性名^="属性值"] 匹配元素中指定的属性的值以 XX 开头

-  元素[属性名$="属性值"] 匹配元素中指定的属性的值以 XX 结尾

-  元素[属性名*="属性值"] 匹配元素中指定的属性的值中包含 XX

-  元素[属性名~="属性值"] 匹配元素中指定的属性的值中含有 XX

#### 子元素选择器

- ：first-of-type = ：nth-of-type（1）         第一个子元素

-  :last-of-type    =   :nth-last-of-type(1)         最后一个子元素

#### 否定伪类

：not     （需要排除的元素）   ==  除了选中这个 其他全选

#### 选择器的权重

1. 内联样式				1000
2. id选择器                          100
3. 类、属性、伪类                10
4. 元素选择器                          1
5. 通配符                                  0

## 文本标签

strong			：语义标签，用于强调

b				：加粗

em				：倾斜  语义标签，着重强调

i				：文本倾斜

small			：小字体

cite				：用于强调标签名的书名   例如《七龙珠》

## 列表标签	

ul > li			有序列表

ol > li			无序列表

dl > dt(头部) > dd（身体）			定义列表

#### 单位	

px 					像素

百分比				相对于父级元素

em					相对于父级元素

rem					相对于根元素

#### 颜色	color

rgba		（red，green，blue，透明度）

## 文字样式 	font

- font-size					文字大小

- font-style：italic			斜体

- line-height				居中，值为元素的高

- text-decoration			参数

- text-decoration: underline;		设置文本下划线

-  text-decoration: overline;			设置文本删除线

-  text-decoration: line-through;		设置文本中划线

- letter-spacing					设置字符间距

- text-align						文字居中

## 边框	border

- none 			无边框
- solid                        实线
- dashed                   虚线
- dotted                    点线

padding                  内边距

margin			 外边距

## display	对于元素

- inline  			行内元素
  - 与其他行内元素并排
  - 不能设置宽高，默认的宽度就是文字的宽度                          
- block                             块级元素
  - 霸占一行，不能与其他任何元素并列。
  - 能接受宽高，如果不设置宽度，那么宽度将默认变为父级的100%
- inline-block                  行内块级元素
  - 该元素就成为一个行内块级元素，既可以在一行内放置多个这样的元素，又可以为它设置宽高内外边距等属性。
- none                              隐藏
- hidden                          隐藏
- visible                            显示

## overflow   对于内容

- visible                      默认值
- hidden                    隐藏超出的内容
- scroll                       添加滚动条
- auto                        超出后在添加滚动条

#### 浮动

float                         元素一旦浮动，立即脱离文本流（脱离半层）

#### 清除浮动

```html
.warp::after {
            content: "";
            clear: both;
            display: block;
}
```

## BFC

- 触发条件或者说哪些元素会生成BFC：满足下列条件之一就可触发BFC

​        　　【1】根元素，即HTML元素

​        　　【2】float的值不为none

​        　　【3】overflow的值不为visible

​        　　【4】display的值为inline-block、table-cell、table-caption

​        　　【5】position的值为absolute或fixed

-  BFC布局规则：

​                1.内部的Box会在垂直方向，一个接一个地放置。

​                2.Box垂直方向的距离由margin决定。属于同一个BFC的两个相邻Box的margin会发生重叠

​                3.每个元素的margin box的左边， 与包含块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此。

​                4.BFC的区域不会与float box重叠。

​                5.BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反之也如此。

​                6.计算BFC的高度时，浮动元素也参与计算

- BFC有哪些作用：

​                1. 自适应两栏布局

​                2. 可以阻止元素被浮动元素覆盖

​                3. 可以包含浮动元素——清除内部浮动(解决高度塌陷)

​                4. 分属于不同的BFC时可以阻止margin重叠

#### 定位

- position：relative                               相对定位
- position：absolute                             绝对定位
- position：fixed                                    固定定位（在视口一直存在）

#### 层级

z-index                      可以改变层级（一定要开启定位）

### 背景	background

- 平铺方式

  -  repeat 左右上下平铺
  - no-repeat 只显示一次
  - repeat-x 水平方向平铺

  -  repeat-y 垂直方向平铺

## 表格

colspan                             合并单元格

rowspan                            合并行

colspan                              合并列

- form 表单 用来收集用户信息

- action 表单提交的url地址（服务器地址）
  - method 表单提交方式
-  get 默认提交方式
  - 表单的内容会显示在 浏览器 地址栏中

- post 表单提交建议使用 post 方式
  -  表单的内容不显示在浏览器地址栏上，包含在了 请求头 中

```html
input
                placeholder 默认显示，当获得焦点，输入内容自动隐藏，内容删除后，自动显示
type 输入类型
    - text 单行文本
    - password 密码框
    - radio 单选， 只能选择一项
        - name 多个单项项必须通过 相同的 name 来设置为一组
    - checkbox 多选， 可以选择多项
        - name 多个项必须通过 相同的 name 来设置为一组
    - submit 提交表单按钮， 可以提交表单的内容到 action 指定的 url
    - reset 重置表单，（不是清空）, 将表单还原到初始（默认）状态
    - button 普通按钮，不能提交表单
    - hidden 隐藏表单域
    - file 文件域
    - imgage 图片按钮
select 下拉列表 默认只能选择一项
    - option 表示下拉列表中的每一项
    - optgroup 为 option 进行分组，使用 label 属性 来为分组命名
    - multiple 可以多选，按 ctrl 进行多选
textarea 多行文本
    - cols 设置每行可以写多少个字符
    - rows 设置多少行

disabled: 禁用
enable: 可用 默认值
```



