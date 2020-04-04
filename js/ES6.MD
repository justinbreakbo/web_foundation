# ES6

ECMAScript 是 JS 的语言标准。而 ES6 是新的 JS 语法标准。

很多人在做业务选型的时候，会倾向于选jQuery。其实jQuery的语法是偏向于ES3的。而现在主流的框架 Vue.js 和React.js的语法，是用的ES6。

ES6中增加了很多功能上的不足。比如：**常量、作用域、对象代理、异步处理、类、继承**等。这些在ES5中想实现，比较复杂，但是ES6对它们进行了封装。

但是浏览器对es6的语法支持不是很好，运行在浏览器的时候需要把es6转成es5，NodeJS平台是可以支持绝大部分的ES6的新内容。



## ES的几个重要版本

- ES5 : 09年发布。
- ES6(ES2015) : 2015年发布，也称为ECMA2015。
- ES7(ES2016) : 2016年发布，也称为ECMA2016 (变化不大)。

## ES5的严格模式

**理解**：除了正常运行模式(混杂模式)，ES5添加了第二种运行模式："严格模式"（strict mode）。

顾名思义，这种模式使得Javascript在更严格的语法条件下运行。

**目的**：

- 消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为
- 消除代码运行的一些不安全之处，为代码的安全运行保驾护航
- 为未来新版本的Javascript做好铺垫



## ES6的变量声明

ES6 中新增了 let 和 const 来定义变量：

- `var`：ES5 和 ES6中，定义**全局变量**（是variable的简写）。

- `let`：定义**局部变量**，替代 var。

- `const`：定义**常量**（定义后，不可修改）。

  用 const 声明的变量，只在局部（块级作用域内）起作用。

**总结：我们要习惯用 let 声明，减少var声明带来的污染全局空间**。

为了进一步说明 let 不会带来污染，需要说明的是：当我们定义了`let a = 1`时，如果我们在同一个作用域内继续定义`let a = 2`，是会报错的。



## 变量的解构赋值

ES6允许我们，通过数组或者对象的方式，对一组变量进行赋值，这被称为解构。

解构赋值在实际开发中可以大量减少我们的代码量，并且让程序结构更清晰。

### 数组的解构赋值

**举例：**

通常情况下，我们在为一组变量赋值时，一般是这样写：

```
	let a = 0;
	let b = 1;
	let c = 2;
```

现在我们可以通过数组解构的方式进行赋值：

```
	let [a, b, c] = [1, 2, 3];
```

二者的效果是一样的。



> - undefined：相当于什么都没有。
> - null：相当于有值，但值为 null。



### 对象的解构赋值

通常情况下，我们从接口拿到json数据后，一般这么赋值：

```
var a = json.a;

var b = json.b;

bar c = json.c;
```

上面这样写，过于麻烦了。

现在，我们同样可以针对对象，进行结构赋值。

**举例如下：**

```
	let { foo, bar } = { bar: '我是 bar 的值', foo: '我是 foo 的值' };
	console.log(foo + ',' + bar); //输出结果：我是键 foo 的值,我是键 bar 的值
```

上方代码可以看出，对象的解构与数组的结构，有一个重要的区别：**数组**的元素是按次序排列的，变量的取值由它的**位置**决定；而**对象的属性没有次序**，是**根据键来取值**的。

> **圆括号的使用**：
>
> 如果变量 foo 在解构之前就已经定义了，此时你再去解构，就会出现问题，编译会报错。要解决报错，只要在解构的语句外边，加一个圆括号即可：



### 字符串解构

字符串也可以解构，这是因为，此时字符串被转换成了一个类似**数组**的对象。举例如下：

```
const [a, b, c, d] = 'smyhvae';
console.log(a);		//s
console.log(b);		//m
console.log(c);		//y
console.log(d);		//h

console.log(typeof a);  //输出结果：string
```



## for ... of 循环

ES6 中，如果我们要遍历一个数组（或Map），可以这样做：（增加代码运行效率，建议使用）

```
let arr1 = [1, 2, 3, 4, 5];

for (let value of arr1) {
	console.log(value);
}
```

`for ... of`获取的是数组里的值；`for ... in`获取的是index索引值。



## 模板字符串

现在有了 ES6 语法，字符串拼接可以这样写：

```
    var name = 'smyhvae';
    var age = '26';

    console.log('name:'+name+',age:'+age);   //传统写法

    console.log(`name:${name},age:${age}`);  //ES6 写法
```

**注意**，上方代码中，倒数第二行用的符号是单引号，最后一行用的符号是反引号（在tab键的上方）。



## 箭头函数

定义和调用函数：（传统写法）

```
function fn1(a, b) {
    return a + b;
}
```

