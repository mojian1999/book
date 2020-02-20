# Bootstrap

- 简洁、直观、强悍的前端开发框架，让web开发更迅速简单
- 来自Twitter，是目前很受欢迎的前端框架之一
- 基于html，css，javascript让代码书写更简单
- 移动优先，响应式布局开发

## 简单使用

### 添加 HTML5 doctype

Bootstrap 要求使用 HTML5 文件类型，所以需要添加 HTML5 doctype 声明。

HTML5 doctype 在文档头部声明，并设置对应编码:

```javascript
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8"> 
  </head>
</html>
```

### 移动设备优先

为了让 Bootstrap 开发的网站对移动设备友好，确保适当的绘制和触屏缩放，需要在网页的 head 之中添加 viewport meta 标签，如下所示：

```javascript
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
```

`width=device-width` 表示宽度是设备屏幕的宽度。

`initial-scale=1` 表示初始的缩放比例。

`shrink-to-fit=no` 自动适应手机屏幕的宽度

----------------------

## 容器类

Bootstrap 4 需要一个容器元素来包裹网站的内容。

我们可以使用以下两个容器类：

- .container 类用于固定宽度并支持响应式布局的容器。

- .container-fluid 类用于 100% 宽度，占据全部视口（viewport）的容器。

  -------------

  ![img](https://www.runoob.com/wp-content/uploads/2017/10/176B67B9-013C-429C-8FD0-BC2409011545.jpg)

## 栅格系统

### 网格类

Bootstrap 4 网格系统有以下 5 个类:

- .col- 针对所有设备
- .col-sm- 平板 - 屏幕宽度等于或大于 576px
- .col-md- 桌面显示器 - 屏幕宽度等于或大于 768px)
- .col-lg- 大桌面显示器 - 屏幕宽度等于或大于 992px)
- .col-xl- 超大桌面显示器 - 屏幕宽度等于或大于 1200px)

| 超小设备 <576px | 平板 ≥576px                    | 桌面显示器 ≥768px | 大桌面显示器 ≥992px | 超大桌面显示器 ≥1200px |            |
| --------------- | ------------------------------ | ----------------- | ------------------- | ---------------------- | ---------- |
| 容器最大宽度    | None (auto)                    | 540px             | 720px               | 960px                  | 1140px     |
| 类前缀          | `.col-`                        | `.col-sm-`        | `.col-md-`          | `.col-lg-`             | `.col-xl-` |
| 列数量和        | 12                             |                   |                     |                        |            |
| 间隙宽度        | 30px （一个列的每边分别 15px） |                   |                     |                        |            |
| 可嵌套          | Yes                            |                   |                     |                        |            |
| 列排序          | Yes                            |                   |                     |                        |            |

### 网页的基本结构

第一个例子：创建一行(**<div class="row">**)。然后， 添加是需要的列( **.col-\*-*** 类中设置)。 第一个星号 (*) 表示响应的设备: sm, md, lg 或 xl, 第二个星号 (*) 表示一个数字, 同一行的数字相加为 12。

第二个例子: 不在每个 **col** 上添加数字，让 bootstrap 自动处理布局，同一行的每个列宽度相等： 两个 **"col"** ，每个就为 50% 的宽度。三个 **"col"**每个就为 33.33% 的宽度，四个 **"col"**每个就为 25% 的宽度，以此类推。同样，你可以使用 **.col-sm|md|lg|xl** 来设置列的响应规则。

接下来我们可以看看实例。

```javascript
<!-- 第一个例子：控制列的宽度及在不同的设备上如何显示 -->
<div class="row">
  <div class="col-*-*"></div>
</div>
<div class="row">
  <div class="col-*-*"></div>
  <div class="col-*-*"></div>
  <div class="col-*-*"></div>
</div>
 
<!-- 第二个例子：或让 Bootstrap 者自动处理布局 -->
<div class="row">
  <div class="col"></div>
  <div class="col"></div>
  <div class="col"></div>
</div>
```

-------------

### 等宽

```javascript
<div class="row">
  <div class="col">.col</div>
  <div class="col">.col</div>
  <div class="col">.col</div>
</div>
```

### 等宽响应式列

以下实例演示了如何在平板及更大屏幕上创建等宽度的响应式列。 **在移动设备上，即屏幕宽度小于 576px 时，四个列将会上下堆叠排版**:

```javascript
<div class="col-sm-3">.col-sm-3</div>
<div class="col-sm-3">.col-sm-3</div>
<div class="col-sm-3">.col-sm-3</div>
<div class="col-sm-3">.col-sm-3</div>
```

### 不等宽响应式列

以下实例演示了在平板及更大屏幕上创建不等宽度的响应式列。 **在移动设备上，即屏幕宽度小于 576px 时，两个列将会上下堆叠排版**:

```javascript
<div class="row">
  <div class="col-sm-4">.col-sm-4</div>
  <div class="col-sm-8">.col-sm-8</div>
</div>
```

### 平板和桌面端

以下实例演示了在桌面设备的显示器上两个列的宽度各占 50%，如果在平板端则左边的宽度为 25%，右边的宽度为 75%, 在移动手机等小型设备上会堆叠显示。

```javascript
<div class="container-fluid">
  <div class="row">
    <div class="col-sm-3 col-md-6">
      <p>RUNOOB</p>
    </div>
    <div class="col-sm-9 col-md-6">
      <p>content</p>
    </div>
  </div>
</div>
```

### 平板、桌面、大桌面显示器、超大桌面显示器

以下实例在平板、桌面、大桌面显示器、超大桌面显示器的宽度比例为分别为：25%/75%、50%/50%、33.33%/66.67%、16.67/83.33%, 在移动手机等小型设备上会堆叠显示。

```javascript
<div class="container-fluid">
  <div class="row">
    <div class="col-sm-3 col-md-6 col-lg-4 col-xl-2">
      <p>RUNOOB</p>
    </div>
    <div class="col-sm-9 col-md-6 col-lg-8 col-xl-10">
      <p>菜鸟教程</p>
    </div>
  </div>
</div>
```

