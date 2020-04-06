# Node.js

Node.js 是一个基于 **Chrome V8** 引擎的 JavaScript 运行环境。 Node.js使用了一个**事件驱动**、**非阻塞式I/O**的模型（ Node.js的特性），使其轻量级又高效。 Node.js 的包管理器 npm 是全球最大的开源库生态系统。



# 模块化



模块化起源于 Node.js。Node.js 中把很多 js 打包成 package，需要的时候直接通过 require 的方式进行调用（CommonJS），这就是模块化的方式。

那如何把这种模块化思维应用到前端来呢？这就产生了两种伟大的 js：RequireJS 和 SeaJS



## 模块化规范

服务器端规范：

- [**CommonJS规范**](http://www.commonjs.org/)：是 Node.js 使用的模块化规范。

CommonJS 就是一套约定标准，不是技术。用于约定我们的代码应该是怎样的一种结构。

浏览器端规范：

- [**AMD规范**](https://github.com/amdjs/amdjs-api)：是 **[RequireJS](http://requirejs.org/)** 在推广过程中对模块化定义的规范化产出。

  - 异步加载模块；

  - 依赖前置、提前执行：require([`foo`,`bar`],function(foo,bar){});   //也就是说把所有的包都 require 成功，再继续执行代码。

  - define 定义模块：define([`require`,`foo`],function(){return});

- **[CMD规范](https://github.com/qianguyihao/Web/blob/master/11-Node.js和模块化)**：是 **[SeaJS](http://seajs.org/)** 在推广过程中对模块化定义的规范化产出。淘宝团队开发。

  - 同步加载模块；

  - 依赖就近，延迟执行：require(./a) 直接引入。或者Require.async 异步引入。   //依赖就近：执行到这一部分的时候，再去加载对应的文件。

  - define 定义模块， export 导出：define(function(require, export, module){});

- ES6规范

> 面试时，经常会问AMD 和 CMD 的区别。



