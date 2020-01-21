# 前端发展简史

## web1.0时代——静态网页

- 1989年，伯纳斯·李（Tim Berners-Lee）提出web原型：个人计算机上访问大量的科研文献，并建议在文档中链接其他文档，此举被认为是web原型。他也被认为是前端之父。
- 1994年，前端历史的起点
  - W3C成立
  - 网景公司推出第一款浏览器——Navigator浏览器
  - html发布第二代版本
  - 伯纳斯·李的好基友设计了CSS

- 1995年，网景工程师Brendan Eic花10天时间设计了JS。
- 1996年微软页发布了JScript(和JS有差异)，同时拉开了Navigator与IE（Internet Explorer）的大战。2002年，ie完胜，占据市场96%的份额。（Windos）
- 1996年6月，ECMA（欧洲计算机制造联合会）以JS语法制定ECMAScript标准规范ECMA-262，浏览器厂商开始按照规范来开发自己的浏览器产品。
- 1999年12月，ES3发布，2011年6月ES5发布（2007年ES4夭折，改动太大），ES3占据了10年历程，也是JS语言的基础。2015年6月ES6发布（由于之后规定每年发布一个新版本，所以更名未ES2015），2016年6月对2015年版本增强的2016版本发布，此后ES2017、ES2018相继发布...
- 2014年10月，HTML发布第五代版本，俗称H5，2011年CSS发布第三代版本，此后前端的技术栈就稳固下来了。

## web2.0时代——动态网页

服务器渲染时代：轻前端重后台

```
前端：
	1.写页面和样式
后端：
	1.会写数据绑定代码
	2.操作数据库
	3.操作服务器
	4.数据结构和算法
	5.服务器分布式（缓存和并发）
	......
```

1995年之前，JS只用来做一些简单的DOM修改，WEB页面都是静态的（显示静态文本和图片）。为了让WEB页面更具备活力（例如：动态展示数据）：

- 1995年PHP诞生，
- 1996年JSP诞生，
- 1996年ASP诞生，
- 2002年ASP.NET诞生
- ...


这些服务器端页面技术实现了WEB页面的动态化，从此WEB2.0时代到来。

缺点：

- 同步非异步刷新    
- 服务器承受压力过大
- 后台开发的任务量过大（网页制作任务量少），代码过于臃肿，两种角色很难实现同时任务开发
- 页面中某个数据想要更改，只能重新刷新整个页面（全局刷新）
- 不利于团队协作开发
- ......

客户端渲染

- 减轻服务器压力
- 页面的局部刷新
- 配合方便，实现前后端分离，同时开发

### 前端干的活

```
1.写页面（HTML5/CSS3）
2.写交互（JS）
3.数据请求和绑定（AJAX）
4.操作系统 Linux
5.HTTP和CP网络的知识
```

### 后台干的活

```
1.业务逻辑处理
2.数据处理，数据库操作
3.数据结构和算法（服务器负载）
4.操作系统
5.HTTP和CP网络的知识
```

### AJAX时代

***前后端分离的雏形，异步渲染大显神通***

​		在Web最初发展的阶段，前端页面要想获取后台信息需要刷新整个页面，这是很糟糕的用户体验。Google分别在2004年和2005年先后发布了两款重量级的Web产品：Gmail和Google Map。这两款Web产品都大量使用了AJAX技术，不需要刷新页面就可以使得前端与服务器进行网络通信，所以AJAX是一项革命性的技术，颠覆了用户体验。到2013年/2014年，随着移动端H5的崛起，高性能的WEB体验是重中之重，国内大部分项目都已经改为“前后端分离”模式，这也奠定了前端开发二分天下的局面。导致到后期，跨域策略请求方案（JSONP、IFRAME、CORS、DOMAIN、POXY、SCOKET...）以及FETCH等新通信方案不断的崛起。

### 前端开发者之殇

***浏览器兼容***

​		IE在第一次浏览器大战中击败Netscape赢得胜利，垄断了浏览器市场。作为独裁者，IE并不遵循W3C的标准，IE成了事实标准。2004年11月Firefox发布，之后一路奋起直追，逐渐蚕食IE市场份额，这引发了第二次浏览器战争。2008年12月Chrome浏览器发布，也加入了浏览器大战，由于其优越的处理性能（webkit内核/V8引擎），到2016年，谷歌占据了浏览器市场的半壁江山。
​       但是浏览器越多，碎片化问题也越来越严重，不同的浏览器执行不同的标准，对于开发人员来说这是一个恶梦。为了解决浏览器兼容性问题，Dojo、jQuery、YUI、ExtJS、等前端类库相继诞生。（jQuery独领风骚，几乎成了所有网站的标配，Dojo、YUI、ExtJS等提供了很多组件，让复杂的业务简单化...）。