-------------

### 偏移列

偏移列通过 offset-*-* 类来设置。第一个星号( * )可以是 **sm、md、lg、xl**，表示屏幕设备类型，第二个星号( * )可以是 **1** 到 **11** 的数字。

为了在大屏幕显示器上使用偏移，请使用 **.offset-md-\*** 类。这些类会把一个列的左外边距（margin）增加 ***** 列，其中 ***** 范围是从 **1** 到 **11**。

例如：.offset-md-4 是把.col-md-4 往右移了四列格。

```javascript
<div class="row">
  <div class="col-md-4">.col-md-4</div>
  <div class="col-md-4 offset-md-4">.col-md-4 .offset-md-4</div>
</div>
<div class="row">
  <div class="col-md-3 offset-md-3">.col-md-3 .offset-md-3</div>
  <div class="col-md-3 offset-md-3">.col-md-3 .offset-md-3</div>
</div>
<div class="row">
  <div class="col-md-6 offset-md-3">.col-md-6 .offset-md-3</div>
</div>
```

## 文字排版

Bootstrap 4默认的 font-size为16px， line-height为1.5。

默认的font-family为“ Helvetica Neue”，Helvetica，Arial，无衬线。

此外，所有的<p>元素 margin-top：0，margin-bottom：1rem（16px）。

### `<h1>-<h6>`

```javascript
< div class = “ container ” > 
    < h1 > h1引导标题（2.5rem = 40px）</ h1 >
	< h2 > h2引导标题（2rem = 32px）</ h2 > 
	< h3 > h3引导标题（1.75rem = 28px ）</ h3 >
	< h4 > h4 Bootstrap标题（1.5rem = 24px）</ h4 > 
	< h5 > h5 Bootstrap标题（1.25rem = 20px）</ h5 > 
	<h6> Bootstrap标题（1rem = 16px）</ h6 > 
</ div >
```

#### 显示标题类

Bootstrap还提供了四个Display类来控制标题的样式：.display-1，.display-2，.display-3，.display-4。

```javascript
< div class = “ container ” >
    < h1 > 显示标题</ h1 > 
< p > 显示标题可以输出更大更粗的字体样式。</ p > 
< h1 class = “ display-1 ” > 显示1 </ h1 > 
< h1 class = “ display-2 ” > 显示2 </ h1 >
< h1 class = " display-3 "> 显示3 </ h1 >
< h1 class = “ display-4 ” > 显示4 </ h1 > 
</ div >
```

### 文本类

| 类名                |                             描述                             |
| ------------------- | :----------------------------------------------------------: |
| .font-weight-bold   |                           加粗文本                           |
| .font-weight-normal |                           普通文本                           |
| .font-weight-light  |                          更细的文本                          |
| .font-italic        |                           斜体文本                           |
| .lead               |                         让段落更突出                         |
| .small              |                指定更小文本 (为父元素的 85% )                |
| .text-left          |                            左对齐                            |
| .text-center        |                             居中                             |
| .text-right         |                            右对齐                            |
| .text-justify       |         设定文本对齐,段落中超出屏幕部分文字自动换行          |
| .text-nowrap        |                   段落中超出屏幕部分不换行                   |
| .text-lowercase     |                         设定文本小写                         |
| .text-uppercase     |                         设定文本大写                         |
| .text-capitalize    |                      设定单词首字母大写                      |
| .initialism         | 显示在 <abbr> 元素中的文本以小号字体展示，且可以将小写字母转换为大写字母 |
| .list-unstyled      | 移除默认的列表样式，列表项中左对齐 ( <ul> 和 <ol> 中)。 这个类仅适用于直接子列表项 (如果需要移除嵌套的列表项，你需要在嵌套的列表中使用该样式) |
| .list-inline        |                    将所有列表项放置同一行                    |
| .pre-scrollable     | 使 <pre> 元素可滚动，代码块区域最大高度为340px,一旦超出这个高度,就会在Y轴出现滚动条 |

## 颜色

```javascript
<div class="container">
  <h2>代表指定意义的文本颜色</h2>
  <p class="text-muted">柔和的文本。</p>
  <p class="text-primary">重要的文本。</p>
  <p class="text-success">执行成功的文本。</p>
  <p class="text-info">代表一些提示信息的文本。</p>
  <p class="text-warning">警告文本。</p>
  <p class="text-danger">危险操作文本。</p>
  <p class="text-secondary">副标题。</p>
  <p class="text-dark">深灰色文字。</p>
  <p class="text-light">浅灰色文本（白色背景上看不清楚）。</p>
  <p class="text-white">白色文本（白色背景上看不清楚）。</p>
</div>
```

### 背景颜色

```javascript
<div class="container">
  <h2>背景颜色</h2>
  <p class="bg-primary text-white">重要的背景颜色。</p>
  <p class="bg-success text-white">执行成功背景颜色。</p>
  <p class="bg-info text-white">信息提示背景颜色。</p>
  <p class="bg-warning text-white">警告背景颜色</p>
  <p class="bg-danger text-white">危险背景颜色。</p>
  <p class="bg-secondary text-white">副标题背景颜色。</p>
  <p class="bg-dark text-white">深灰背景颜色。</p>
  <p class="bg-light text-dark">浅灰背景颜色。</p>
</div>
```

## 表格

通过 .table 类来设置基础表格的样式

```javascript
<table class="table">
    <thead>
      <tr>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Email</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>John</td>
        <td>Doe</td>
        <td>john@example.com</td>
      </tr>
      <tr>
        <td>Mary</td>
        <td>Moe</td>
        <td>mary@example.com</td>
      </tr>
      <tr>
        <td>July</td>
        <td>Dooley</td>
        <td>july@example.com</td>
      </tr>
    </tbody>
</table>
```

### 条纹表格

