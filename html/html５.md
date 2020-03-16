# HTML5

> HTML5并不仅仅只是做为HTML标记语言的一个最新版本，更重要的是它**制定了Web应用开发的一系列标准**，成为第一个将Web做为应用开发平台的HTML语言。
>
> HTML5定义了一系列新元素，如新语义标签、智能表单、多媒体标签等，可以帮助开发者创建富互联网应用，还提供了一些 Javascript API，如地理定位、重力感应、硬件访问等，可以在浏览器内实现类原生应用。我们甚至可以结合 Canvas 开发网页版游戏。



## HTML5新增语义标签

- `<section>` 表示区块
- `<article>` 表示文章。如文章、评论、帖子、博客
- `<header>` 表示页眉
- `<footer>` 表示页脚
- `<nav>` 表示导航
- `<aside>` 表示侧边栏。如文章的侧栏
- `<figure>` 表示媒介内容分组。
- `<mark>` 表示标记 (用得少)
- `<progress>` 表示进度 (用得少)
- `<time>` 表示日期



## HTML5表单

### HTML5新增的表单类型

- `email` 只能输入email格式。自动带有验证功能。
- `tel` 手机号码。
- `url` 只能输入url格式。
- `number` 只能输入数字。
- `search` 搜索框
- `range` 滑动条
- `color` 拾色器
- `time` 时间
- `date` 日期
- `datetime` 时间日期
- `month` 月份
- `week` 星期

上面的部分类型是针对移动设备生效的，且具有一定的兼容性，在实际应用当中可选择性的使用。

### 表单元素

- `<datalist>` 数据列表

  ```html
  <input type="text" list="myData">
  <datalist id="myData">
      <option>本科</option>
      <option>研究生</option>
      <option>不明</option>
  </datalist>
  ```

  上方代码中，input里的list属性和 datalist 进行了绑定, 可以在输入的时候提示数据列表的内容

- `<keygen>` 元素

  keygen 元素的作用是提供一种验证用户的可靠方法。

  keygen 元素是密钥对生成器（key-pair generator）。当提交表单时，会生成两个键：一个公钥，一个私钥。

  私钥（private key）存储于客户端，公钥（public key）则被发送到服务器。公钥可用于之后验证用户的客户端证书（client certificate）。

### 表单属性

- `placeholder` 占位符（提示文字）
- `autofocus` 自动获取焦点
- `multiple` 文件上传多选或多个邮箱地址
- `autocomplete` 自动完成（填充的）。on 开启（默认），off 取消。用于表单元素，也可用于表单自身(on/off)
- `form` 指定表单项属于哪个form，处理复杂表单时会需要
- `novalidate` 关闭默认的验证功能（只能加给form）
- `required` 表示必填项
- `pattern` 自定义正则，验证表单。例如

### 表单事件

- `oninput()`：用户输入内容时触发，可用于输入字数统计。
- `oninvalid()`：验证不通过时触发。比如，如果验证不通过时，想弹出一段提示文字，就可以用到它。



## 多媒体

在HTML5之前，在网页上播放音频/视频的通用方法是利用Flash来播放。但是大多情况下，并非所有用户的浏览器都安装了Flash插件，由此使得音频、视频播放的处理变得非常复杂；并且移动设备的浏览器并不支持Flash插件。

H5里面提供了视频和音频的标签。

### 音频

- `<audio>` 音频播放 



我们可以通过附加属性，来更友好地控制音频的播放，如：

- `autoplay` 自动播放。写成`autoplay` 或者 `autoplay = ""`，都可以。
- `controls` 控制条。（建议把这个选项写上，不然都看不到控件在哪里）
- `loop` 循环播放。
- `preload` 预加载 同时设置 autoplay 时，此属性将失效。



由于版权等原因，不同的浏览器可支持播放的格式是不一样的：

![image-20200316114133378](/home/just/.config/Typora/typora-user-images/image-20200316114133378.png)

为了做到多浏览器支持，可以采取以下兼容性写法：(如果识别不出音频格式，就弹出那句“抱歉”)

```html
<!--推荐的兼容写法：-->
<audio controls loop>
    <source src="music/yinyue.mp3"/>
    <source src="music/yinyue.ogg"/>
    <source src="music/yinyue.wav"/>
    抱歉，你的浏览器暂不支持此音频格式
</audio>
```



### 视频

- `<video>` 视频播放



我们可以通过附加属性，来更友好地控制视频的播放，如：

- `autoplay` 自动播放。写成`autoplay` 或者 `autoplay = ""`，都可以。
- `controls` 控制条。（建议把这个选项写上，不然都看不到控件在哪里）
- `loop` 循环播放。
- `preload` 预加载 同时设置 autoplay 时，此属性将失效。
- `width`：设置播放窗口宽度。
- `height`：设置播放窗口的高度。



由于版权等原因，不同的浏览器可支持播放的格式是不一样的：

![img](https://camo.githubusercontent.com/2ff8793bbda3c4982e35833618b3d42d4ba38081/687474703a2f2f696d672e736d79687661652e636f6d2f32303138303230365f323032352e706e67)

兼容性写法：

```html
    <!--<video src="video/movie.mp4" controls  autoplay ></video>-->
    <!--  行内块 display:inline-block -->
    <video controls autoplay>
        <source src="video/movie.mp4"/>
        <source src="video/movie.ogg"/>
        <source src="video/movie.webm"/>
        抱歉，不支持此视频
    </video>
```





## DOM操作

### 获取元素

- document.querySelector("selector") 通过CSS选择器获取符合条件的第一个元素。
- document.querySelectorAll("selector") 通过CSS选择器获取符合条件的所有元素，以类数组形式存在。

### 类名操作

- Node.classList.add("class") 添加class
- Node.classList.remove("class") 移除class
- Node.classList.toggle("class") 切换class，有则移除，无则添加
- Node.classList.contains("class") 检测是否存在class

### 自定义属性

js 里可以通过 `box1.index=100;` `box1.title` 来自定义属性和获取属性。

H5可以直接在标签里添加自定义属性，**但必须以 `data-` 开头**。





其他详细内容见[原网页](https://github.com/qianguyihao/Web/tree/master/01-html)