## H5崛起

***Hybrid混合开发成为主导***

​		自2009年起，随着iOS和Android等智能手机的广泛使用，移动浏览器也逐步加强了对HTML5特性的支持力度。相比于Native App，移动Web开发成本低、跨平台、发布周期短的优势愈发明显，但是Native App的性能和UI体验要远胜于移动Web（Hybrid技术是结合两者优势），截止目前，市面上95%以上的APP都是Hybrid混合APP开发的。根据实现原理，Hybrid技术可以分为两大类：

- 将HTML5的代码放到Native App的WebView控件中运行，典型代表有PhoneGap(Cordova)以及AppCan、Ionic等（微信二次开发）。 
- 将HTML5代码针对不同平台编译成不同的原生应用，实现了Web开发，Native部署。这一类的典型代表有React Native  / Flutter / uni-app。

***原生app***

- 优势
  - 性能好
  - 功能强大（可以调用手机软件硬件）
- 缺点
  - 不能跨平台
    - 成本大
  - 不能同步
    - 功能上线不同步

***Web App***

H5页面  =>  响应式布局开发

***H5优势***

1. 跨平台
2. 及时更新

***H5缺点***

1. 性能相对不好
2. 功能不强大

***目前手机APP开发（99.99999%）选择Hybrid混合APP开发***

概念：

```
webview			(webkit内核，就是浏览器内核)
JSBridge		JS调用原生APP的活儿
// 原生APP的盒子
React-Native	
Flutter
uni-app			HBuder发布的框架
```

## NODE崛起

***JS成为最热门全栈开发技术***

- 2009年，Ryan利用Chrome的V8引擎打造了基于事件循环的异步I/O框架-Node.js诞生。
- NODE特点：基于事件循环的异步I/O框架，能够提高I/O吞吐量；单线程运行，能够避免了多线程变量同步的问题；使得JS可以编写后台代码，前后端编程语言统一。
- 2010年1月，NPM作为Node.js的包管理系统首次发布。前NPM具有40万左右的模块，是世界上最大的包模块管理系统。

## 前端未来发展预估

- 小程序是企业产品的重要组成部分
- IOS和安卓开发逐步被淘汰
- VR/AI最终转为B端（JS，尤其是webGL、canvas、three.js等是3D虚拟交互的主要实现技术）    
- H5游戏/小游戏的热度会提高（白鹭JS引擎）
- NODE.JS还会迎来下一个高潮

## 前端技术栈

### 第一阶段：HTML（5） + CSS（3）

​       ***技术要点***

- HTML5
- CSS3
- 响应式布局（rem/flex/@media等）
- Hybrid混合APP开发
- 微信二次开发
- 小程序开发
- React Native开发、Flutter、uni-app...
         特殊说明：Hybrid、微信开发、小程序开发、React Native开发等，这些都需要有JS和框架编程的基础；H5不仅仅是标签，还需要掌握常用的API以及video和audio等，例如：localstorage、webscoket、getCurrentPosition等。

### 第二阶段：JS包括ES6核心原理

​       JS堆栈内存、闭包作用域、浏览器词法解析（v8渲染机制原理）、面向对象和THIS处理（主要是独立封装组件和插件，研究常用类库的源码）； 
​       ES6基础语法（包括class类的继承封装和多态）、ES6中的Promise（及Promise A+规范）、Generator生成器函数等深入用法；
​       同步异步编程（包括运行机制和微任务、宏任务，以及实战应用）
​       常用的编程思想和设计模式：函数的防抖和节流、柯理化函数、惰性函数、单例设计模式、发布订阅模式、Promise设计模式等
​       DOM性能优化（重排和重绘的优化）、DOM事件
​       前端编程常规算法：去重、冒泡排序、插入排序、快速排序、递归等    

### 第三阶段：AJAX和HTTP

​      ***技术要点***

- ajax原理、ajax异步解决方案（promise）
- axios（包括自己封装promise版ajax库）
- fetch及封装处理
- jquery中的ajax操作和库的封装等
           跨域解决方案及实现原理：jsonp、cors、webpack proxy（scoket.io）、document.domain、window.name+iframe、postMessage等
          HTTP报文（常用的响应请求头实战应用技巧）、HTTP（TCP）传输流程（包括三次握手四次挥手及TCP底层协议）、HTTP1和HTTP2的区别、HTTP和HTTPS的区别等
         特殊说明：HTTP是目前优秀公司重点考察的知识点，因为传统前端代码优化，性能上提高较小，HTTP相关优化手段是性能提高的重要方法（例如：304缓存、DNS缓存、减少HTTP传输次数和大小、HTTPS的加密等），这块是一个重点！    

### 第四阶段：框架开发

