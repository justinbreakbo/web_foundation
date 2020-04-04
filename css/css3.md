# CSS3

CSS3参考手册：http://css.doyoe.com/



## CSS3选择器

CSS3新增了许多**灵活**查找元素的方法，极大的提高了查找元素的效率和**精准度**。CSS3选择器与 jQuery 中所提供的**绝大部分**选择器兼容。

### 属性选择器

> 属性选择器的标志性符号是 `[]`。

匹配含义：

```
^：开头  $：结尾  *：包含
```

- `E[title]` 选中页面的E元素，并且E存在 title 属性即可。
- `E[title="abc"]`选中页面的E元素，并且E需要带有title属性，且属性值**完全等于**abc。
- `E[attr~=val]` 选择具有 att 属性且属性值为：用空格分隔的字词列表，其中一个等于 val 的E元素。
- `E[attr|=val]` 表示要么是一个单独的属性值，要么这个属性值是以“-”分隔的。
- `E[title^="abc"]` 选中页面的E元素，并且E需要带有 title 属性,属性值以 abc 开头。
- `E[title$="abc"]` 选中页面的E元素，并且E需要带有 title 属性,属性值以 abc 结尾。
- `E[title*="abc"]` 选中页面的E元素，并且E需要带有 title 属性,属性值任意位置包含abc。



### 结构伪类选择器

> 伪类选择器的标志性符号是 `:`

- `E:first-child` 匹配父元素的第一个子元素E。
- `E:last-child` 匹配父元素的最后一个子元素E。
- `E:nth-child(n)` 匹配父元素的第n个子元素E。**注意**，盒子的编号是从`1`开始算起，不是从`0`开始算起。
- `E:nth-child(odd)` 匹配奇数
- `E:nth-child(even)` 匹配偶数
- `E:nth-last-child(n)` 匹配父元素的倒数第n个子元素E。



- `E:first-of-type` 匹配同类型中的第一个同级兄弟元素E。
- `E:last-of-type` 匹配同类型中的最后一个同级兄弟元素E。
- `E:nth-of-type(n)` 匹配同类型中的第n个同级兄弟元素E。
- `E:nth-last-of-type(n)` 匹配同类型中的倒数第n个同级兄弟元素E。



- `E:empty` 匹配没有任何子节点（包括空格等text节点）的元素E。
- `E:target` 匹配相关URL指向的E元素。要配合锚点使用。



### 伪元素选择器

> 伪元素选择器的标志性符号是 `::`

- `E::before` 设置在 元素E 前面（依据对象树的逻辑结构）的内容，配合content属性一起使用。

- `E::after` 设置在 元素E 后面（依据对象树的逻辑结构）的内容，配合content属性一起使用。

  `E:after`、`E:before `在CSS2旧版本里是伪类，在 CSS3 这个新版本里是伪元素。新版本里，`E:after`、`E:before`会被自动识别为`E::after`、`E::before`，按伪元素来对待，这样做的目的是用来做兼容处理。h5开发里面一般用`::after`的写法。

- `E::first-letter` 设置元素 E 里面的**第一个字符**的样式。

- `E::first-line` 设置元素 E 里面的**第一行**的样式。

- `E::selection` 设置元素 E 里面被鼠标选中的区域的样式（一般设置颜色和背景色）。



## 文本属性

### text-shadow：设置文本的阴影

格式举例：

```
	text-shadow: 20px 27px 22px pink;
	
    /* text-shadow 可以设置多个阴影，每个阴影之间使用逗号隔开*/
    text-shadow: -1px -1px 1px #fff, 1px 1px 1px #000;  
```

参数解释：水平位移 垂直位移 模糊程度 阴影颜色。



## 盒子属性

### 盒模型中的 box-sizing 属性

CSS3 对盒模型做出了新的定义，即允许开发人员**指定盒子宽度和高度的计算方式**。

这就需要用到 `box-sizing`属性。它的属性值可以是：`content-box`、`border-box`。解释如下。

**外加模式：**（css的默认方式）

```
	box-sizing: content-box;
```

解释：此时设置的 width 和 height 是**内容区域**的宽高。`盒子的实际宽度 = 设置的 width + padding + border`。此时改变 padding 和 border 的大小，也不会改变内容的宽高，而是盒子的总宽高发生变化。

**内减模式：**【需要注意】

```
	box-sizing: border-box;
```

解释：此时设置的 width 和 height 是**盒子**的总宽高。`盒子的实际宽度 = 设置的 width`。此时改变 padding 和 border 的大小，会改变内容的宽高，盒子的总宽高不变。



