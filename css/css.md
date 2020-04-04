# CSS

## 样式表

CSS和HTML结合的方式，其实就是问你css的代码放在哪里比较合适。CSS代码理论上的位置是任意的，**但通常写在`<style>`标签里**。只要是`<style>`标签里的代码，那就是css代码，浏览器就是这样来进行解析的。

CSS和HTML的结合方式有3种：

- **行内样式**：在某个特定的标签里采用style**属性**。范围只针对此标签。

- **内嵌样式表**：在页面的head里采用``**标签**。范围针对此页面。

- 引入外部样式表css文件

  的方式。这种引入方式又分为两种：

  - 采用`<link>`标签。例如：`<link rel = "stylesheet" type = "text/css" href = "a.css"></link>`
  - 采用import，必须写在``标签中，并且必须是第一句。例如：`@import url(a.css) ;`

> 两种引入样式方式的区别：外部样式表中不能写标签，但是可以写import语句。



## 选择器

**基本选择器：**

- 标签选择器：针对**一类**标签 （直接写标签名字）
- ID选择器：针对某**一个**特定的标签使用 （用#来定义）
- 类选择器：针对**你想要的所有**标签使用 （ 用.来定义）
- 通用选择器（通配符）：针对所有的标签都适用（不建议使用）

**高级选择器：**

- 后代选择器：用空格隔开

- 交集选择器：选择器之间紧密相连

- 并集选择器（分组选择器）：用逗号隔开

- 伪类选择器：用冒号来表示

  **伪类**：同一个标签，根据其**不同的种状态，有不同的样式**。这就叫做“伪类”。

  （1）**静态伪类**：只能用于**超链接**的样式。如下：

  - `:link` 超链接点击之前
  - `:visited` 链接被访问过之后

  PS：以上两种样式，只能用于超链接。

  （2）**动态伪类**：针对**所有标签**都适用的样式。如下：

  - `:hover` “悬停”：鼠标放到标签上的时候
  - `:active` “激活”： 鼠标点击标签，但是不松手时。
  - `:focus` 是某个标签获得焦点时的样式（比如某个输入框获得焦点）

  在css中，a标签的四种状态**必须按照固定的顺序写**：（love hate）

  `a:link 、a:visited 、a:hover 、a:active`    （`a:link`和`a:visited`是一个整体，要么同时写，要么同时不写）

  **`a{}`和`a:link{}`的区别：**
  
  - `a{}`定义的样式针对所有的超链接(包括锚点)
  - `a:link{}`定义的样式针对所有写了href属性的超链接(不包括锚点)
  
  

一些其他选择器例子：

```
div>p 子代选择器（注意不是后代）
* : 通配符
div+p: 选中div后面相邻（兄弟）的第一个p
div~p: 选中的div后面所有的p
```




## 继承性

- 关于文字样式的属性，都具有继承性。这些属性包括：color、 text-开头的、line-开头的、font-开头的。
- 关于盒子、定位、布局的属性，都不能继承。



## 层叠性

层叠性。层叠性是一种能力，就是处理冲突的能力。当不同选择器，对一个标签的同一个样式，有不同的值，听谁的？这就是冲突。css有着严格的处理冲突的机制。

当多个选择器，选择上了某个元素的时候，要按照如下顺序统计权重：

1. id 选择器

2. 类选择器、属性选择器、伪类选择器

3. 标签选择器、伪元素选择器

因为对于相同方式的样式表，其选择器排序的优先级为：ID选择器 > 类选择器 > 标签选择器

- 权重不同时：作用于同一个元素的样式，先比较其ID选择器的数量，哪个多就那个胜出，相同的情况下比较类选择器，以此类推。
- 权重相同时：看最后一个选择器的优先级谁更高谁胜出（就近原则）

如果不能**直接选中**某个元素，通过继承性影响的话，那么权重是0。



**CSS样式表的冲突的总结**

- 对于相同的选择器（比如同样都是类选择器），其样式表排序：行级样式 > 内嵌样式表 > 外部样式表（就近原则）
- 对于相同类型的样式表（比如同样都是内部样式表），其选择器排序：ID选择器 > 类选择器 > 标签选择器
- 外部样式表的ID选择器 > 内嵌样式表的标签选择器(先看选择器优先级，再看样式表优先级)



**注意：属性值后面加一个`!important`标记，该属性权重为无穷大。**