通过添加 .table-striped 类，您将在 **<tbody>** 内的行上看到条纹

```javascript
<table class="table table-striped">
    <thead>
      <tr>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Email</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>John</td>
        <td>Doe</td>
        <td>john@example.com</td>
      </tr>
      <tr>
        <td>Mary</td>
        <td>Moe</td>
        <td>mary@example.com</td>
      </tr>
      <tr>
        <td>July</td>
        <td>Dooley</td>
        <td>july@example.com</td>
      </tr>
    </tbody>
</table>
```

### 带边框表格

.table-bordered 类可以为表格添加边框

```javascript
<table class="table table-bordered">
    <thead>
      <tr>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Email</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>John</td>
        <td>Doe</td>
        <td>john@example.com</td>
      </tr>
      <tr>
        <td>Mary</td>
        <td>Moe</td>
        <td>mary@example.com</td>
      </tr>
      <tr>
        <td>July</td>
        <td>Dooley</td>
        <td>july@example.com</td>
      </tr>
    </tbody>
</table>
```

### 鼠标悬停状态表格

.table-hover 类可以为表格的每一行添加鼠标悬停效果（灰色背景）：

```javascript
<table class="table table-hover">
    <thead>
      <tr>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Email</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>John</td>
        <td>Doe</td>
        <td>john@example.com</td>
      </tr>
      <tr>
        <td>Mary</td>
        <td>Moe</td>
        <td>mary@example.com</td>
      </tr>
      <tr>
        <td>July</td>
        <td>Dooley</td>
        <td>july@example.com</td>
      </tr>
    </tbody>
</table>
```

### 黑色背景表格

.table-dark 类可以为表格添加黑色背景：

```javascript
<table class="table table-dark">
    <thead>
      <tr>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Email</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>John</td>
        <td>Doe</td>
        <td>john@example.com</td>
      </tr>
      <tr>
        <td>Mary</td>
        <td>Moe</td>
        <td>mary@example.com</td>
      </tr>
      <tr>
        <td>July</td>
        <td>Dooley</td>
        <td>july@example.com</td>
      </tr>
    </tbody>
</table>
```

### 混合使用表格

联合使用 .table-dark 和 .table-hover 类可以设置黑色背景表格的鼠标悬停效果：

```javascript
<table class="table table-dark table-hover">
    <thead>
      <tr>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Email</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>John</td>
        <td>Doe</td>
        <td>john@example.com</td>
      </tr>
      <tr>
        <td>Mary</td>
        <td>Moe</td>
        <td>mary@example.com</td>
      </tr>
      <tr>
        <td>July</td>
        <td>Dooley</td>
        <td>july@example.com</td>
      </tr>
    </tbody>
</table>
```

### 响应式表格

.table-responsive 类用于创建响应式表格：在屏幕宽度小于 992px 时会创建水平滚动条，如果可视区域宽度大于 992px 则显示不同效果（没有滚动条）:

```javascript
<div class="table-responsive">
<table class="table">
    <thead>
      <tr>
        <th>#</th>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Age</th>
        <th>City</th>
        <th>Country</th>
        <th>Sex</th>
        <th>Example</th>
        <th>Example</th>
        <th>Example</th>
        <th>Example</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>1</td>
        <td>Anna</td>
        <td>Pitt</td>
        <td>35</td>
        <td>New York</td>
        <td>USA</td>
        <td>Female</td>
        <td>Yes</td>
        <td>Yes</td>
        <td>Yes</td>
        <td>Yes</td>
      </tr>
    </tbody>
</table>
</div>
```

### 表格滚动条

| 类名                 | 屏幕宽度 |
| -------------------- | -------- |
| .table-responsive-sm | < 576px  |
| .table-responsive-md | < 768px  |
| .table-responsive-lg | < 992px  |
| .table-responsive-xl | < 1200px |

```javascript
<div class="table-responsive-sm">
  <table class="table">
    ...
  </table>
</div>
```

##  图像形状

### 圆角图片

.rounded 类可以让图片显示圆角效果：

```javascript
<img src="cinqueterre.jpg" class="rounded" alt="Cinque Terre">
```

### 椭圆图片

.rounded-circle 类可以设置椭圆形图片:

```javascript
<img src="cinqueterre.jpg" class="rounded-circle" alt="Cinque Terre">
```

### 缩略图

.img-thumbnail 类用于设置图片缩略图(图片有边框):

```javascript
<img src="cinqueterre.jpg" class="img-thumbnail" alt="Cinque Terre">
```

### 图片对齐方式

使用 .float-right 类来设置图片右对齐，使用 .float-left 类设置图片左对齐:

```javascript
<img src="paris.jpg" class="float-left"> 
<img src="cinqueterre.jpg" class="float-right">
```

### 响应式图片

图像有各种各样的尺寸，我们需要根据屏幕的大小自动适应。

我们可以通过在 <img> 标签中添加 .img-fluid 类来设置响应式图片。

.img-fluid 类设置了 max-width: 100%; 、 height: auto; 

```javascript
<img class="img-fluid" src="img_chania.jpg" alt="Chania">
```

## 超大屏幕

Jumbotron（超大屏幕）会创建一个大的灰色背景框，里面可以设置一些特殊的内容和信息。

**提示:** Jumbotron 里头可以放一些 HTML标签，也可以是 Bootstrap 的元素。

-----------

我们可以通过在 `<div>` 元素 中添加 .jumbotron 类来创建 jumbotron:

```javascript
<div class="jumbotron">
  <h1>zzzzzz</h1> 
  <p>aaaaaaaaaaaaaaaa</p> 
</div>
```

### 全屏幕的 Jumbotron

如果你想创建一个没有圆角的全屏幕，可以在 .jumbotron-fluid 类里头的 div添加 .container 或 .container-fluid 类来实现:

```javascript
<div class="jumbotron jumbotron-fluid">
  <div class="container">
      <h1>aaaaaaaaaaaaa</h1> 
      <p>zzzzzzzzzzzzzzzzzzzzzzzzzz</p>
  </div>
</div>
```