## 边框

边框的属性很多，其中**边框圆角**和**边框阴影**这两个属性，应用十分广泛，兼容性也相对较好，且符合**渐进增强**的原则，需要重点熟悉。

### 边框圆角：`border-radius` 属性

边框的每个圆角，本质上是一个圆，圆有**水平半径**和**垂直半径**：如果二者相等，就是圆；如果二者不等， 就是椭圆。

单个属性的写法：

```
	border-top-left-radius: 60px 120px;        //参数解释：水平半径   垂直半径

	border-top-right-radius: 60px 120px;

	border-bottom-left-radius: 60px 120px;

	border-bottom-right-radius: 60px 120px;
```

复合写法：

```
	border-radius: 60px/120px;             //参数：水平半径/垂直半径

	border-radius: 20px 60px 100px 140px;  //从左上开始，顺时针赋值。如果当前角没有值，取对角的值

	border-radius: 20px 60px;
```

最简洁的写法：（四个角的半径都相同时）

```
	border-radius: 60px;
```



### 边框阴影：`box-shadow` 属性

格式举例：

```
	box-shadow: 水平偏移 垂直偏移 模糊程度 阴影大小 阴影颜色

	box-shadow: 15px 21px 48px -2px #666;
```

参数解释：

- 水平偏移：正值向右，负值向左。
- 垂直偏移：正值向下，负值向上。
- 模糊程度：不能为负值。
- 阴影大小 ：值越大，阴影面积越大，可以为负值

**注意**：设置边框阴影不会改变盒子的大小，即不会影响其兄弟元素的布局。



### 边框图片

边框图片有以下属性：

```css
	/* 边框图片的路径*/
	border-image-source: url("images/border.png");

	/* 图片边框的裁剪*/
	border-image-slice: 27;

	/*图片边框的宽度*/
	border-image-width: 27px;

	/*边框图片的平铺*/
	/*repeat :正常平铺 但是可能会显示不完整*/
	/*round: 平铺 但是保证 图片完整*/
	/*stretch: 拉伸显示*/
	border-image-repeat: stretch;
```

我们也可以写成一个综合属性：

```
	 border-image: url("images/border.png") 27/20px round;
```



## 过渡

> `transition`的中文含义是**过渡**。过渡是CSS3中具有颠覆性的一个特征，可以实现元素**不同状态间的平滑过渡**（补间动画），经常用来制作动画效果。

- 补间动画：自动完成从起始状态到终止状态的的过渡。不用管中间的状态。
- 帧动画：通过一帧一帧的画面按照固定顺序和速度播放。如电影胶片。



transition 包括以下属性：

- `transition-property: all;` ，过渡属性。属性值可以是：
  -  ` width` 意思是只让盒子的宽度在变化时进行过渡
  -  ` all` 意思是让盒子的所有属性（包括宽度、背景色等）在变化时都进行过渡
- `transition-duration: 1s;` 过渡的持续时间。
- `transition-timing-function: linear;` 运动曲线。属性值可以是：
  - `linear` 线性
  - `ease` 减速
  - `ease-in` 加速
  - `ease-out` 减速
  - `ease-in-out` 先加速后减速
- `transition-delay: 1s;` 过渡延迟。多长时间后再执行这个过渡动画。

上面的四个属性也可以写成**综合属性**：

```
	transition: 让哪些属性进行过度 过渡的持续时间 运动曲线 延迟时间;

	transition: all 3s linear 0s;
```



## 转换

> 在 CSS3 当中，通过 `transform` 转换来实现 2D 转换或者 3D 转换。



**转换**是 CSS3 中具有颠覆性的一个特征，可以实现元素的**位移、旋转、变形、缩放**，甚至支持矩阵方式。

转换再配合过渡和动画，可以取代大量早期只能靠 Flash 才可以实现的效果。



### 2D转换

1. **缩放：scale**

   格式：

   ```
   	transform: scale(x, y);
   
   	transform: scale(2, 0.5);
   ```

   参数解释： x：表示水平方向的缩放倍数。y：表示垂直方向的缩放倍数。如果只写一个值就是等比例缩放。

   取值：大于1表示放大，小于1表示缩小。不能为百分比。

   

2. **位移：translate**

   格式：

   ```
   	transform: translate(水平位移, 垂直位移);
   
   	transform: translate(-50%, -50%);
   ```

   参数解释：

- 参数为百分比，相对于自身移动。
- 正值：向右和向下。 负值：向左和向上。如果只写一个值，则表示水平移动。