没选中（权重为0）属性加了也没有用，权重还是零。（`!important`尽量不要用，否则会让css写得很乱）

eg：`font-size:60px !important;`



## 单位

- 绝对单位：in、cm、mm、pt、pc

  1 `in`=2.54`cm`=25.4`mm`=72`pt`=6`pc`。

- 相对单位：px、rem、em、%

  - `px`：像素
  - `em`：相对于当前使用em单位的对象内文本的字体尺寸，font-size是多少px，em就是多少px
  - `rem`：相对于html根元素的字体尺寸，font-size是多少px，em就是多少px（css3新增）

  **px 与 rem 的选择？**

  对于只需要适配少部分手机设备，且分辨率对页面影响不大的，使用px即可 。

  对于需要适配各种移动设备，使用rem，例如只需要适配iPhone和iPad等分辨率差别比较挺大的设备。



## 字体属性

```css
p{
	font-size: 50px; 		/*字体大小*/
	line-height: 30px;      /*行高*/
	font-family: 幼圆,黑体; 	/*字体类型：如果没有幼圆就显示黑体，没有黑体就显示默认*/
	font-style: italic ;		/*italic表示斜体，normal表示不倾斜*/
	font-weight: bold;	/*粗体*/
	font-variant: small-caps;  /*小写变大写*/
}
```

- 字体写法：`font-family: "Times New Roman","微软雅黑","宋体";` 

  上方代码的意思是，英文会采用Times New Roman字体，而中文会采用微软雅黑字体（因为美国人设计的Times New Roman字体并不针对中文，所以中文会采用后面的微软雅黑）

- 连写格式：`font: 加粗 字号/行高/ 字体`	  

  连写示例：`font: 400 14px/24px "宋体";`    （PS：400是nomal，700是bold）

  

## 文本属性

CSS样式中，常见的文本属性有以下几种：

- `letter-spacing: 0.5cm ;` 单个字母之间的间距
- `word-spacing: 1cm;` 单词之间的间距
- `text-decoration: none;` 字体修饰：none 去掉下划线、**underline 下划线**、line-through 中划线、overline 上划线
- `text-transform: lowercase;` 单词字体大小写。uppercase大写、lowercase小写
- `color:red;` 字体颜色
- `text-align: center;` 在当前容器中的对齐方式。属性值可以是：left、right、center（**在当前容器的中间**）、justify
- `text-transform: lowercase;` 单词的字体大小写。属性值可以是：`uppercase`（单词大写）、`lowercase`（单词小写）、`capitalize`（每个单词的首字母大写）