## 信息提示框

提示框可以使用 .alert 类,(可以添加颜色) 后面加上类来实现:

```javascript
<div class="alert alert-success">
  <strong>成功!</strong> 指定操作成功提示信息。
</div>
```

### 信息提示框加链接

提示框中在链接的标签上添加 alert-link 类来设置匹配提示框颜色的链接：

```javascript
<div class="alert alert-success">
  <strong>成功!</strong> 你应该认真阅读 <a href="#" class="alert-link">这条信息</a>。
</div>
```

### 关闭信息提示框

我们可以在提示框中的 div 中添加 .alert-dismissible 类，然后在关闭按钮的链接上添加 class="close" 和 data-dismiss="alert" 类来设置提示框的关闭操作。

```javascript
<div class="alert alert-success alert-dismissible">
  <button type="button" class="close" data-dismiss="alert">&times;</button>
  <strong>成功!</strong> 指定操作成功提示信息。
</div>

//提示: &times; (×) 是 HTML 实体字符，来表示关闭操作，而不是字母 "x"。
```

### 信息提示动画

.fade 和 .show 类用于设置提示框在关闭时的淡出和淡入效果：

```javascript
<div class="alert alert-danger alert-dismissible fade show">
```

## 按钮

```javascript
<button type="button" class="btn">基本按钮</button>
<button type="button" class="btn btn-primary">主要按钮</button>
<button type="button" class="btn btn-secondary">次要按钮</button>
<button type="button" class="btn btn-success">成功</button>
<button type="button" class="btn btn-info">信息</button>
<button type="button" class="btn btn-warning">警告</button>
<button type="button" class="btn btn-danger">危险</button>
<button type="button" class="btn btn-dark">黑色</button>
<button type="button" class="btn btn-light">浅色</button>
<button type="button" class="btn btn-link">链接</button>
```

按钮类可用于` <a>`, `<button>`, 或 `<input>` 元素上:

```javascript
<a href="#" class="btn btn-info" role="button">链接按钮</a>
<button type="button" class="btn btn-info">按钮</button>
<input type="button" class="btn btn-info" value="输入框按钮">
<input type="submit" class="btn btn-info" value="提交按钮">
```

### 按钮设置边框

```javascript
<button type="button" class="btn btn-outline-primary">主要按钮</button>
<button type="button" class="btn btn-outline-secondary">次要按钮</button>
<button type="button" class="btn btn-outline-success">成功</button>
<button type="button" class="btn btn-outline-info">信息</button>
<button type="button" class="btn btn-outline-warning">警告</button>
<button type="button" class="btn btn-outline-danger">危险</button>
<button type="button" class="btn btn-outline-dark">黑色</button>
<button type="button" class="btn btn-outline-light text-dark">浅色</button>
```

### 不同大小的按钮

```javascript
<button type="button" class="btn btn-primary btn-lg">大号按钮</button>
<button type="button" class="btn btn-primary">默认按钮</button>
<button type="button" class="btn btn-primary btn-sm">小号按钮</button>
```

### 块级按钮

通过添加 .btn-block 类可以设置块级按钮：

```javascript
<button type="button" class="btn btn-primary btn-block">按钮 1</button>
```

### 激活和禁用按钮

按钮可设置为激活或者禁止点击的状态。

.active 类可以设置按钮是可用的， disabled 属性可以设置按钮是不可点击的。 注意 <a> 元素不支持 disabled 属性，你可以通过添加 .disabled 类来禁止链接的点击。

```javascript
<button type="button" class="btn btn-primary active">点击后的按钮</button>
<button type="button" class="btn btn-primary" disabled>禁止点击的按钮</button>
<a href="#" class="btn btn-primary disabled">禁止点击的链接</a>
```

## 按钮组

可以在 <div> 元素上添加 .btn-group 类来创建按钮组。

```javascript
<div class="btn-group">
  <button type="button" class="btn btn-primary">Apple</button>
  <button type="button" class="btn btn-primary">Samsung</button>
  <button type="button" class="btn btn-primary">Sony</button>
</div>
```

### 按钮组大小

**提示:** 我们可以使用 .btn-group-lg|sm 类来设置按钮组的大小。

```javascript
<div class="btn-group btn-group-lg">
  <button type="button" class="btn btn-primary">Apple</button>
  <button type="button" class="btn btn-primary">Samsung</button>
  <button type="button" class="btn btn-primary">Sony</button>
</div>
```

### 垂直按钮组

可以使用 .btn-group-vertical 类来创建垂直的按钮组：

```javascript
<div class="btn-group-vertical">
  <button type="button" class="btn btn-primary">Apple</button>
  <button type="button" class="btn btn-primary">Samsung</button>
  <button type="button" class="btn btn-primary">Sony</button>
</div>
```

### 内嵌按钮组及以下拉菜单

```javascript
<div class="btn-group">
  <button type="button" class="btn btn-primary">Apple</button>
  <button type="button" class="btn btn-primary">Samsung</button>
  <div class="btn-group">
    <button type="button" class="btn btn-primary dropdown-toggle" data-toggle="dropdown">
       Sony
    </button>
    <div class="dropdown-menu">
      <a class="dropdown-item" href="#">Tablet</a>
      <a class="dropdown-item" href="#">Smartphone</a>
    </div>
  </div>
</div>
```

### 拆分按钮下拉菜单

```javascript
<div class="btn-group">
  <button type="button" class="btn btn-primary">Sony</button>
  <button type="button" class="btn btn-primary dropdown-toggle dropdown-toggle-split" data-toggle="dropdown">
    <span class="caret"></span>
  </button>
  <div class="dropdown-menu">
    <a class="dropdown-item" href="#">Tablet</a>
    <a class="dropdown-item" href="#">Smartphone</a>
  </div>
</div>
```

### 垂直按钮组和下拉菜单