3. ****旋转：rotate***

   格式：

   ```
   	transform: rotate(角度);
   
   	transform: rotate(45deg);
   ```

   参数解释：正值 顺时针；负值：逆时针。



### 3D转换

1. **旋转：rotateX、rotateY、rotateZ**

   **3D坐标系（左手坐标系）**

   **格式：**

   ```
   	transform: rotateX(360deg);    //绕 X 轴旋转360度
   
   	transform: rotateY(360deg);    //绕 Y 轴旋转360度
   
   	transform: rotateZ(360deg);    //绕 Z 轴旋转360度
   ```

   

2. **移动：translateX、translateY、translateZ**

   **格式：**

   ```
   	transform: translateX(100px);    //沿着 X 轴移动
   
   	transform: translateY(360px);    //沿着 Y 轴移动
   
   	transform: translateZ(360px);    //沿着 Z 轴移动
   ```

   

3. **透视：perspective**

   电脑显示屏是一个 2D 平面，图像之所以具有立体感（3D效果），其实只是一种视觉呈现，通过透视可以实现此目的。

   透视可以将一个2D平面，在转换的过程当中，呈现3D效果。但仅仅只是视觉呈现出 3d 效果，并不是正真的3d。**需要呈现3D效果的转换都必须加透视**。

   格式有两种写法：

   - 作为一个属性，设置给父元素，作用于所有3D转换的子元素
   - 作为 transform 属性的一个值，做用于元素自身。

   格式举例：

   ```
   perspective: 500px;
   ```



4. **3D呈现**

   3D元素构建是指某个图形是由多个元素构成的，可以给这些元素的**父元素**设置`transform-style: preserve-3d`来使其变成一个真正的3D图形。属性值可以如下：

   ```
   transform-style: preserve-3d;     /* 让 子盒子 位于三维空间里 */
   
   transform-style: flat;            /* 让子盒子位于此元素所在的平面内（子盒子被扁平化） */
   ```



## 动画

> 动画是CSS3中具有颠覆性的特征，可通过设置**多个节点** 来精确控制一个或一组动画，常用来实现**复杂**的动画效果。

### 定义动画的步骤

1. 通过@keyframes定义动画；

2. 将这段动画通过百分比，分割成多个节点；然后各节点中分别定义各属性；

3. 在指定元素里，通过 `animation` 属性调用动画。

```
    定义动画：
        @keyframes 动画名{
            from{ 初始状态 }
            to{ 结束状态 }
        }

     调用：
      animation: 动画名称 持续时间；
```

其中，animation属性的格式如下：

```
animation: 定义的动画名称 持续时间  执行次数  是否反向  运动曲线 延迟执行。(infinite 表示无限次)

animation: move1 1s  alternate linear 3;

animation: move2 4s;
```



### 动画属性

上面的 animation 是综合属性，接下来，我们把这个综合属性拆分看看。

1. 动画名称：

```
	animation-name: move;
```

2. 执行一次动画的持续时间：

```
	animation-duration: 4s;
```

备注：上面两个属性，是必选项，且顺序固定。

3. 动画的执行次数：

```
	animation-iteration-count: 1;       //iteration的含义表示迭代
```

属性值`infinite`表示无数次。

4. 动画的方向：

```
	animation-direction: alternate;
```

属性值：normal 正常，alternate 反向。

5. 动画延迟执行：

```
	animation-delay: 1s;
```

6. 设置动画结束时，盒子的状态：

```
	animation-fill-mode: forwards;
```

属性值： forwards：保持动画结束后的状态（默认）， backwards：动画结束后回到最初的状态。

7. 运动曲线：

```
	animation-timing-function: ease-in;
```

属性值可以是：linear 、ease-in-out、 steps()等。

注意，如果把属性值写成**` steps()`**，则表示动画**不是连续执行**，而是间断地分成几步执行。



## Flex布局

> CSS3中的 flex 属性（弹性盒子），在布局方面做了非常大的改进，使得我们对**多个元素之间**的布局排列变得十分灵活，适应性非常强。其强大的伸缩性和自适应性，在网页开中可以发挥极大的作用。
>

**使用方法：给父容器仅仅加一个 `display: flex`属性**，就可以声明父容器为弹性盒子

**flex布局的优势和缺点：**

1. **flex 布局的子元素不会脱离文档流**，很好地遵从了“流的特性”。

   但你如果用 float 来做布局，float 属性的元素会脱离文档流，而且会涉及到各种 BFC、清除浮动的问题。浮动相关的问题，比较麻烦，所以也成了面试必问的经典题目。但有了 flex 布局之后，这些问题都不存在的。