![img](https://camo.githubusercontent.com/eedba3fdcf4a77513183078909dfdbdca8362c81/687474703a2f2f696d672e736d79687661652e636f6d2f323031352d31302d30332d6373732d31382e706e67)



## 列表属性

列表有以下几个属性：

- `list-style-image:url;` 将图像设置为列表标记项

- `list-style-positon:inside;` 设置列表中列表项标记被防止的位置

- `list-style-type` 设置列表项标记的类型

- `list-style` 上面三个属性的简写属性，用于把所有属性写在一个声明中

  用列表写导航栏一般设置：`list-style: none;/*去掉列表前面的圆点*/`
  
  ```
  ul{
      /*去掉小圆点*/
      list-style: none;
  }
  ```
  
  

```
ul li{
	list-style-image:url(images/2.gif) ;  /*列表项前设置为图片*/
	margin-left:80px;  /*公有属性*/
}
```

![img](https://camo.githubusercontent.com/8d85ff3a6d81a463641c609288ae20ee8023c56e/687474703a2f2f696d672e736d79687661652e636f6d2f323031352d31302d30332d6373732d32362e706e67)



## 鼠标属性

鼠标的属性`cursor`有以下几个常用属性值：

- `auto`：默认值。浏览器根据当前情况自动确定鼠标光标类型。
- `pointer`：IE6.0，竖起一只手指的手形光标。就像通常用户将光标移到超链接上时那样。
- `hand`：和`pointer`的作用一样：竖起一只手指的手形光标。就像通常用户将光标移到超链接上时那样。

```
p:hover{
	cursor: pointer;
}
```

`:hover`  hover选择器用于选择鼠标指针浮动在上面的元素，可用于所有元素，不只是链接。

- 还有一堆其他属性值，需要用的时候再查。



## 滤镜

eg：让图片变成灰度图的效果，可以这样设置滤镜：

```
	<img src="test.jpg" style="filter:gray()">
```



## overflow属性

`overflow`属性的属性值可以是：

- `visible`：默认值。多余的内容不剪切也不添加滚动条，会全部显示出来。
- `hidden`：不显示超过对象尺寸的内容。
- `auto`：如果内容不超出，则不显示滚动条；如果内容超出，则显示滚动条。
- `scroll`：Windows 平台下，无论内容是否超出，总是显示滚动条。Mac 平台下，和 `auto` 属性相同。





## 背景属性

**CSS2.1** 中，常见的背景属性有以下几种：（经常用到，要记住）

- `background-color:#ff99ff;` 设置元素的背景颜色。

- `background-image:url(images/test.gif);` 将图像设置为背景。

- `background-repeat: no-repeat;` 设置背景图片是否重复及如何重复，默认平铺满。（重要）

  - `no-repeat`不要平铺；
  - `repeat-x`横向平铺；
  - `repeat-y`纵向平铺。

- `background-position:center top;` 设置背景图片在当前容器中的位置。

  - 可以用单词描述属性值 `background-position: 描述左右的词 描述上下的词;`
  - 可以用像素值描述属性值 `background-position:向右偏移量 向下偏移量;`

- `background-attachment:scroll;` 设置背景图片是否跟着滚动条一起移动。 属性值可以是：`scroll`（与fixed属性相反，默认属性）、`fixed`（背景就会被固定住，不会被滚动条滚走）。

- 另外还有一个综合属性叫做`background`，它的作用是：将上面的多个属性写在一个声明中。

  ```
  background:red url(1.jpg) no-repeat 100px 100px fixed;
  ```

**CSS3** 中，新增了一些background属性：

- `background-origin`  背景原点，控制背景从什么地方开始显示

  - `padding-box` 内边距开始显示背景图
  - `border-box` 边框开始显示背景图
  - `conten-box` 内容区域开始显示背景图

- `background-clip` 背景裁切，设置元素的背景（图片或颜色）是否延伸到边框下面

  - `border-box` 超出 border-box 的部分，将裁剪掉
  - `padding-box` 超出 padding-box 的部分，将裁剪掉
  - `content-box` 超出 content-box 的部分，将裁剪掉

- `background-size` 调整尺寸

- 多重背景

  我们可以给一个盒子同时设置多个背景，用以逗号隔开即可。可用于自适应局。

  ```
   background: url(images/bg1.png) no-repeat left top,
              url(images/bg2.png) no-repeat right top,
              url(images/bg3.png) no-repeat right bottom,
              url(images/bg4.png) no-repeat left bottom,
              url(images/bg5.png) no-repeat center;
  ```



### 渐变

>  background-image的×××-gradient属性

渐变分为：

- 线性渐变：沿着某条直线朝一个方向产生渐变效果。

  格式：`background-image: linear-gradient(方向, 起始颜色, 终止颜色);`

  例子：`background-image: linear-gradient(to right, yellow, green);`

  - 方向可以是：`to left`、`to right`、`to top`、`to bottom`、角度`30deg`（指的是顺时针方向30°）。

- 径向渐变：从一个**中心点**开始沿着**四周**产生渐变效果。

  格式：`background-image: radial-gradient(辐射的半径大小, 中心的位置, 起始颜色, 终止颜色);`

  例子：`background-image: radial-gradient(100px at center,yellow ,green);`

- 重复渐变。



### 裁剪元素

> clip-path

```
    .div1 {
        width: 320px;
        height: 320px;
        border: 1px solid red;
        background: url(http://img.smyhvae.com/20191006_1410.png) no-repeat;
        background-size: cover;

        /* 裁剪出圆形区域，100px 100px 为定点坐标 */
        clip-path: circle(50px at 100px 100px); 
        transition: clip-path .4s;
    }
    .div1:hover{
        /* 鼠标悬停时，裁剪出更大的圆形 */
        clip-path: circle(80px at 100px 100px);
    }
```





## 盒子模型

盒子模型，英文即box model。无论是div、span、还是a都是盒子。

但是，图片、表单元素一律看作是文本，它们并不是盒子。这个很好理解，比如说，一张图片里并不能放东西，它自己就是自己的内容。



一个盒子中主要的属性就5个：width、height、padding、border、margin。如下：

- width和height：**内容**的宽度、高度（不是盒子的宽度、高度）。
- padding：内边距。
- border：边框。
- margin：外边距。



CSS盒模型和IE盒模型的区别：

- 在 **标准盒子模型**中，**width 和 height 指的是内容区域**的宽度和高度。增加内边距、边框和外边距不会影响内容区域的尺寸，但是会增加元素框的总尺寸。
- **IE盒子模型**中，**width 和 height 指的是内容区域+border+padding**的宽度和高度。

```
    /* 设置当前盒子为 标准盒模型（默认） */
    box-sizing: content-box;

    /* 设置当前盒子为 IE盒模型 */
    box-sizing: border-box;
```



## 浮动

> 浮动是css里面布局用的最多的属性。

标准文档流等级森严。标签分为两种等级：

- 行内元素（除了p标签以外的所有文本及标签）
  - 与其他行内元素并排；
  - 不能设置宽、高。默认的宽度，就是文字的宽度（可以设置margin、padding、border）。
- 块级元素（所有的容器及标签和p标签）
  - 霸占一行，不能与其他任何元素并列；
  - 能接受宽、高。如果不设置宽度，那么宽度将默认变为父亲的100%。

> 块级转行内：display: inline;
>
> 行内转块级：display: block;

css中一共有三种手段，使一个元素脱离标准文档流（不再区分行内元素和块级元素）：

- 浮动
- 绝对定位
- 固定定位



### 浮动的三个性质

1. 脱离标准流

2. 浮动的元素互相贴靠

3. 浮动的元素有“字围”效果，即浮动的div挡住了不浮动的p，但不会挡住p中的文字。

   **标准流中的文字不会被浮动的盒子遮挡住**。（文字就像水一样）

4. 收缩，浮动的元素没有设置width，将自动收缩为内容的宽度。



### 浮动的清除（四个方法）

> 浮动的清除即清除浮动带来的影响

1. 给浮动元素的祖先元素增加高度

   > 如果一个元素要浮动，那么它的祖先元素一定要有高度。
   >
   > 有高度的盒子，才能关住浮动。（记住这句过来人的经验之语）

2. clear: both;

   clear就是清除，both指的是左浮动、右浮动都要清除。`clear:both`的意思就是：**不允许左侧和右侧有浮动对象。**

   这种方法有一个非常大的、致命的问题，**它所在的标签，margin属性失效了**。

3. 隔墙法

   - 外墙法：在两部分浮动元素中间，建一个墙，在墙里面`clear: both;`。墙隔开两部分浮动，让后面的浮动元素，不去追前面的浮动元素。 墙用自己的身体当做了间隙。（但是第一个div，还是没有高度）

   - 内墙法：把墙建在第一个元素里面，就可以让让第一个div，自动根据自己的儿子撑出高度。

4. overflow: hidden;

   一个父亲不能被自己浮动的儿子，撑出高度。但是，只要给父亲加上`overflow:hidden`; 那么，父亲就能被儿子撑出高了。这是一个浏览器偏方。

   （建议用该方法，美观又简单）



### 浮动与margin相关的知识

- margin塌陷：浮动的两个盒子之间没有margin塌陷现象

- 盒子水平居中：`margin:0 auto;` ，脱离标准文档流的盒子不能使用`margin:0 auto`

  > - 上下的margin为0，左右的margin都尽可能的大，于是就居中了。
  >
  > - 使用`margin:0 auto;`的盒子，必须有width，有明确的width。
  >
  > - `margin:0 auto;` 是让盒子居中，不是让盒子里的文本居中。文本的居中，要使用`text-align:center;`

- 善用父亲的padding，而不是儿子的margin

  **margin这个属性，本质上描述的是兄弟和兄弟之间的距离； 最好不要用这个marign表达父子之间的距离。**所以，如果要表达父子之间的距离，我们一定要善于使用父亲的padding，而不是儿子的margin。



## 定位属性

### 相对定位

> 让元素相对于自己原来的位置，进行位置调整（可用于盒子的位置微调）。

```
	position: relative;
	left: 50px;
	top: 50px;
```

用途：

- 微调元素
- 做绝对定位的参考（父容器），子绝父相



### 绝对定位

> 定义横纵坐标。原点在父容器的左上角或左下角。横坐标用left表示，纵坐标用top或者bottom表示。（脱离标准文档流）

```
	position: absolute;  /*绝对定位*/
	left: 10px;  /*横坐标*/
	top/bottom: 20px;  /*纵坐标*/
```

注意点：

1. 要听最近的**已经定位**的祖先元素的，不一定是父亲，可能是爷爷

   工程上应用：子绝父相（父亲没有脱标，儿子脱标在父亲的范围里面移动）

   > 父亲浮动，设置相对定位（零偏移），然后让儿子绝对定位一定的距离。

2. 不一定是相对定位，任何定位，都可以作为儿子的参考点：

3. 绝对定位的儿子，无视参考的那个盒子的padding：



### 固定定位

> 就是相对浏览器窗口进行定位。无论页面如何滚动，这个盒子显示的位置不变。（IE6不兼容）

```
    position: fixed;
    bottom: 100px;
    right: 30px;
```

用途：

- 网页右下角的“返回到顶部”
- 顶部导航条



### z-index属性

> 表示谁压着谁。数值大的压盖住数值小的。

特性如下：

1. 属性值大的位于上层，属性值小的位于下层。

2. z-index值没有单位，就是一个正整数。默认的z-index值是0。

3. 如果大家都没有z-index值，或者z-index值一样，那么在HTML代码里谁写在后面，谁就在上面能压住别人。定位了的元素，永远能够压住没有定位的元素。

4. 只有定位了的元素，才能有z-index值。也就是说，不管相对定位、绝对定位、固定定位，都可以使用z-index值。**而浮动的元素不能用**。

5. 从父现象：父亲怂了，儿子再牛逼也没用。意思是，如果父亲1比父亲2大，那么，即使儿子1比儿子2小，儿子1也能在最上层。



## 水平垂直居中

### 行内元素

- 水平居中

  给父容器设置：

  ```
      text-align: center;
  ```

- 垂直居中

  让**文字的行高** 等于 **盒子的高度**，可以让单行文本垂直居中。比如：

  ```
  .father {
      height: 20px;
      line-height: 20px;
  }
  ```

### 块级元素

> 弹窗要求严格水平垂直居中，例如：移动端红包弹窗

- 水平居中

  给自身设置：

  ```
  	margin: 0 auto;	 /*水平居中*/
  	margin: auto;  /*本意是水平垂直居中，但这种方法垂直居中不起效，只剩水平居中的效果*/
  ```

  这种方法对浮动的元素不起作用（实际上浮动的元素没有什么居中的需求）

- 垂直水平居中

  - 绝对定位 + margin（需要指定子元素的宽高，不推荐）

    ```css
    div {
        width: 600px;
        height: 60px;
        position: absolute;  绝对定位的盒子
        top: 50%;				
        left: 50%;           首先，让左上角居中
        top: 0;
        margin-left: -300px;	向左移动宽度（600px）的一半
        margin-top: -300px;		向上移动宽度（600px）的一半
        /*margin-left为负数，自身会左移，后面元素会补位，不会破坏文档流*/
    }
    ```

    此方法可同时垂直水平居中，要求指定子元素的宽高，才能写出 `margin-top` 和 `margin-left` 的属性值。

    但是，在通常情况下，对那些需要居中的元素来说，其宽高往往是由其内容来决定的，不建议固定宽高。

  - **绝对定位 + translate（无需指定子元素的宽高，推荐）**

    ```
    .son {
        position: absolute;
        background: red;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
    ```

    此方法可同时垂直水平居中，在没有指定子元素宽高的情况下，也能让其在父容器中垂直居中。因为 translate() 函数中使用百分比值时，是以这个元素自身的宽度和高度为基准进行换算和移动的（**动态计算宽高**）。

  - flex布局（待改进）

    ```
    .father{
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
        background: pink;
    }
    .son {
    	background: red;
    }
    ```

    将父容器设置为 Flex 布局，再给父容器加个属性`justify-content: center`，这样的话，子元素就能水平居中了；再给父容器加个属性 `align-items: center`，这样的话，子元素就能垂直居中了。

  - flex布局+margin:auto （推荐）

    ```
    .father{
        display: flex;
        min-height: 100vh;
        background: pink;
    }
    .son {
        margin: auto;
        background: red;
    }
    ```

    我们只需写两行声明即可：先给父容器设置 `display: flex`，再给指定的子元素设置我们再熟悉不过的 `margin: auto`，即可让这个指定的子元素在**剩余空间**里，水平垂直居中。大功告成。