```javascript
<div class="btn-group-vertical">
  <button type="button" class="btn btn-primary">Apple</button>
  <button type="button" class="btn btn-primary">Samsung</button>
  <div class="btn-group">
    <button type="button" class="btn btn-primary dropdown-toggle" data-toggle="dropdown">
       Sony
    </button>
    <div class="dropdown-menu">
      <a class="dropdown-item" href="#">Tablet</a>
      <a class="dropdown-item" href="#">Smartphone</a>
    </div>
  </div>
</div>
```

## 徽章

徽章（Badges）主要用于突出显示新的或未读的项。如需使用徽章，只需要将 .badge 类加上带有指定意义的颜色类 (如 .badge-secondary) 添加到 <span> 元素上即可。 徽章可以根据父元素的大小的变化而变化:

```javascript
<h1>测试标题 <span class="badge badge-secondary">New</span></h1>
<h2>测试标题 <span class="badge badge-secondary">New</span></h2>
<h3>测试标题 <span class="badge badge-secondary">New</span></h3>
<h4>测试标题 <span class="badge badge-secondary">New</span></h4>
<h5>测试标题 <span class="badge badge-secondary">New</span></h5>
<h6>测试标题 <span class="badge badge-secondary">New</span></h6>
```

### 各种颜色的徽章

```javascript
<span class="badge badge-primary">主要</span>
<span class="badge badge-secondary">次要</span>
<span class="badge badge-success">成功</span>
<span class="badge badge-danger">危险</span>
<span class="badge badge-warning">警告</span>
<span class="badge badge-info">信息</span>
<span class="badge badge-light">浅色</span>
<span class="badge badge-dark">深色</span>
```

### 药丸形状徽章

使用 .badge-pill 类来设置药丸形状徽章:

```javascript
<span class="badge badge-pill badge-default">默认</span>
<span class="badge badge-pill badge-primary">主要</span>
<span class="badge badge-pill badge-success">成功</span>
<span class="badge badge-pill badge-info">信息</span>
<span class="badge badge-pill badge-warning">警告</span>
<span class="badge badge-pill badge-danger">危险</span>
```

### 徽章插入到元素内

```javascript
<button type="button" class="btn btn-primary">
  Messages <span class="badge badge-light">4</span>
</button>
```

## 进度条

进度条可以显示用户任务的完成过程。

创建一个基本的进度条的步骤如下：

- 添加一个带有 **.progress** 类的 <div>。
- 接着，在上面的 <div> 内，添加一个带有 class **.progress-bar** 的空的 <div>。
- 添加一个带有百分比表示的宽度的 style 属性，例如 style="width:70%" 表示进度条在 **70%** 的位置

```javascript
<div class="progress">
  <div class="progress-bar" style="width:70%"></div>
</div>
```

### 进度条高度

进度条高度默认为 16px。我们可以使用 CSS 的 `height` 属性来修改他：

```javascript
<div class="progress" style="height:20px;">
  <div class="progress-bar" style="width:40%;"></div>
</div>
```

### 进度条标签

可以在进度条内添加文本，如进度的百分比：

```javascript
<div class="progress">
  <div class="progress-bar" style="width:70%">70%</div>
</div>
```

### 不同颜色的进度条

默认情况下进度条为蓝色，Bootstrap4 还提供了以下颜色的进度条：

```javascript
<div class="progress">
  <div class="progress-bar bg-success" style="width:40%"></div>
</div>
 
<div class="progress">
  <div class="progress-bar bg-info" style="width:50%"></div>
</div>
 
<div class="progress">
  <div class="progress-bar bg-warning" style="width:60%"></div>
</div>
 
<div class="progress">
  <div class="progress-bar bg-danger" style="width:70%"></div>
</div>

//颜色看我上面颜色
```

### 条纹的进度条

可以使用 `.progress-bar-striped` 类来设置条纹进度条：

```javascript
<div class="progress">
  <div class="progress-bar progress-bar-striped" style="width:40%"></div>
</div>
```

### 动画进度条

使用 `.progress-bar-animated` 类可以为进度条添加动画：

```javascript
<div class="progress-bar progress-bar-striped progress-bar-animated" style="width: 40%"></div>
```

### 混合色彩进度条

```javascript
<div class="progress">
  <div class="progress-bar bg-success" style="width:40%">
    Free Space
  </div>
  <div class="progress-bar bg-warning" style="width:10%">
    Warning
  </div>
  <div class="progress-bar bg-danger" style="width:20%">
    Danger
  </div>
</div>
```

## 分页

网页开发过程，如果碰到内容过多，一般都会做分页处理。

Bootstrap 4 可以很简单的实现分页效果。

要创建一个基本的分页可以在 <ul> 元素上添加 .pagination 类。然后在 <li> 元素上添加 .page-item 类

```javascript
<ul class="pagination">
  <li class="page-item"><a class="page-link" href="#">Previous</a></li>
  <li class="page-item"><a class="page-link" href="#">1</a></li>
  <li class="page-item"><a class="page-link" href="#">2</a></li>
  <li class="page-item"><a class="page-link" href="#">3</a></li>
  <li class="page-item"><a class="page-link" href="#">Next</a></li>
</ul>
```

### 当前页页码状态

```javascript
<ul class="pagination">
  <li class="page-item"><a class="page-link" href="#">Previous</a></li>
  <li class="page-item"><a class="page-link" href="#">1</a></li>
  <li class="page-item active"><a class="page-link" href="#">2</a></li>
  <li class="page-item"><a class="page-link" href="#">3</a></li>
  <li class="page-item"><a class="page-link" href="#">Next</a></li>
</ul>
```

### 不可点击的分页链接

.disabled 类可以设置分页链接不可点击:

```javascript
<ul class="pagination">
  <li class="page-item disabled"><a class="page-link" href="#">Previous</a></li>
  <li class="page-item"><a class="page-link" href="#">1</a></li>
  <li class="page-item"><a class="page-link" href="#">2</a></li>
  <li class="page-item"><a class="page-link" href="#">3</a></li>
  <li class="page-item"><a class="page-link" href="#">Next</a></li>
</ul>
```