2. **flex 是一种现代的布局方式，是 W3C 第一次提供真正用于布局的 CSS 规范**。 flex 非常提供了丰富的属性，非常灵活，让布局的实现更佳多样化，且方便易用。

3. flex 唯一的缺点就在于，**它不支持低版本的 IE 浏览器**。 flex 布局不支持 IE9 及以下的版本；IE10及以上也只是部分支持。如果你的页面不需要处理 IE浏览器的兼容性问题，则可以放心大胆地使用 flex 布局。



涉及 flex 的知识点的一些约定的概念：

- **弹性盒子**：指的是使用 `display:flex` 或 `display:inline-flex` 声明的**父容器**。
- **子元素/弹性元素**：指的是父容器里面的子元素们（父容器被声明为 flex 盒子的情况下）。

- 主轴：flex容器的主轴，默认是水平方向，从左向右。

- 侧轴：与主轴垂直的轴称作侧轴，默认是垂直方向，从上往下。

  

### 弹性盒子

- flex-direction 属性

  `flex-direction`：用于设置盒子中**子元素**的排列方向。属性值可以是：

  - row：从左到右水平排列子元素（默认值）
  - column：从上到下垂直排列子元素
  - row-reverse：从右到左排列子元素
  - column-reverse：从下到上排列子元素

- flex-wrap 属性

  `flex-wrap`：控制子元素溢出时的换行处理。

- justify-content 属性

  `justify-content`：控制子元素在主轴上的排列方式。



### 弹性元素

- justify-content 属性

  `justify-content` ：设置子元素在**主轴上的对齐方式**，属性值可以是：

  - `flex-start` 从主轴的起点对齐（默认值）
  - `flex-end` 从主轴的终点对齐
  - `center` 居中对齐
  - `space-around` 在父盒子里平分
  - `space-between` 两端对齐 平分

- align-items 属性

  `align-items`：设置子元素在**侧轴上的对齐方式**。属性值可以是：

  - `flex-start` 从侧轴开始的方向对齐 
  - `flex-end` 从侧轴结束的方向对齐 
  - `baseline` 基线 默认同flex-start
  -  `center` 中间对齐
  - `stretch` 拉伸

- `flex`属性

  `flex`：设置子盒子的权重

  ```
  section:nth-child(1) ul li:nth-child(1){
  	flex:1;
  }
  
  section:nth-child(1) ul li:nth-child(2){
  	flex:1;
  }
  
  section:nth-child(1) ul li:nth-child(3){
  	flex:8;
  }
  ```

  

## Web字体

> 开发人员可以为自已的网页指定特殊的字体（将指定字体提前下载到站点中），无需考虑用户电脑上是否安装了此特殊字体。从此，把特殊字体处理成图片的方式便成为了过去。
>
> 支持程度比较好，甚至 IE 低版本的浏览器也能支持。

**我们就需要为不同的浏览器准备不同格式的字体**。通常我们会通过字体生成工具帮我们生成各种格式的字体，因此无需过于在意字体格式之间的区别。

详细使用步骤见 [原文]([https://github.com/qianguyihao/Web/blob/master/02-CSS%E5%9F%BA%E7%A1%80/14-CSS3%E5%B1%9E%E6%80%A7%E8%AF%A6%E8%A7%A3%EF%BC%9AWeb%E5%AD%97%E4%BD%93.md](https://github.com/qianguyihao/Web/blob/master/02-CSS基础/14-CSS3属性详解：Web字体.md))



## 处理兼容性问题：私有前缀

通过网址http://caniuse.com/ 可以查询CSS3各特性的支持程度。

处理兼容性问题的常见方法：为属性添加**私有前缀**。

如此方法不能解决，应尽量避免使用，无需刻意去处理CSS3的兼容性问题。



比如说，我想给指定的div设置下面这样一个属性：

```
	background: linear-gradient(left, green, yellow);
```

上面这个属性的作用是：添加从左到右的线性渐变，颜色从绿色变为黄色。

如果直接像上面这样写属性，是看不到效果的。此时，我们可以**为浏览器添加不同的私有前缀**，属性就可以生效了。

格式如下：

```
    -webkit-: 谷歌 苹果
    -moz-:火狐
    -ms-：IE
    -o-：欧朋
```

格式举例如下：

```
    background: -webkit-linear-gradient(left, green, yellow);
    background: -moz-linear-gradient(left, green, yellow);
    background: -ms-linear-gradient(left, green, yellow);
    background: -o-linear-gradient(left, green, yellow);
    background: linear-gradient(left, green, yellow);
```