定义和调用函数：（ES6中的写法）

```
	var fn2 = (a, b) => a + b;	//函数体只有一句返回值可以直接写返回值，不写return

	var fn2 = (a, b) => {
	    console.log('haha');
	    return a + b;
	};							// 函数体不止一句，就需要加花括号
```



> ES5 中，this指向的是函数被调用的对象；而 ES6 的箭头函数中，this指向的是函数被定义时。
>
> **简单来说，ES6箭头函数中的this，是不会变的，是永远绑定在当前的环境下。**





## 参数默认值

ES6可以设置参数的默认值，如下：

如果调用时不传入参数，就使用'hello'默认值（设置默认值的参数要放在最后面）：

```
    function fn(param1, param2 = 'hello') {
        console.log(param1,param2);
    }
```



## 扩展运算符和rest运算符

有了ES6，当我们在定义一个方法，但是不确定其参数的个数时，我们就可以用**扩展运算符**作为参数。

注意区分：

- 扩展运算符的格式为`...`

  使用了扩展运算符的参数，不能再加别的参数

- rest运算符的格式为`...变量名`

  rest运算符的参数是和别的参数一起配合使用的，表示“剩余的参数”

### 扩展运算符

```
function fn(...arg) {   //当不确定方法的参数时，可以使用扩展运算符
    console.log(arg[0]);
    console.log(arg[1]);
    console.log(arg[2]);
    console.log(arg[3]);
}

fn(1, 2, 3); //方法中定义了四个参数，但只引用了三个参数，ES6 中并不会报错。
```

上方代码中注意，arg参数之后，不能再加别的参数，否则编译报错。



另外，数组赋值时：`let arr2 = arr1;`其实是让 arr2 指向 arr1 的地址。也就是说，二者指向的是同一个内存地址。这时候改变arr1，arr2也会改变。如果不想让 arr1 和 arr2 指向同一个内存地址，我们可以借助扩展运算符来做：

```
let arr1 = ['www', 'smyhvae', 'com'];
let arr2 = [...arr1];  //arr2 会重新开辟内存地址
console.log('arr1:' + arr1);
console.log('arr2:' + arr2);
console.log('---------------------');

arr2.push('你懂得');  //往arr2 里添加一部分内容
console.log('arr1:' + arr1);
console.log('arr2:' + arr2);
```

### rest运算符

`rest` 在英文中指的是**剩余部分**（不是指休息）。我们来举个例子，理解剩余部分的含义：

```
	function fn(first, second, ...arg) {
	    console.log(arg.length);
	}

	fn(0, 1, 2, 3, 4, 5, 6);  //调用函数后，输出结果为 5
```

上方代码的输出结果为 5。 调用`fn()`时，里面有七个参数，而`arg`指的是剩下的部分（因为除去了`first`和`second`）。

从上方例子中可以看出，`rest`运算符适用于：知道前面的一部分参数的数量，但对于后面剩余的参数数量未知的情况。



## 字符串的扩展

ES6中的字符串扩展，用得少，而且逻辑相对简单。如下：

- `includes(str)`：判断是否包含指定的字符串
- `startsWith(str)`：判断是否以指定字符串开头
- `endsWith(str)`：判断是否以指定字符串结尾
- `repeat(count)`：重复指定次数



## Number 的扩展

- 二进制与八进制数值表示法: 二进制用`0b`, 八进制用`0o`。

举例：

```
    console.log(0b1010);//10
    console.log(0o56);//46
```

- `Number.isFinite(i)`：判断是否为有限大的数。比如`Infinity`这种无穷大的数，返回的就是false。
- `Number.isNaN(i)`：判断是否为NaN。
- `Number.isInteger(i)`：判断是否为整数。
- `Number.parseInt(str)`：将字符串转换为对应的数值。
- `Math.trunc(i)`：去除小数部分。



## 数组的扩展

> 下面提到的数组的几个方法，更详细的内容，可以看《04-JavaScript基础/17-数组的常见方法.md》。

### 扩展1：Array.from()

```
	Array.from(伪数组/可遍历的对象)
```

**作用**：将**伪数组**或可遍历对象转换为**真数组**。

### 扩展2：Array.of()

```
	Array.of(value1, value2, value3)
```

**作用**：将一系列值转换成数组。

### 扩展3：find() 和 findIndex()

**方法1**：

```
	find(function(item, index, arr){return true})
```

**作用**：找出**第一个**满足「指定条件返回true」的元素。

**方法2**：

```
	findIndex(function(item, index, arr){return true})
```

**作用**：找出第一个满足「指定条件返回true」的元素的index。

## 对象的扩展

### 扩展1

```
	Object.is(v1, v2)
```

**作用：\**判断两个数据是否完全相等。底层是通过\**字符串**来判断的。