### 分页显示大小

可以将分页条目设置为不同的大小。

.pagination-lg 类设置大字体的分页条目，.pagination-sm 类设置小字体的分页条目:

```javascript
<ul class="pagination pagination-lg">
  <li class="page-item"><a class="page-link" href="#">Previous</a></li>
  <li class="page-item"><a class="page-link" href="#">1</a></li>
  <li class="page-item"><a class="page-link" href="#">2</a></li>
  <li class="page-item"><a class="page-link" href="#">3</a></li>
  <li class="page-item"><a class="page-link" href="#">Next</a></li>
</ul>
 
<ul class="pagination pagination-sm">
  <li class="page-item"><a class="page-link" href="#">Previous</a></li>
  <li class="page-item"><a class="page-link" href="#">1</a></li>
  <li class="page-item"><a class="page-link" href="#">2</a></li>
  <li class="page-item"><a class="page-link" href="#">3</a></li>
  <li class="page-item"><a class="page-link" href="#">Next</a></li>
</ul>
```

### 面包屑导航

.breadcrumb 和 .breadcrumb-item 类用于设置面包屑导航：

```javascript
<ul class="breadcrumb">
  <li class="breadcrumb-item"><a href="#">Photos</a></li>
  <li class="breadcrumb-item"><a href="#">Summer 2017</a></li>
  <li class="breadcrumb-item"><a href="#">Italy</a></li>
  <li class="breadcrumb-item active">Rome</li>
</ul>
```

## 列表组

要创建列表组，可以在 <ul> 元素上添加 .list-group 类, 在 <li> 元素上添加 .list-group-item 类:

```javascript
<ul class="list-group">
  <li class="list-group-item">First item</li>
  <li class="list-group-item">Second item</li>
  <li class="list-group-item">Third item</li>
</ul>
```

### 激活状态的列表项

通过添加 .active 类来设置激活状态的列表项：

```javascript
<ul class="list-group">
  <li class="list-group-item active">Active item</li>
  <li class="list-group-item">Second item</li>
  <li class="list-group-item">Third item</li>
</ul>
```

### 链接列表项

要创建一个链接的列表项，可以将 <ul> 替换为 <div> ， <a> 替换 <li>。如果你想鼠标悬停显示灰色背景就添加.list-group-item-action 类:

```javascript
<div class="list-group">
  <a href="#" class="list-group-item list-group-item-action">First item</a>
  <a href="#" class="list-group-item list-group-item-action">Second item</a>
  <a href="#" class="list-group-item list-group-item-action">Third item</a>
</div>
```

### 列表项颜色

```javascript
<ul class="list-group">
  <li class="list-group-item list-group-item-success">成功列表项</li>
  <li class="list-group-item list-group-item-secondary">次要列表项</li>
  <li class="list-group-item list-group-item-info">信息列表项</li>
  <li class="list-group-item list-group-item-warning">警告列表项</li>
  <li class="list-group-item list-group-item-danger">危险列表项</li>
  <li class="list-group-item list-group-item-primary">主要列表项</li>
  <li class="list-group-item list-group-item-dark">深灰色列表项</li>
  <li class="list-group-item list-group-item-light">浅色列表项</li>
</ul>
```

### 链接的多种颜色的列表项

```javascript
<div class="list-group">
    <a href="#" class="list-group-item list-group-item-action">激活列表项</a>
    <a href="#" class="list-group-item list-group-item-success">成功列表项</a>
    <a href="#" class="list-group-item list-group-item-secondary">次要列表项</a>
    <a href="#" class="list-group-item list-group-item-info">信息列表项</a>
    <a href="#" class="list-group-item list-group-item-warning">警告列表项</a>
    <a href="#" class="list-group-item list-group-item-danger">危险列表项</a>
    <a href="#" class="list-group-item list-group-item-primary">主要列表项</a>
    <a href="#" class="list-group-item list-group-item-dark">深灰色列表项</a>
    <a href="#" class="list-group-item list-group-item-light">浅色列表项</a>
</div>
```

## 卡片

我们可以通过 Bootstrap4 的 .card 与 .card-body 类来创建一个简单的卡片

```javascript
<div class="card">
  <div class="card-body">简单的卡片</div>
</div>
```

### 头部和底部

.card-header类用于创建卡片的头部样式， .card-footer 类用于创建卡片的底部样式：

```javascript
<div class="card">
  <div class="card-header">头部</div>
  <div class="card-body">内容</div> 
  <div class="card-footer">底部</div>
</div>
```

### 多种颜色卡片

多种卡片的背景颜色类： .bg-primary, .bg-success, .bg-info, .bg-warning, .bg-danger, .bg-secondary, .bg-dark 和 .bg-light。

```javascript
<div class="container">
  <h2>多种颜色卡片</h2>
  <div class="card">
    <div class="card-body">Basic card</div>
  </div>
  <br>
  <div class="card bg-primary text-white">
    <div class="card-body">Primary card</div>
  </div>
  <br>
  <div class="card bg-success text-white">
    <div class="card-body">Success card</div>
  </div>
  <br>
  <div class="card bg-info text-white">
    <div class="card-body">Info card</div>
  </div>
  <br>
  <div class="card bg-warning text-white">
    <div class="card-body">Warning card</div>
  </div>
  <br>
  <div class="card bg-danger text-white">
    <div class="card-body">Danger card</div>
  </div>
  <br>
  <div class="card bg-secondary text-white">
    <div class="card-body">Secondary card</div>
  </div>
  <br>
  <div class="card bg-dark text-white">
    <div class="card-body">Dark card</div>
  </div>
  <br>
  <div class="card bg-light text-dark">
    <div class="card-body">Light card</div>
  </div>
</div>
```

### 标题、文本和链接

