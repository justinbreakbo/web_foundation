# JavaScript

JavaScript基础分为三个部分：

- ECMAScript：JavaScript的语法标准。包括变量、表达式、运算符、函数、if语句、for语句等。
- **DOM**：文档对象模型（Document object Model），操作**网页上的元素**的API。比如让盒子移动、变色、轮播图等。
- **BOM**：浏览器对象模型（Browser Object Model），操作**浏览器部分功能**的API。比如让浏览器自动滚动。

![img](https://camo.githubusercontent.com/e82acbb54f1a12e60c41b7c220dcaa9ea0daa8f9/687474703a2f2f696d672e736d79687661652e636f6d2f32303138303230315f323035322e706e67)

## ECMAScript

### 数组

**数组的四个基本方法如下**：（数组元素的添加和删除）

| 方法      | 描述                                                         | 备注         |
| --------- | ------------------------------------------------------------ | ------------ |
| push()    | 向数组的**最后面**插入一个或多个元素，返回结果为**该数组新的长度** | 会改变原数组 |
| pop()     | 删除数组中的**最后一个**元素，返回结果为**被删除的元素**     | 会改变原数组 |
| unshift() | 在数组**最前面**插入一个或多个元素，返回结果为**该数组新的长度** | 会改变原数组 |
| shift()   | 删除数组中的**第一个**元素，返回结果为**被删除的元素**       | 会改变原数组 |

**数组的常见方法如下**：

| 方法          | 描述                                                         | 备注           |
| ------------- | ------------------------------------------------------------ | -------------- |
| slice(n1, n2) | 从数组中**提取**指定的一个或多个元素，返回结果为**新的数组** | 不会改变原数组 |
| splice()      | 从数组中**删除**指定的一个或多个元素，返回结果为**新的数组**（也可以增加元素） | 会改变原数组   |
| concat()      | 连接两个或多个数组，返回结果为**新的数组**                   | 不会改变原数组 |
| join()        | 将数组转换为字符串，返回结果为**转换后的字符串**             | 不会改变原数组 |
| reverse()     | 反转数组，返回结果为**反转后的数组**                         | 会改变原数组   |
| sort()        | 对数组的元素,默认按照**Unicode编码**，从小到大进行排序<br />对number排序时，一般要声明一个回调函数function (a,b){ return a-b } | 会改变原数组   |

**遍历数组的方法如下**：

| 方法      | 描述                                                         | 备注                                                   |
| --------- | ------------------------------------------------------------ | ------------------------------------------------------ |
| for循环   | 这个大家都懂                                                 |                                                        |
| forEach() | 和 for循环类似，但需要兼容IE8以上                            | forEach() 没有返回值。也就是说，它的返回值是 undefined |
| map()     | 对原数组中的每一项进行加工，将组成新的数组                   | 不会改变原数组                                         |
| filter()  | 对数组中每一项运行回调函数，该函数返回结果是true的项，将组成新的数组，返回结果为**新的数组**。可以起到过滤的作用 | 不会改变原数组                                         |
| every()   | 如果有一项返回false，则停止遍历，此方法返回 false            | 一假即假。要求每一项都返回true，最终的结果才返回true   |
| some()    | 只要有一项返回true，则停止遍历，此方法返回true               | 一真即真。要求每一项都返回false，最终的结果才返回false |
| reduce    | 为数组中的每一个元素，依次执行回调函数                       |                                                        |

**数组的其他方法如下**：

| 方法                             | 描述                                                | 备注 |
| -------------------------------- | --------------------------------------------------- | ---- |
| indexOf(value)                   | 从前往后索引，获取 value 在数组中的第一个下标       |      |
| lastIndexOf(value)               | 从后往前索引，获取 value 在数组中的最后一个下标     |      |
| find(function())                 | 找出**第一个**满足「指定条件返回true」的元素。      |      |
| findIndex(function())            | 找出**第一个**满足「指定条件返回true」的元素的index |      |
| Array.from(arrayLike)            | 将**伪数组**转化为**真数组**                        |      |
| Array.of(value1, value2, value3) | 将**一系列值**转换成数组。                          |      |

### 函数

#### 普通函数

常见的函数

匿名函数

箭头函数：更简短的函数且不绑定this值

回调函数：一个函数作为参数传递给另一个函数

#### 构造函数

与普通函数相比，构造函数有以下明显特点：

- 用new关键字调用。
- 不需要用return显式返回值的，默认会返回this，也就是新的实例对象。
- 建议函数名的首字母大写，与普通函数区分开。

```
    function Foo(name, age) {
        this.name = name;
        this.age = age;
        //retrun this;   //默认有这一行。new一个构造函数，返回一个对象

    }

    var fn1 = new Foo('smyhvae', 26);
    var fn2 = new Foo('vae',30);    //new 多个实例对象
```



### 原型模式

原型模式是js对继承的一种实现

- `prototype`：构造函数中的属性，指向该构造函数的原型对象。

- `_proto_`：实例中的属性，指向new这个实例的构造函数的原型对象

- `constructor`：原型对象中的属性，指向该原型对象的构造函数

  

**原型、构造函数、实例三者的区别：**

![](/home/just/Pictures/687474703a2f2f696d672e736d79687661652e636f6d2f32303138303330365f323130372e706e67.png)

- 构造函数通过 new 生成实例

- 构造函数也是函数，构造函数的`prototype`指向原型。（所有的函数有`prototype`属性，但实例没有 `prototype`属性）

- 原型对象中有 constructor，指向该原型的构造函数。

  **注意：Foo.prototype.constructor === Foo**（Foo为构造函数）



**`instanceof`的原理**

`instanceof`的**作用**：用于判断**实例**属于哪个**构造函数**。

`instanceof`的**原理**：判断实例对象的`__proto__`属性，和构造函数的`prototype`属性，是否为同一个引用（是否指向同一个地址）。



#### 原型规则

- 所有的引用类型（数组、对象、函数），都具有对象特性，都可以**自由扩展属性**。null除外。
- 所有的**引用类型**（数组、对象、函数），都有一个`_proto_`属性，属性值是一个**普通的对象**。`_proto_`的含义是隐式原型
- 所有的**函数**（不包括数组、对象），都有一个`prototype`属性，属性值是一个**普通的对象**。`prototype`的含义是**显式原型**。（实例没有这个属性）
- 所有的**引用类型**（数组、对象、函数），`_proto_`属性指向它的**构造函数**的`prototype`值
- 当试图获取一个对象的某个属性时，如果这个对象本身没有这个属性，那么会去它的`_proto_`中寻找（即它的构造函数的`prototype`）。

#### 原型链

在实例p1中想要调用一个方法或者属性的时候会沿原型链向上查找。

### 继承

1. 组合继承：结合 原型链+借用构造函数 方式，实现组合继承。
2. 原型式继承：借助原型，基于已有的对象创建新对象。
3. 寄生继承：创建一个用于封装继承过程的函数，在函数内部增强对象，并返回对象。
4. 寄生组合式继承：借用构造函数来继承属性，通过原型链混成来继承方法。不必在子类原型中调用超类的构造函数。使用寄生继承来继承超类的原型，再将结果制定给子类的原型。

#### this

三个函数能改变this的指向：`call()` `apply()` `bind()`，三个函数的异同可参考 [此处]([https://github.com/qianguyihao/Web/blob/master/05-JavaScript%E8%BF%9B%E9%98%B6/call%E3%80%81apply%E3%80%81bind%E7%9A%84%E5%8C%BA%E5%88%AB.md](https://github.com/qianguyihao/Web/blob/master/05-JavaScript进阶/call、apply、bind的区别.md))



this关键字永远指向函数（方法）运行时的**所有者**。

- 函数赋值给变量时，this指向window

- 以函数形式调用时，this永远都是window
- 以方法的形式调用时，this是调用方法的对象



### 正则表达式

正则表达式：查找一个字符串是否包含正则表达式所描述的东西（用test方法）

> test() 方法用于检测一个字符串是否匹配某个模式.

```
const reg = /test/g;   也可以用new方法来声明正则表达式
const str = '_test_test';

console.log(reg.test(str));
```

String对象的如下方法，是支持正则表达式的：

| 方法      | 描述                                                   | 备注 |
| --------- | ------------------------------------------------------ | ---- |
| split()   | 将字符串拆分成数组                                     |      |
| search()  | 搜索字符串中是否含有指定内容，返回索引 index           |      |
| match()   | 根据正则表达式，从一个字符串中将符合条件的内容提取出来 |      |
| replace() | 将字符串中的指定内容，替换为新的内容并返回             |      |

```
	var str = "1a2b3c4d5e6f7g";

	var result = str.split(/[A-z]/); // 参数是一个正则表达式：表示所有字母  （直接写正则表达式）
	console.log(result);
```



用途：

- 检查一个字符串是否是一个合法手机号

  ```
  	var phoneStr = "13067890123";
  	var phoneReg = /^1[3-9][0-9]{9}$/;
  	console.log(phoneReg.test(phoneStr));
  ```

- 去掉字符串开头和结尾的空格

  ```
  str = str.replace(/^\s*|\s*$/g,"");
  ```

- 判断字符串是否为电子邮件

  ```
  	var emailReg = /^\w{3,}(\.\w+)*@[A-z0-9]+(\.[A-z]{2,5}){1,2}$/;
  	var email = "abchello@163.com";
  	console.log(emailReg.test(email));
  ```





## DOM

> 使用 HTML DOM 来增强网站的动态交互性

### 节点

根据 W3C 的 HTML DOM 标准，HTML 文档中的所有内容都是节点：

- 整个文档是一个文档节点
- 每个 HTML 元素是元素节点
- HTML 元素内的文本是文本节点
- 每个 HTML 属性是属性节点
- 注释是注释节点

### 方法

> HTML DOM 方法是我们可以在节点（HTML 元素）上执行的动作。
>
> HTML DOM 属性是我们可以在节点（HTML 元素）设置和修改的值。

| 方法                     | 描述                                                         |
| :----------------------- | :----------------------------------------------------------- |
| getElementById()         | 返回带有指定 ID 的元素。                                     |
| getElementsByTagName()   | 返回包含带有指定标签名称的所有元素的节点列表（集合/节点数组）。 |
| getElementsByClassName() | 返回包含带有指定类名的所有元素的节点列表。                   |
| appendChild()            | 把新的子节点添加到指定节点。                                 |
| removeChild()            | 删除子节点。                                                 |
| replaceChild()           | 替换子节点。                                                 |
| insertBefore()           | 在指定的子节点前面插入新的子节点。                           |
| createAttribute()        | 创建属性节点。                                               |
| createElement()          | 创建元素节点。                                               |
| createTextNode()         | 创建文本节点。                                               |
| getAttribute()           | 返回指定的属性值。                                           |
| setAttribute()           | 把指定属性设置或修改为指定的值。                             |

### 属性

> 属性是节点（HTML 元素）的值，您能够获取或设置。

- innerHTML属性

  获取元素内容的最简单方法是使用 innerHTML 属性。

  innerHTML 属性对于获取或替换 HTML 元素的内容很有用

  ```
  <script> 
      var txt=document.getElementById("intro").innerHTML; document.write(txt); 
  </script>
  ```

- nodeValue 属性

  nodeValue 属性规定节点的值。

  - 元素节点的 nodeValue 是 undefined 或 null
  - 文本节点的 nodeValue 是文本本身
  - 属性节点的 nodeValue 是属性值

  ```
  <script> 
      x=document.getElementById("intro"); 
      document.write(x.firstChild.nodeValue); 
  </script>
  ```

- nodeType属性

  nodeType 属性返回节点的类型。nodeType 是只读的。

  比较重要的节点类型有：

  | 元素类型 | NodeType |
  | :------- | :------- |
  | 元素     | 1        |
  | 属性     | 2        |
  | 文本     | 3        |
  | 注释     | 8        |
  | 文档     | 9        |



### 事件

- 事件源：引发后续事件的html标签。

- 事件：js已经定义好了（见下图）。

  ![img](https://camo.githubusercontent.com/8b9f269ab37f67948c8e00bceb556f4a270f1223/687474703a2f2f696d672e736d79687661652e636f6d2f32303138303132365f313535332e706e67)

- 事件驱动程序：对样式和html的操作。也就是DOM。

也就是说，我们可以在时间对应的属性中写一些js代码，当事件被触发时，这些代码将会执行。



**代码书写步骤如下：**（重要）

1. 获取事件源：document.getElementById(“box”); // 类似于Android里面的findViewById

2. 绑定事件： 事件源box.事件onclick = function(){ 事件驱动程序 };

3. 书写事件驱动程序：可以改变css的样式（关于DOM的操作）。

```
    <style>
        #box1 {
            width: 100px;
            height: 100px;
            background-color: pink;
            cursor: pointer;
        }
    </style>
</head>

<body>

<div id="box1" ></div>

<script type="text/javascript">
    var div1 = document.getElementById("box1");			// 获取事件源
    //点击鼠标时，原本粉色的div变大了，背景变红了			
    div1.onclick = function () {						// 绑定事件,函数内即驱动程序
        div1.style.width = "200px";   //属性值要写引号（可以更改css属性）
        div1.style.height = "200px";
        div1.style.backgroundColor = "red";   //属性名是backgroundColor，不是background-color
    }
</script>
```



特殊事件：

​		**当页面加载（文本和图片）完毕的时候，触发onload事件。**有一点我们要知道：**js的加载是和html同步加载的**。因此，如果使用元素在定义元素之前，容易报错。这个时候，onload事件就能派上用场了，我们可以把使用元素的代码放在onload里，就能保证这段代码是最后执行。

建议是：整个页面上所有元素加载完毕再执行js内容。所以，window.onload可以预防使用标签在定义标签之前。



### DOM操作

DOM各种操作（访问，修改，修改html内容等）都是使用上面的方法



## BOM

### 常见的 BOM 对象

> 下面的方法在浏览器的控制台也可以使用

BOM可以让我们通过JS来操作浏览器。BOM中为我们提供了一些对象，来完成对浏览器相关的操作。

常见的 BOM对象有：

- Window：代表整个浏览器的窗口，同时 window 也是网页中的全局对象。

- Navigator：代表当前浏览器的信息，通过该对象可以识别不同的浏览器。

  **一般我们只会使用`navigator.userAgent`来获取浏览器的信息**。

  ```
  var ua = navigator.userAgent; // 获取当前浏览器的 userAgent
  if (/firefox/i.test(ua)) {	//test()方法用于检测一个字符串是否匹配某个模式(一般是正则表达式)
  	alert('是火狐浏览器');
  } else if (/chrome/i.test(ua)) {
  	alert('是Chrome浏览器');
  } else if (/msie/i.test(ua)) {
  	alert('是IE浏览器');
  } else if ('ActiveXObject' in window) {
  	alert('是 IE11 浏览器');
  }
  ```

- Location：代表当前浏览器的地址栏信息，通过 Location 可以获取地址栏信息，或者操作浏览器跳转页面。

  - location对象的属性：

    - href

      ```
      location.href			// 获取当前的url
      location.href = 'https://xxx';		// 设置当前的url
      ```

  - location对象的方法：
    - `location.assign(str);` 用来跳转到其他的页面，作用和直接修改`location.href`一样。
    - `location.reload();` 用于重新加载当前页面，作用和刷新按钮一样。
    - `location.replace();` 使用一个新的页面替换当前页面，调用完毕也会跳转页面。但不会生成历史记录，不能使用「后退按钮」后退。

- History：代表浏览器的历史记录，通过该对象可以操作浏览器的历史记录。由于隐私原因，该对象不能获取到具体的历史记录，只能操作浏览器向前或向后翻页，而且该操作只在当次访问时有效。

  ```
  history.back(); 	//回退到上一个页面（后退按钮）
  history.forward();	//跳转到下一个页面（前进按钮）
  ```

  

- Screen：代表用户的屏幕信息，通过该对象可以获取用户的显示器的相关信息。

备注1：这些 BOM 对象都是作为 window 对象的属性保存的，可以通过window对象来使用，也可以直接使用。比如说，我可以使用 `window.location.href`，也可以直接使用 `location.href`，二者是等价的。

备注2：不要忘了，之前学习过的`document`也是在`window`中保存的。

### 定时器

- `setInterval()` 循环调用。将一段代码，**每隔一段时间**执行一次。（循环执行）

  ```
     let num = 1;
     setInterval(function () {
         num ++;
         console.log(num);
     }, 1000);
  ```

  假设定时器setInterval()的返回值是`参数1`，那么`clearInterval(参数1)`就可以清除定时器。

- `setTimeout()` 延时调用。将一段代码，等待一段时间之后**再执行**。（只执行一次）

  代码举例：

  ```
      const timer = setTimeout(function() {
          console.log(1); // 3秒之后，再执行这段代码。
      }, 3000);
  
      clearTimeout(timer);
  ```

  代码举例：（箭头函数写法）

  ```
      setTimeout(() => {
          console.log(1); // 3秒之后，再执行这段代码。
      }, 3000);
  ```

### 打开窗口和关闭窗口

```
window.open(url,target,param);
window.close();
```

代码举例：

```
<body>
<a href="javascript:;">点击我打开一个新的页面</a>
<a href="javascript:;">点击我关闭本页面</a>
<script>
    //新窗口 = window.open(地址,是否开新窗口,新窗口的各种参数);
    var a1 = document.getElementsByTagName("a")[0];
    var a2 = document.getElementsByTagName("a")[1];
    a1.onclick = function () {
//举例1： window.open("http://www.jx.com","_blank");
        var json = {
            "name": "helloworld",
            "fullscreen": "no",
            "location": "no",
            "width": "100px",
            "height": "100px",
            "top": "100px",
            "left": "100px"
        };
        window.open("http://www.baidu.com", "_blank", json); //举例2
    }

    //关闭本页面
    a2.onclick = function () {
        window.close();
    }
</script>
</body>
```

新窗口相关：

- 新窗口.moveTo(5,5)
- 新窗口.moveBy()
- 新窗口.resizeTo()
- window.resizeBy()

代码举例：

```hv
        var newWin = window.open("demo.html", "_blank", json);
        newWin.moveTo(500, 500);
```