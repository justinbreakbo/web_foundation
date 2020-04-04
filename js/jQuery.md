# jQuery

jQuery 是 js 的一个库，封装了我们开发过程中常用的一些功能，方便我们调用，提高开发效率。

js库是把我们常用的功能放到一个单独的文件中，我们用的时候，直接引用到页面里即可。

以下是jQuery的相关信息：

- 官网：http://jquery.com/
- 官网API文档：http://api.jquery.com/
- 中文汉化API文档：http://www.css88.com/jqapi-1.9/



**angular操作DOM：**

　　通过elementRef或者@viewChild @viewChildren获取元素，再通过renderer2提供的API来操作元素。不过记得在不要在 ngAfterViewInit 周期之前使用。通过Angular提供的方式，可以满足大部分的操作DOM的需求了。如果有特殊的场景，当然还是原生DOM撸起来。