我们可以在头部元素上使用 .card-title 类来设置卡片的标题 。 .card-text 类用于设置卡片正文的内容。 .card-link 类用于给链接设置颜色。

```javascript
<div class="card">
  <div class="card-body">
    <h4 class="card-title">Card title</h4>
    <p class="card-text">Some example text. Some example text.</p>
    <a href="#" class="card-link">Card link</a>
    <a href="#" class="card-link">Another link</a>
  </div>
</div>
```

### 图片卡片

我们可以给 <img> 添加 .card-img-top（图片在文字上方） 或 .card-img-bottom（图片在文字下方 来设置图片卡片：

```javascript
<div class="card" style="width:400px">
  <img class="card-img-top" src="img_avatar1.png" alt="Card image">
  <div class="card-body">
    <h4 class="card-title">John Doe</h4>
    <p class="card-text">Some example text.</p>
    <a href="#" class="btn btn-primary">See Profile</a>
  </div>
</div>
```

### 背景图片卡片

如果图片要设置为背景，可以使用 .card-img-overlay 类:

```javascript
<div class="card" style="width:500px">
  <img class="card-img-top" src="img_avatar1.png" alt="Card image">
  <div class="card-img-overlay">
    <h4 class="card-title">John Doe</h4>
    <p class="card-text">Some example text.</p>
    <a href="#" class="btn btn-primary">See Profile</a>
  </div>
</div>
```

## 下拉菜单

下拉菜单依赖于 popper.min.js。

下拉菜单是可切换的，是以列表格式显示链接的上下文菜单。

```javascript
<div class="dropdown">
  <button type="button" class="btn btn-primary dropdown-toggle" data-toggle="dropdown">
    Dropdown button
  </button>
  <div class="dropdown-menu">
    <a class="dropdown-item" href="#">Link 1</a>
    <a class="dropdown-item" href="#">Link 2</a>
    <a class="dropdown-item" href="#">Link 3</a>
  </div>
</div>
```

--------

.dropdown 类用来指定一个下拉菜单。

我们可以使用一个按钮或链接来打开下拉菜单， 按钮或链接需要添加 .dropdown-toggle 和 data-toggle="dropdown" 属性。

<div> 元素上添加 .dropdown-menu 类来设置实际下拉菜单，然后在下拉菜单的选项中添加 .dropdown-item 类。

我们也可以在 <a> 标签中使用：

```javascript
<div class="dropdown">
  <a class="btn btn-secondary dropdown-toggle" href="#" role="button" id="dropdownMenuLink" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
    Dropdown link
  </a>
 
  <div class="dropdown-menu" aria-labelledby="dropdownMenuLink">
    <a class="dropdown-item" href="#">Action</a>
    <a class="dropdown-item" href="#">Another action</a>
    <a class="dropdown-item" href="#">Something else here</a>
  </div>
</div>
```

### 下拉菜单中的分割线

.dropdown-divider 类用于在下拉菜单中创建一个水平的分割线：

```javascript
<div class="dropdown-divider"></div>
```

### 下拉菜单的标题

.dropdown-header 类用于在下拉菜单中添加标题：

```javascript
<div class="dropdown-header">Dropdown header 1</div>
```

### 下拉菜单的可用禁用项

```javascript
<a class="dropdown-item active" href="#">Active</a>
<a class="dropdown-item disabled" href="#">Disabled</a>
```

### 下拉菜单的定位

如果我们想让下拉菜单右对齐，可以在元素上的 .dropdown-menu 类后添加 .dropdown-menu-right 类。

```javascript
<div class="dropdown-menu dropdown-menu-right">
```

### 下拉菜单弹出方向设置

下拉菜单弹出方向默认为向下，当然我们也可以设置不同的方向。

##### 指定向右弹出下拉菜单

如果你希望下拉菜单向右弹出，可以在 div 元素上添加 "dropright" 类:

```javascript
<!-- Default dropright button -->
<div class="btn-group dropright">
  <button type="button" class="btn btn-secondary dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
    Dropright
  </button>
  <div class="dropdown-menu">
    <!-- Dropdown menu links -->
  </div>
</div>
 
<!-- Split dropright button -->
<div class="btn-group dropright">
  <button type="button" class="btn btn-secondary">
    Split dropright
  </button>
  <button type="button" class="btn btn-secondary dropdown-toggle dropdown-toggle-split" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
    <span class="sr-only">Toggle Dropright</span>
  </button>
  <div class="dropdown-menu">
    <!-- Dropdown menu links -->
  </div>
</div>
```

##### 指定向上弹出上拉菜单

如果你希望上拉菜单向上弹出，可以在 div 元素上添加 "dropup" 类:

```javascript
<!-- Default dropup button -->
<div class="btn-group dropup">
  <button type="button" class="btn btn-secondary dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
    Dropup
  </button>
  <div class="dropdown-menu">
    <!-- Dropdown menu links -->
  </div>
</div>
 
<!-- Split dropup button -->
<div class="btn-group dropup">
  <button type="button" class="btn btn-secondary">
    Split dropup
  </button>
  <button type="button" class="btn btn-secondary dropdown-toggle dropdown-toggle-split" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
    <span class="sr-only">Toggle Dropdown</span>
  </button>
  <div class="dropdown-menu">
    <!-- Dropdown menu links -->
  </div>
</div>
```

##### 指定向左弹出下拉菜单

如果你希望下拉菜单向上弹出，可以在 div 元素上添加 "dropleft" 类:

```javascript
<!-- Default dropleft button -->
<div class="btn-group dropleft">
  <button type="button" class="btn btn-secondary dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
    Dropleft
  </button>
  <div class="dropdown-menu">
    <!-- Dropdown menu links -->
  </div>
</div>
 
<!-- Split dropleft button -->
<div class="btn-group">
  <div class="btn-group dropleft" role="group">
    <button type="button" class="btn btn-secondary dropdown-toggle dropdown-toggle-split" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
      <span class="sr-only">Toggle Dropleft</span>
    </button>
    <div class="dropdown-menu">
      <!-- Dropdown menu links -->
    </div>
  </div>
  <button type="button" class="btn btn-secondary">
    Split dropleft
  </button>
</div>
```