​       技术要点：目前市场上的项目大部分都是框架开发的，所以框架学习非常的重要，目前主流框架是 vue、react、angular，angular现在用的越来越少，一般都是老项目使用这个技术在维护（angular1.0版本居多）。
​       vue全家桶：vue（MVVM实现的原理以及一些语法实现的原理）、vue-router(HASH路由实现的原理)、vuex（掌握原理）、axios、vue-cli（需要能够修改脚手架的webpack配置项）、iview/vux/vue element等常用框架的使用等。
​       react全家桶：create-react-app（能够修改webpack的配置项）、react（掌握虚拟DOM渲染原理，掌握DOM-DIFF原理，掌握INDEX索引对比机制，掌握MVC实现的原理）、react-dom/react-native、react-router、react-redux/dva/mobx（掌握原理，自己可以基于原生JS写一套类似的插件、发现里面的一些不足点）、antd（最好可以自己封装一些基础的组件）等。

### 第五阶段：辅助技能

​       技术要点

- Webpack：掌握常用的脚手架使用和修改，会一些基础的webpack搭建。
- Git：熟练掌握团队协作开发中代码版本管控技巧，熟悉常用的操作命令。
- Node：掌握基础的API、掌握express/koa/egg等框架、可以编写伪API，可以基于node做跨域处理等，有精力的同学可以研究一下数据库操作等。
- Canvas：一些公司要求会可视化，需要掌握canvas/webGl/d3等，这个对于数学结构、算法等有一定的要求；这方面不好的，可以先掌握一些基础的操作，掌握echarts的用法等。   

### 常见的技术论坛

```
	   掘金：https://juejin.im/
       简书：https://www.jianshu.com/
       https://segmentfault.com/
       https://stackoverflow.com/
       https://github.com/
       https://developer.mozilla.org/zh-CN/
       百度FEX：http://fex.baidu.com/
	   淘宝FED：http://taobaofed.org/
	   腾讯：http://alloyteam.com/
	   360奇舞团：https://75team.com/
	   凹凸实验室：https://aotu.io/
```

### 找工作

2013年：我是做前端的，我能写页面。

2014年：我JQuery比较熟。

2015年：我原生JS掌握的不错

2016年：我能做Hybrid混合开发。

2017年：我vue或react会。

2018年：我vue或react会，原生JS设计模式、常用原理掌握的很清楚。

2019年~...：掌握底层原理，掌握项目实战，掌握框架、组件的封装。

------

***没有捷径、技术为王***

------

### 推荐学习方法

1. 笔记+复习
2. 深挖底层原理
3. 学而思
4. 实战：薪资和你敲过的代码成正比
5. 多读书：与技术无关

# 前端IDE

 ***Integrated Development Environment  集成开发环境***

- sublime text 
- Hbuilderx
- webstorm
- Visual Studio Code

### 推荐IDE-VScode

​		***微软唯一的良心产品***

#### 安装

官网：https://code.visualstudio.com

***一路下一步，遇框全选***。

特点：

```
永久免费
支持30多种编程语言
强大的代码提示和其它功能（debug/git等）
丰富的插件库   
轻量级    
```

#### 推荐添加插件

```
1. Chinese	汉化插件（英文原版对英语提高有帮助）
2. open in borwser	关联浏览器插件
3. Beautify（shift + alt + f）	代码格式化插件
4. Live Server	实时显示效果插件
......
```

# 浏览器内核和控制台

## 常用浏览器

* 谷歌浏览器（推荐）
* 火狐浏览器（推荐）
* 欧朋浏览器
* IE浏览器（6，7，8，9-11）
* QQ浏览器
* 百度
* 360
* UC
* 搜狗
* 猎豹
* 好123
* 2345
* ......

## 按照内核来分

- **webkit内核**（v8引擎）
    + 谷歌Chrome
    + Safari
    + Opera >= V14
    + 国产浏览器
    + 手机浏览器
- **Gecko**
    + 火狐Firefox
- Presto
    + Opera < V14
- **Trident**
	+ IE
	+ IE EDGE开始采用双内核（其中包含chrome迷你）

浏览器二战：**火狐、欧朋 + IE**平分天下
浏览器三战：**webkit内核浏览器**一家独大

## 谷歌浏览器的控制台
快捷键：**（F12/Fn+F12）/右键 -> 检查**

### 开发者工具
Elements / Console / Network / Sources / Application
**优秀前端职业病:打开网页按F12**

1. Elements：查看结构样式，可以修改这些内容
2. Console：查看输出结果和报错信息，是JS调试的利器
	- 临时调试器
3. Sources：查看项目源码
4. Network：查看当前网站所有资源的请求信息（包括和服务器传输的HTTP报文信息）、加载时间等（根据加载时间进行项目优化）
5. Application：查看当前网站的数据存储和资源文件（可以盗图）