我们先来看下面这两行代码的打印结果：

```
        console.log(0 == -0);
        console.log(NaN == NaN);
```

打印结果：

```
	true
	false
```

上方代码中，第一行代码的打印结果为true，这个很好理解。第二行代码的打印结果为false，因为NaN和任何值都不相等。

但是，如果换成下面这种方式来比较：

```
        console.log(Object.is(0, -0));
        console.log(Object.is(NaN, NaN));
```

打印结果却是：

```
	false
	true
```

代码解释：还是刚刚说的那样，`Object.is(v1, v2)`比较的是字符串是否相等。

### 扩展2（重要）

```
	Object.assign(目标对象, 源对象1, 源对象2...)
```

**作用：** 将源对象的属性追加到目标对象上。如果对象里属性名相同，会被覆盖。

其实可以理解成：将多个对象**合并**为一个新的对象。

举例：

```
        let obj1 = { name: 'smyhvae', age: 26 };
        let obj2 = { city: 'shenzhen' };
        let obj3 = {};

        Object.assign(obj3, obj1, obj2);
        console.log(obj3);
```

打印结果：

[![img](https://camo.githubusercontent.com/255f58b3801325cfae5977e9673b3a05c05b9c3d/687474703a2f2f696d672e736d79687661652e636f6d2f32303138303430345f323234302e706e67)](https://camo.githubusercontent.com/255f58b3801325cfae5977e9673b3a05c05b9c3d/687474703a2f2f696d672e736d79687661652e636f6d2f32303138303430345f323234302e706e67)

上图显示，成功将obj1和obj2的属性复制给了obj3。

### 扩展3：`__proto__`属性

举例：

```
       let obj1 = {name:'smyhvae'};
       let obj2 = {};

       obj2.__proto__ = obj1;

       console.log(obj1);
       console.log(obj2);
       console.log(obj2.name);
```

打印结果：

[![img](https://camo.githubusercontent.com/403b5cc49c18b988156519a3c3785900a184758b/687474703a2f2f696d672e736d79687661652e636f6d2f32303138303430345f323235312e706e67)](https://camo.githubusercontent.com/403b5cc49c18b988156519a3c3785900a184758b/687474703a2f2f696d672e736d79687661652e636f6d2f32303138303430345f323235312e706e67)

上方代码中，obj2本身是没有属性的，但是通过`__proto__`属性和obj1产生关联，于是就可以获得obj1里的属性。



## Promise

### 概述

Promise对象: 代表了未来某个将要发生的事件(通常是一个异步操作)。

ES6中的promise对象, 可以**将异步操作以同步的流程表达出来，很好地解决了回调地狱**的问题（避免了层层嵌套的回调函数）。在使用ES5的时候，在多层嵌套回调时，写完的代码层次过多，很难进行维护和二次开发。

### promise对象的3个状态

- 初始化状态（等待状态）：pending
- 成功状态：fullfilled
- 失败状态：rejected

### 使用promise的基本步骤

（1）创建promise对象

（2）调用promise的**回调函数**then()

## Symbol

### 概述

背景：ES5中对象的属性名都是字符串，容易造成重名，污染环境。

**概念**：ES6 引入了一种新的原始数据类型Symbol，表示独一无二的值。它是 JavaScript 语言的第七种数据类型，前六种是：undefined、null、布尔值（Boolean）、字符串（String）、数值（Number）、对象（Object）。

**特点：**

- Symbol属性对应的值是唯一的，解决**命名冲突问题**
- Symbol值不能与其他数据进行计算，包括同字符串拼串
- for in、for of 遍历时不会遍历Symbol属性。

### 创建Symbol属性值

Symbol是函数，但并不是构造函数。创建一个Symbol数据类型：

```
    let mySymbol = Symbol();

    console.log(typeof mySymbol);  //打印结果：symbol
    console.log(mySymbol);         //打印结果：Symbol()
```





## async函数（异步函数）

### 概述

> async 函数是在 ES2017 引入的。

概念：真正意义上去解决异步回调的问题，同步流程表达异步操作。

本质： Generator 的语法糖。

async比之前的 Promise、Generator要好用一些。

语法：

```
    async function foo() {
        await 异步操作;
        await 异步操作；
    }
```

我们在普通的函数前面加上 async 关键字，就成了 async 函数。

### async、Promise、Generator的对比（async的特点）

1、不需要像Generator去调用next方法，遇到await等待，当前的异步操作完成就往下执行。

2、async返回的总是Promise对象，可以用then方法进行下一步操作。

3、async取代Generator函数的星号*，await取代Generator的yield。

4、语意上更为明确，使用简单，经临床验证，暂时没有任何副作用。