#####　按钮中设置下拉菜单

```javascript
<div class="btn-group">
  <button type="button" class="btn btn-primary">Sony</button>
  <button type="button" class="btn btn-primary dropdown-toggle dropdown-toggle-split" data-toggle="dropdown">
    <span class="caret"></span>
  </button>
  <div class="dropdown-menu">
    <a class="dropdown-item" href="#">Tablet</a>
    <a class="dropdown-item" href="#">Smartphone</a>
  </div>
</div>
```



## 折叠

collapse 类用于指定一个折叠元素 (实例中的 <div>); 点击按钮后会在隐藏与显示之间切换。

控制内容的隐藏与显示，需要在 <a> 或 <button> 元素上添加 data-toggle="collapse" 属性。 data-target="#id" 属性是对应折叠的内容 (<div id="demo">)。

**注意:** <a> 元素上你可以使用 href 属性来代替 data-target 属性:

```javascript
<a href="#demo" data-toggle="collapse">Collapsible</a>
 
<div id="demo" class="collapse">
Lorem ipsum dolor text....
</div>
```

**默认情况下折叠的内容是隐藏的，你可以添加 .show 类让内容默认显示:**

```javascript
<div id="demo" class="collapse show">
Lorem ipsum dolor text....
</div>
```

## 导航

如果你想创建一个简单的水平导航栏，可以在 <ul> 元素上添加 .nav类，在每个 <li> 选项上添加 .nav-item 类，在每个链接上添加 .nav-link 类:

```javascript
<ul class="nav">
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link disabled" href="#">Disabled</a>
  </li>
</ul>
```

### 导航对齐方式

.justify-content-center 类设置导航居中显示， .justify-content-end 类设置导航右对齐。

```javascript
<!-- 导航居中 -->
<ul class="nav justify-content-center">
 
<!-- 导航右对齐 -->
<ul class="nav justify-content-end">
</div>
```

### 垂直导航

.flex-column 类用于创建垂直导航

```javascript
<ul class="nav flex-column">
```

### 选项卡

使用 .nav-tabs 类可以将导航转化为选项卡。然后对于选中的选项使用 .active 类来标记。

```javascript
<ul class="nav nav-tabs">
  <li class="nav-item">
    <a class="nav-link active" href="#">Active</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link disabled" href="#">Disabled</a>
  </li>
</ul>
```

### 胶囊导航

.nav-pills 类可以将导航项设置成胶囊形状。

```javascript
<ul class="nav nav-pills">
  <li class="nav-item">
    <a class="nav-link active" href="#">Active</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link disabled" href="#">Disabled</a>
  </li>
</ul>
```

### 导航等宽

.nav-justified 类可以设置导航项齐行等宽显示。

```javascript
<ul class="nav nav-pills nav-justified">..</ul>
<ul class="nav nav-tabs nav-justified">..</ul>
```

### 动态选项卡

如果你要设置选项卡是动态可切换的，可以在每个链接上添加 data-toggle="tab" 属性。 然后在每个选项对应的内容的上添加 .tab-pane 类。

如果你希望有淡入效果可以在 .tab-pane 后添加 .fade类:

```javascript
<!-- Nav tabs -->
<ul class="nav nav-tabs">
  <li class="nav-item">
    <a class="nav-link active" data-toggle="tab" href="#home">Home</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" data-toggle="tab" href="#menu1">Menu 1</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" data-toggle="tab" href="#menu2">Menu 2</a>
  </li>
</ul>
 
<!-- Tab panes -->
<div class="tab-content">
  <div class="tab-pane active container" id="home">...</div>
  <div class="tab-pane container" id="menu1">...</div>
  <div class="tab-pane container" id="menu2">...</div>
</div>
```

### 胶囊下拉菜单

```javascript
<ul class="nav nav-pills">
  <li class="nav-item">
    <a class="nav-link active" href="#">Active</a>
  </li>
  <li class="nav-item dropdown">
    <a class="nav-link dropdown-toggle" data-toggle="dropdown" href="#">Dropdown</a>
    <div class="dropdown-menu">
      <a class="dropdown-item" href="#">Link 1</a>
      <a class="dropdown-item" href="#">Link 2</a>
      <a class="dropdown-item" href="#">Link 3</a>
    </div>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link disabled" href="#">Disabled</a>
  </li>
</ul>
```

### 选项卡下拉菜单

```javascript
<ul class="nav nav-tabs">
  <li class="nav-item">
    <a class="nav-link active" href="#">Active</a>
  </li>
  <li class="nav-item dropdown">
    <a class="nav-link dropdown-toggle" data-toggle="dropdown" href="#">Dropdown</a>
    <div class="dropdown-menu">
      <a class="dropdown-item" href="#">Link 1</a>
      <a class="dropdown-item" href="#">Link 2</a>
      <a class="dropdown-item" href="#">Link 3</a>
    </div>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#">Link</a>
  </li>
  <li class="nav-item">
    <a class="nav-link disabled" href="#">Disabled</a>
  </li>
</ul>
```

### 胶囊状动态选项卡

胶囊状动态选项卡只需要将以上实例的代码中 data-toggle 属性设置为 data-toggle="pill":

```javascript
<!-- Nav pills -->
<ul class="nav nav-pills">
  <li class="nav-item">
    <a class="nav-link active" data-toggle="pill" href="#home">Home</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" data-toggle="pill" href="#menu1">Menu 1</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" data-toggle="pill" href="#menu2">Menu 2</a>
  </li>
</ul>
 
<!-- Tab panes -->
<div class="tab-content">
  <div class="tab-pane active container" id="home">...</div>
  <div class="tab-pane container" id="menu1">...</div>
  <div class="tab-pane container" id="menu2">...</div>
</div>
```

