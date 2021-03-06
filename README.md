# Node.js入门到企业Web开发中的应用

Node.js 各种语法 入门讲解

从零开始掌握大型互联网公司NodeJS实际使用

[【视频地址】慕课网 Node.js入门到企业Web开发中的应用](https://coding.imooc.com/class/chapter/146.html#Anchor)

课程出品时间：2017年11月

看视频整理要点笔记：

----

**目录**
- [第1章 导学](#第1章-导学)
- [第2章 NodeJS 是什么，为什么偏爱NodeJS ?](#第2章-nodejs-是什么为什么偏爱nodejs-)
    - [2-1 NodeJS 是什么？](#2-1-nodejs-是什么)
    - [2-2 NodeJS 究竟好在哪里？](#2-2-nodejs-究竟好在哪里)
- [第3章 环境 & 调试](#第3章-环境--调试)
    - [3-1 CommonJS1](#3-1-commonjs1)
    - [3-2 CommonJS2](#3-2-commonjs2)
    - [3-4 引用系统内置模块 & 引用第三方模块](#3-4-引用系统内置模块--引用第三方模块)
    - [3-5 module.exports 与 exports 的区别](#3-5-moduleexports-与-exports-的区别)
    - [3-6 global变量](#3-6-global变量)
    - [3-7 process进程](#3-7-process进程)
    - [3-8 debug 调试](#3-8-debug-调试)
- [第4章 NodeJS 基础 API](#第4章-nodejs-基础-api)
    - [4-1 path 路径](#4-1-path-路径)
    - [4-3 Buffer](#4-3-buffer)
    - [4-6 Event 事件](#4-6-event-事件)
    - [4-8 fs 文件系统](#4-8-fs-文件系统)
- [第5章 项目初始化](#第5章-项目初始化)
    - [5-1 .gitignore .npmignore .EditorConfig](#5-1-gitignore)
    - [5-2 ESLint](#5-2-eslint)
- [第6章 静态资源服务器](#第6章-静态资源服务器)
    - [6-1 静态资源服务器 01](#6-1-静态资源服务器-01)
    - [6-2 使用 supervisor 监听目录，如果文件有变化 则自动重启服务器](#6-2-使用-supervisor-监听目录，如果文件有变化-则自动重启服务器)
    - [6-3 实现 静态资源服务器](#6-3-实现-静态资源服务器)
    - [6-4 promisify 化 静态资源服务器](#6-4-promisify-化-静态资源服务器)
    - [6-5 使用 HTML模板 生成动态网页](#6-5-使用-HTML模板-生成动态网页)
    - [6-7 自动传递 Content-Type && 根据不同文件类型显示不同icon](#6-7-自动传递-Content-Type-&&-根据不同文件类型显示不同icon)
    - [6-8 服务器 压缩文件 Content-Encoding 和 Accept-Encoding](#6-8-服务器-压缩文件-Content-Encoding-和-Accept-Encoding)
    - [6-9 range 范围请求 / http tpc range](#6-9-range-范围请求-/-http-tpc-range)
    - [6-10 http 缓存](#6-10-http-缓存)
    - [6-11 将 静态资源服务器工具 做成 CLI工具 (命令行工具)](#6-11-将-静态资源服务器工具-做成-CLI工具-(命令行工具))
    - [6-12 静态资源服务器 12--cli & 版本]()
    - [6-13 静态资源服务器 13--cli]()
- [第7章 本地构建]()
    - [7-1 gulp 1]()
    - [7-2 gulp 2]()
    - [7-3 babel]()
    - [7-4 webpack--简介]()
    - [7-5 webpack--entry、output]()
    - [7-6 webpack--module]()
    - [7-7 webpack--plugins]()
- [第8章 单元测试 & UI 测试]()
    - [8-1 单元测试 mocha 1--断言assert]()
    - [8-2 单元测试 mocha 2--Mocha]()
    - [8-3 测试 覆盖率 istanbul]()
    - [8-4 持续集成]()
    - [8-5 benchmark]()
- [第9章 UI 测试常用工具]()
    - [9-1 UI 测试 1]()
    - [9-2 UI 测试 2]()
    - [9-3 UI 测试 3--sinon]()
    - [9-4 UI 测试 4--webdriver]()
- [第10章 案例项目--headless 爬虫]()
    - [10-1 爬虫与反爬虫简介试看]()
    - [10-2 初使用puppeteer爬百度图片试看]()
    - [10-3 Pupeteer API]()
    - [10-4 爬虫任务分析]()
    - [10-5 爬虫代码实现1]()
    - [10-6 爬虫代码实现2]()
    - [10-7 爬虫代码实现3]()
- [第11章 课程总结]()
    - []()

----

## 第1章 导学
- 带着以下4个问题学习本门课
    - NodeJS 究竟是什么？
    - NodeJS 好在哪里？
    - NodeJS 擅长解决哪些实际问题？
    - NodeJS 怎么解决这些问题的？

- 学习方式
    - 了解 NodeJS 是什么，好在哪里
    - 从静态资源服务器实战熟悉使用NodeJS做项目流程
    - 展开介绍代码构建、测试等使用技巧，介绍项目周边

- 课程大纲
    - NodeJS 介绍
    - 调试 & 项目初始化
    - 基础API
    - 简单 Web Server
    - 单元测试 & 发布
    - NodeJS 爬虫示例

## 第2章 NodeJS 是什么，为什么偏爱NodeJS ?
- ### 2-1 NodeJS 是什么？
    - 1.官方解释："Node.js is a JavaScript runtime built on Chrome`s V8"
        - Node.js是一个构建中Chrome V8 引擎上的JavaScript运行时
        - Node.js 不是一门语言，JS才是语言。Node只是一个运行时(runtime)
        - 语言想在不同的宿主上跑，就需要不同的runtime。Node.js 就是让 JavaScript 在服务器端跑起来的 runtime
    - 2.严格来说，Node.js 不能使用 javascript 的全集，如 DOM, BOM
        - 所以，我们也可以称 Node.js 为 ECMA 的 runtime
        - Node.js 也很像 Java 的 JDK。所以我们也可以称 Node.js 为 EDK，ECMA Development Kit(工具包)
    - 3.NodeJS 特点
        - Node.js uses an event-driven, non-blocking I/O model
            - 事件驱动，非阻塞的I/O模型
        - 非阻塞 I/O
            - I/O
                - Input/Output
                - 计算机 输入/输出 的意思
            - 先看什么是 阻塞I/O
                - **阻塞：I/O 时，进程休眠等待I/O完成后再进行下一步**
                    - 为什么会这样子？因为一般情况下
                    - 计算机的指令是逐条顺序执行的，执行完前一句，才会执行下一句，直到程序结束
                    - 其中，如果程序语句遇到了，调用I/O的操作，会向系统底层的 I/O 发送调用指令，期间会等待I/O返回结果，然后在继续执行当前指令。
                    - 其中，这种等待I/O返回结果的行为，就叫做 **阻塞**
                - **非阻塞：I/O 时，函数立即返回，进程不等待 I/O 完成**
                    - 在程序指令一条条的执行，当碰到 I/O 指令，开始调用系统底层的 I/O , 然后主程序不用等待 I/O 返回结果，直接进行下一步，执行下一条指令，当 I/O 完成时，就会通知主进程，这时候，主进程再决定是使用 I/O 得到的结果继续处理，还是丢弃 I/O 得到的结果。
                    - 这其中，主程序始终是流畅的，并没有等待的过程，所以我们称之为 **非阻塞**
            - 实际上
                - 在计算机中，上一条指令，实际上就是 阻塞了 下一条指令。那为什么还把 非阻塞I/O 这个概念拿出来说？
                - 原来，在计算机中 CPU 的计算速度是奇快无比的，一秒钟能执行 30亿 条指令
                - 而，磁盘的读写操作，却远远比不上 CPU 的计算速度
                - 这将导致，我们在打开网页的时，主要的速度瓶颈在于 I/O操作，而不在于 CPU 计算速度
        - 事件驱动
            - 什么是事件驱动？
                - 举个例子
                    - 我们在开发网页的时候，写个按钮，然后给按钮绑定一个 click 事件。
                    - JavaScript 并不知道什么时候调用这个 Click 事件处理程序，只是给他绑定了 事件处理程序，然后等待调用。我也不知道什么时候调用，反正不是立马调用。
                    - 只有当按钮被点击时，才触发 click 事件，然后才会执行这个 事件处理程序
            -  等I/O的异步操作 结束后的通知主进程
            - 内部的实现 也是一个 **观察者模式**

- ### 2-2 NodeJS 究竟好在哪里？
    - NodeJS 并不适合所有 Server 的场景，Web 是 NodeJS 最适合的场景
    - 为什么前端偏爱 NodeJS ？
        - NodeJS 使用的语言就是 JavaScript
        - 前端职责范围变大，统一开发体验
        - 在处理高并发、I/O密集场景性能优势明显(事件驱动、异步I/O模型)
    - #### 什么是I/O密集？
        - CPU 密集
            - 如果一个程序，大部分时间是用来做计算、做逻辑判断、等CPU动作，我们就称之为 CPU密集
            - CPU 密集: 压缩、解压、加密、解密
        - I/O 密集
            - 如果一个程序，大部分时间是用来做存取、网络的存取操作，我们就称之为 I/O密集
            - I/O 密集：文件操作、网络操作、数据库
    - Web 常见场景
        - 静态资源读取
        - 数据库操作
        - 渲染页面
        - 由于CPU是超级快的，而 I/O 是超级慢的，所以，Web 场景是 I/O 密集场景
        - 对于上面这三个场景，Node 比 Java 更擅长
    - #### 高并发应对之道
        - 什么是高并发？
            - 单位时间内，访问量特别大，就是高并发
        - 通用的高并发解决之道
            - 举个例子
            - 老王开了一个饭店
                - 1.雇了一个厨师 小A，客人源源不断，客人来了 小A 就去接待，选好菜了 小A 就去后厨做，做完后就交给客户享用。
                    - 但是呢，总要有人排队等，因为他都是一个一个的做，所以客人有点不爽
                - 2.老王于是雇了3个厨师，现在共有 小A 小B 小C 三个厨师，客户排三条队，快了很多，这样问题就初步解决了
                    - 然后呢，饭店名气越来越大，客人就更多了。这时候，老王就想再雇用多几个厨师，但是又一想，好像不太划算，因为每雇用一个厨师，要提供宿舍、福利、管饭... 划不来。
                    - 老王想了想，**可以多花些钱，顾一些做饭快的厨师**，即使工资给两倍，宿舍什么的还是跟能力差的住的是一样的，**相较之下，还是有一定的成本降低的**
                - 3.后来老王通过调查发现，做饭快一倍的 给1.5倍工资就行了，做饭快4倍的 给1.8倍工资就行了。
                    - 相较于 单纯增加普通厨师，是快了很多，而且成本也没增加多少
                - 4.于是，老王换了三个做饭快的厨师，并雇了三个服务员来负责点菜，相当于开启了三个进程，排三个队伍 点餐，这样做饭速度 和 人流量 就达到平衡了，即使很多人来，也能上菜比较快
        - 对应于，我们 web 开发场景
            - 大厨就是物理服务器
            - 开始，高并发应对之道，就是 **增加机器数**。通过负载均衡，让流量到不同的机器上处理
                - 但是，增加机器数 增加到一定的数量时，你会发现 这并不是一个很划算的事情
            - 于是，我们开始使用更好的机器，**增加每台机器的CPU数 ——— 多核**，这样的话，同样的单位时间内 **计算能力更强了**，当然 这是针对 运算密集型的(CPU密集)，也可以增加 I/O 能力更强的机器
            - 从这方面来讲呢，单价虽然贵了，但是总体来说还划算的
            - NodeJS 性能好，是指 对于单个CPU，在处理 Web 请求，相较于Java Apache 性能更好
    - #### 进程
        - 什么是进程?
            - 官方解释：进程 是计算机中的程序，关于某数据集合上的一次运行活动，是系统进行资源分配，和调度的基本单位
            - 通俗解释：我们可以用电脑来，听音乐、上网，对应的音乐播放器、浏览器 都是一个程序，当我们打开该应用程序的时候，实际上就是把该程序 加载到了内存中 执行，我们把这个**执行中的程序 称为 进程**
            - 但是我们发现，单核CPU的电脑 也是可以一边听音乐 一边上网的。按理说，这也是调CPU的指令 一句句执行 是不能同时执行两个程序的。实际上，他们也不是同时执行的，计算机用了一个很巧妙的方法，跟播放视频很像，一秒24帧，虽然是一帧一帧的，但是肉眼看起来就是连续的动画。CPU也是这样，使用了**调度算法**，现在有两个程序，我在非常快的速度做切换，可能是0.1纳秒，不断的切换，0.1纳秒 执行A程序，0.1纳秒 执行B程序。对于人来说，就以为是连续的，我们的听的音乐也是连续的。
        - 多进程：启动多个进程，多个进程可以一块执行多个任务
    - #### NodeJS 工作模型
        <!-- - ![NodeJS 工作模型](https://github.com/946629031/hello-node.js/blob/master/img/1.jpg) -->
        - 其中，点菜的动作很快 类似于 CPU计算，大厨做饭 相当于 I/O操作
        - 类似于上面说到的，单纯的增加厨师，就相当于 每来一个web请求，我就增加一个进程 处理这个请求
            - 后面，老王发现，在一个服务员对接一个大厨的模式中，他顾的服务员太悠闲了，两分钟就点好菜了，然后大厨就做10分钟，其中服务员会有8分钟没事干。
            - 相当于一个进程处理一个web请求，这时候CPU在等待 I/O 返回结果的8分钟内 是在空转，性能就被浪费掉了。而 **NodeJS 就很好的解决了这个 CPU性能浪费的问题**
        - 再来看，**老赵的饭店**
            - 他只雇了一个服务员，几个厨师，客人来了点菜，然后叫个号就去等待上菜去了。点完菜后，服务员就去接待下一个客人去了。什么时候，厨师做好了菜，就会通知服务员，服务员看是哪个人的号 就把菜端过去了。
            - 这种模式下，就没有性能的浪费，服务员一直在接待客人，厨师一直在做菜
        - 在上图中
            - single thread 单线程
                - Javascript 的特性，单线程，只开一个进程，一个进程也只开一个线程。NodeJS 也继承了这个特性
                - 单线程只是针对 主进程，I/O 操作 是系统底层 自己做多线程调度的
            - 单线程，并不是单进程
                - 另外一个，对 NodeJS 很深的误解："NodeJS 没法使用多CPU"
                - cluster 模块，提供的是多进程的解决方案，能够利用多核CPU，而不是"我有一个8核CPU 你只能使用一个CPU"
    - #### 线程
        - 什么是线程？
            - 官方解释：线程 是进程内一个相对独立的、可调度的执行单元，与同属一个进程的线程共享进程的资源
            - 通俗解释：线程 相当于 分子里的原子。一个音乐播放器进程 里的多个线程，只能使用分配给该音乐播放器的内存，不能用其他进程的内存
        - 多线程：启动一个进程，在一个进程内启动多个线程，这样，多个线程也可以一块执行多个任务

## 第3章 环境 & 调试
NodeJs 的开发环境、运行环境、常用 IDE 以及集中常用的调试工具 & 方法
- ### 3-1 CommonJS1
    - #### node 运行环境
        - 安装node [node官网](https://nodejs.org)
        - **CommonJS** - 模块规范
            - nodejs 的模块管理规范
            - 其他模块规范还有：AMD、CMD、CommonJS
            - **CommonJS 规定**
                - 1.**每个文件是一个模块，有自己的作用域**
                    - 也可以反过来说，一个文件就是一个模块，一个文件内也只能有一个模块，不允许在一个文件内定义两个模块
                    - **作用域** 
                        - 虽然我们写代码的时候，已经把语句、变量 都写在最外面了，但是在 node 执行js文件的时候，都会给每个模块自动包裹一个函数，所以模块内的变量 就会**自动变成了 局部变量**
                - 2.**在模块内部 moudule 变量代表模块本身**
                - 3.**module.export 属性代表模块对外接口**
        - **global** - 全局对象
            - 在以前，浏览器上有 BOM,DOM,其中 window 就是全局对象，alert 和 console 可以不做任何的引用就直接使用，是因为它直接挂载到了全局对象上
            - 但是，由于 NodeJS 是在服务器上跑的，所以它没有 BOM,DOM ，只有 ECMA 的全局对象，而没有 window 全局对象，取而代之的是 global 全局对象 
        - **proess** - 当前执行的进程
    - #### 执行 node 脚本
        - 新建js文件
            ```js
            // run.js
            console.log('this is a test')
            ```
        - 执行js脚本
            - 1.cd 到该js脚本的目录下
            - 2.执行 node+文件名 ```node run.js```
    - #### node 调试方法
        - 执行命令 ```node --inspect --inspect-brk 01-run.js```
            - ```--inspect``` 开启调试模式
            - ```--inspect-brk``` 在第一行处打断点
        - 然后在 chrome 浏览器，打开控制台，会控制台左侧看到一个绿色的 node图标，点击图标，即可进入node调试界面
        - [【慕课网】 Chrome 调试工具讲解 node.js调试入门](https://www.imooc.com/learn/1093)

- ### 3-2 CommonJS2
    - **require 规则**
        - 1."/"表示绝对路径， "./" 表示相对当前文件的路径
        - 2.支持js、json、node 拓展名，不写时会依次尝试
        - 3.不写路径时
            - 当不写路径时会被认为是 build-in 模块（**自带模块**）（优先）
            - 或者各级 node_modules 内的第三方模块
                - 先会在当前层级的 node_modules 查找，如果没有，则会向上一层寻找，如果一直到根目录都没找到 该模块 则会报错
    - **require 特性**
        - 1.**module 被加载的时候执行，加载后缓存**
            - 加载后缓存 的意思是，只加载一次，第二次就直接从内存中读取了，不会重复加载了
        - 2.**一旦出现某个模块被循环加载，就只输出已经执行的部分，还未执行的部分不会输出**
            - 循环加载 是什么意思？
                - 就是 A 依赖了 B，B 又require了 A，两个互相引用了（在其他很多语言中就会报错）
            - 在我们写业务代码时，要**尽量避免** 这种循环加载的情况，因为很难理解，容易把人绕晕
    - 1.定义一个模块
        ```js
        // 02-cusmod.js
        console.log('this is a module')

        const testVar = 100;

        function test(){
            console.log(testVar)
        }

        module.exports.testVar = testVar;
        module.exports.testFn = test;
        ```
    - 2.执行一个引用模块
        ```js
        // 03-require.js
        const mod = require('./02-cusmod')

        console.log(mod.testVar)

        mod.testFn()
        ```
    - 3.执行结果如下：
        ```js
        $ node 03-require.js
        this is a module
        100
        100
        ```
        - 但是这其中，你会发现有一点奇怪的地方，为什么会出现 ```this is a module``` ?
        - 原因：
            - 当我们加载一个模块的时候，它的所有语句都会被执行，所以我们才能拿到里面的变量
    - 4.验证一下 ```module 被加载的时候执行，加载后缓存```
        ```js
        // 04-require_cache.js
        require('./02_cusmod');
        require('./02_cusmod');
        ```
        - 当执行 ```node 04-require_cache.js``` 后，
        - 执行结果如下
        ```js
        this is a module
        ```
        - ```02_cusmod.js``` 里面的 ```console.log('this is a module')``` 只被打印了一次，证明："module 被加载的时候执行，加载后缓存。只加载一次，第二次就直接从内存中读取了，不会重复加载了"
        - 这种情况也说明，如果你有什么东西不希望被用户看到，你就应该把它 ```console.log()``` 写到 ```function()``` 里面。这样用户在使用时，就不会看到你打印的内容了
    - 5.验证一下 ```一旦出现某个模块被循环加载，就只输出已经执行的部分，还未执行的部分不会输出```
        - 为了看出循环引用被部分加载的特性，我们来重复定义一个变量，看他的具体值是多少，就知道他执行到哪里了
        ```js
        // 05-modA.js
        module.exports.test = 'A';

        const modB = require('./05-modB');
        console.log('modA: ', modB.test);

        module.exports.test = 'AA';
        ```
        ```js
        // 05-modB.js
        module.exports.test = 'B';

        const modA = require('./05-modA');
        console.log('modB: ', modA.test);

        module.exports.test = 'BB';
        ```
        ```js
        // 05-main.js
        const modA = require('./05-modA');

        const modB = require('./05-modB');  // 如果注释掉这一句，不影响下面的输出结果
        ```
        - 执行结果
        ```js
        $ node js/05-main.js
        modB:  A
        modA:  BB
        ```
        - 如果把 ```05-main.js``` 改成这样
        ```js
        // 05-main.js
        const modA = require('./05-modA');

        const modB = require('./05-modB');

        console.log(modA.test);
        console.log(modB.test);
        ```
        - 执行结果为
        ```js
        $ node js/05-main.js
        modB:  A
        modA:  BB
        AA  // 这里输出 AA 和 BB，说明 modA 和 modB 已经被完全加载了
        BB
        ```
        - 在我们写业务代码时，要**尽量避免** 这种循环加载的情况，因为很难理解，容易把人绕晕
        
- ### 3-4 引用系统内置模块 & 引用第三方模块
    - 1.引用系统内置模块
        ```js
        // 06-fs.js
        const fs = require('fs')  // 引用系统内置模块不用写路径，直接写模块名即可

        const result = fs.readFile('./06-fs.js', (err, data) => {  // readFile() 是异步操作，当前是没有返回结果的
            if (err) {  // 如果网络错误 或者 路径错误... 等其他原因 则会报错
                console.log(err)
            }else{      // 如果没错误，则能读取到文件
                console.log(data.toString())    // 将buffer 转换成字符串
            }
        })

        console.log(result)
        ```
    - 2.引用第三方模块
        - 引用第三方模块，也不需要写路径
        - 因为在系统模块中如果没找到该模块，就会自动去 node_modules 里面找
        - 优先到当前目录下 node_modules 里查找该模块，如果没有则向上一层查找，直到根目录，如果还没有则会抛出异常
            - 题外话：
                - 现在的 NPM 做了优化，会把某个模块的依赖，尽量放在同一级目录上
                - 这样能避免相同的模块被多次安装的问题
                - 也能提高查找模块的速度，优化性能
                - 但是，以前的旧版本 NPM 却是一层套一层的...
        ```js
        // 07-chalk.js
        const chalk = require('chalk');     // 引用第三方模块，也不需要写路径

        console.log(chalk.red('This is a red text'))
        ```
        - 在使用第三方模块时，需要安装该模块 ```npm i chalk```

- ### 3-5 module.exports 与 exports 的区别
    - 我们知道，一个模块中执行的时候，NodeJS 会帮我们包裹一个函数
        ```js
        // 08-exports.js
        (
            function(exports, require, module, __filename, __dirname) {

            }
        )
        ```
    - 其中 exports 是 module.exports 的快捷方式
        - 我们来验证一下
            ```js
            // 08-exps.js
            exports.test = 100;
            ```
            ```js
            // 08-main.js
            const mod = require('./08-exps.js')

            console.log(mod.test)       // 这里能被打印出 100
            ```
        - 能被打印出 100 ，则证明 **exports 相当于 module.exports**
    - **注意**：
        - 既然，exports 是 module.exports 的快捷方式
        - 那么，我们就不能改变 exports 的变量指向，如
        ```js
        // 08-exps.js   我们把内容修改成这样之后
        exports = {
            a: 1,
            b: 2,
            test: 100
        }
        ```
        - 这种情况下，exports 的指向被改变，就不再指向 module.exports 了
        - 当我们再执行 ```node 08-exps.js``` 时，会输出 ```undefined```
    - **但是**：
        - 如果我们这样赋值
        ```js
        // 08-exps.js   我们把内容修改成这样之后
        module.exports = {
            a: 1,
            b: 2,
            test: 100
        }
        ```
        - 当我们再执行 ```node 08-exps.js``` 时，就能输出 ```100```，是可以拿到 test 的值的
    - **总结**：
        - 在 CommonJS 中，模块对外的输出 永远都是 ```module.exports```
        - 不用轻易改变 ```exports``` 的指向，如果改变了 它就跟普通的对象没有任何区别


- ### 3-6 global变量
    - global 是什么？
        - global 是 NodeJS 的全局变量
        - 和浏览器非常相像，在浏览器中，我们的 全局方法和属性 就挂载在 window 中
        - 同样的，在 node 中，我们把希望能在全局访问到的 对象、属性、方法 就挂载在 global 中
    - global 自带的属性 和 方法
        - CommonJS
        - Buffer, process, console
        - timer
            - 包括 setTimeout, setInterval, setImmediate ...等
        - 以上的属性和方法，都是 node 默认挂载在 global 上的
    ```js
    // 09-global.js
    const testVar = 1000;

    global.testVar2 = 200;  // 在 global 上挂载全局变量，testVar2

    module.exports.testVar = testVar;
    ```
    ```js
    // 09-main.js
    const mod = require('./09-global.js');

    console.log(mod.testVar)    // 1000

    console.log(testVar)    // undefind  由于每个模块都是有自己作用域的，所以取不到该值

    console.log(testVar2)   // 200  全局变量, 任意一个地方都可以访问
    ```

- ### 3-7 process进程
    - [Process 官方文档](http://nodejs.cn/api/process.html)
    - 什么是 Process ？
        - 进程
    - Process 里面有什么？
        - Process Events - 进程事件
            - uncaughtException
                - 在我们程序执行的时候，有的异常没有被捕获，这样的话有可能 **打断整个进程**，为了防止这种情况，我们可以在 Process 下面 **加最后一层保险。当异常被抛到最外层的时候，我们来捕获一下**，让 Process 可以优雅的退出
        - `process.argv` 参数相关
            > argv, argv0, execArgv, execPath <br><br>
            > **上面4个 可以读取启动 Node.js 进程时，传入的命令行参数**

            <br>

            > **总结**：<br>
            > 这四个参数，大多数情况下，我们只需要用 ```process.argv``` 就足够了，因为 ```process.argv``` 包含了其他三个

            ```js
            // 10-process.js

            const {argv, argv0, execArgv, execPath} = process; // 这四个对象 都是 process 的子对象
            ```
            - ```process.argv``` **包含当启动 Node.js 进程时，传入的命令行参数**
                ```js
                // 10-process-argv.js

                process.argv.forEach(item => {
                    console.log(item)
                })
                ```
                ```js
                当我们在命令行执行上面当js脚本时: ```node 10-process-argv.js```

                会得到下面当结果:

                /usr/local/bin/node     // 表示启动进程所用的命令，也是node安装路径
                /Users/Samartian/nodejs/demos/10-process-argv.js    // 表示当前执行文件的路径

                // 上面两条是固定的
                ```
                ```js
                当然也可以带自定义参数，如，执行 ```node 10-process-argv.js --test a=1 b=2```

                /usr/local/bin/node
                /Users/Samartian/nodejs/demos/10-process-argv.js

                --test
                a=1
                b=2

                // 命令行传入的其它参数，也都会被打印出来
                ```
            - ```process.argv0``` **argv 的第一个参数**
                - process.argv0 实际上就是 process.argv[0]
                ```js
                console.log(process.argv0)
                ```
                - 执行该脚本，得到结果如下
                ```js
                /usr/local/bin/node
                ```
            - ```process.execArgv``` **读取 特殊参数**
                - 我们发现，在 文件名 和 node 之间写的 参数，是不会进入到 ```argv``` 的，如
                    - ```node --inspect 10-process-argv.js --test a=1 b=2```
                    - 打印结果如下
                    ```js
                    /usr/local/bin/node
                    /Users/Samartian/nodejs/demos/10-process-argv.js

                    --test
                    a=1
                    b=2
                    ```
                - 但是，我们可以通过 ```process.execArgv``` 的方式来读取，在 文件名 和 node 之间写的 参数
                    ```js
                    process.argv.forEach(item => {
                        console.log(item)
                    })

                    console.log(process.execArgv)
                    ```
                    - 执行```node --inspect 10-process-argv.js --test a=1 b=2```
                    - 打印结果如下
                    ```js
                    /usr/local/bin/node
                    /Users/Samartian/nodejs/demos/10-process-argv.js

                    --test
                    a=1
                    b=2

                    [ '--inspect' ]     // 这是 process.execArgv 读取到的 特殊参数
                    ```
            - ```process.execPath``` **读取 可执行程序的路径** <br>
                ```js
                process.argv.forEach(item => {
                    console.log(item)
                })

                console.log(process.execPath)
                ```
                - 打印结果如下
                ```js
                /usr/local/bin/node
                /Users/Samartian/nodejs/demos/10-process-argv.js

                --test
                a=1
                b=2

                /usr/local/bin/node     // 这是 process.execPath 读取到的 可执行程序的路径
                ```
        - ```process.env``` **返回包含用户环境的对象**
            ```js
            // 10-process-env.js
            console.log(process.env)
            ```
            此对象的示例如下所示：
            ```js
            {
                TERM: 'xterm-256color',
                SHELL: '/usr/local/bin/bash',
                USER: 'maciej',
                PATH: '~/.bin/:/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin',
                PWD: '/Users/maciej',       // 当前的路径
                EDITOR: 'vim',
                SHLVL: '1',
                HOME: '/Users/maciej',
                LOGNAME: 'maciej',
                _: '/usr/local/bin/node'

                // ...等待
            }
            ```
        - ```process.cwd()``` **返回当前路径，跟命令行里 pwd 是一样的**
            ```js
            // 10-process-env.js
            console.log(process.cwd())
            ```
            - 执行结果
            ```js
            /Users/Samartian/nodejs/demos
            ```
        - ```setImmediate()``` **等下一个事件队列**
            - 同步的东西都执行完后，就执行它 ```setImmediate()```
            - 它和事件无关，所以它只有一个参数, 直接传入一个 function 即可
            ```js
            setImmediate(() => {
                console.log('setImmediate')
            })
            ```
            - 题外话：node.js 是不断的在检查自己的事件队列的
        - ```process.nextTick()```
            - ```process.nextTick()``` 跟 ```setImmediate()``` 非常像，都是过一会儿执行
            - **当前事件队列里面的东西执行完后，就执行他**
            ```js
            process.nextTick(() => {
                console.log('nextTick')
            })
            ```
            - 但是，```process.nextTick()``` 会比 ```setImmediate()``` **执行的早**
                - 我们来验证一下
                ```js
                setImmediate(() => { console.log('setImmediate') })

                setTimeout(()   => { console.log('setTimeout') }, 0)

                setInterval(()  => { console.log('setInterval') }, 0)

                process.nextTick(() => { console.log('nextTick') })
                ```
                - 执行结果
                ```js
                nextTick
                setTimeout
                setInterval
                setImmediate
                ```
                - 总结：
                    -  **执行速度**： ```process.nextTick()``` > ```setTimeout()``` = ```setInterval()``` > ```setImmediate()```
                    - ```process.nextTick()``` 是插入了 **当前事件队列的最后一个**
                    - ```setImmediate()``` 是放在 **下个事件队列的队首**
                    - ```setTimeout()``` 和 ```setInterval()``` 放在上面两个的中间
                    - 如果用 ```setImmediate()``` 可以，用 ```process.nextTick()``` 也可以，这种情况下，推荐用 ```setImmediate()```，因为这是后来优化的版本 后来加上的api
                    <br><br>
                    - 如果 ```process.nextTick()``` 里面 再插入 ```process.nextTick()```，那么其他的几个 timer 就可能导致 我正常的异步操作都没法正常执行了，所以在使用 ```nextTick()``` 时 一定要慎重。
                        ```js
                        process.nextTick(() => {
                            console.log('nextTick')

                            process.nextTick(() => {
                                console.log('nextTick')
                            })
                        })
                        ```
                        - 除非你想要做 异步操作前 执行某个操作，才用 ```process.nextTick()```

- ### 3-8 debug 调试
    - 为什么要 **debug 调试**？
        - 在我们编写比较复杂的程序，遇到一些意外的问题，让我们不能一眼看出问题时，如果了解调试技巧，可以让我们**排查问题 变得迅速 且 精确**
    - #### node 调试工具 使用方法
        - ```"node --inspect-brk demo.js"```
            - ```--inspect``` 开启调试工具
            - ```--inspect-brk``` 开启调试工具 并 在第一行上打一个断点
        - 然后在 chrome 浏览器，打开控制台，会控制台左侧看到一个绿色的 node图标，点击图标，即可进入node调试界面
        - 在我们做 plugin 开发的时候，需要对 plugin 做调试的时候，在插件代码里写 ```debugger;``` 来手动打断点
        - **add conditional breakpoint** 条件断点
            - 条件断点，在对于 for 循环，或者某些特定情况下，暂停，是非常实用的一个功能
        ```js
        console.log(process.env)

        setImmediate(() => { console.log('setImmediate') })

        debugger;

        setTimeout(()   => { console.log('setTimeout') }, 0)

        process.nextTick(() => { console.log('nextTick') })
        ```
    - 除了可以利用 chrome 浏览器做node调试以外，还可以利用 vscode 里面的调试工具来调试，操作方法跟 chrome 非常类似


## 第4章 NodeJS 基础 API
介绍 NodeJS 最常用的基础 API，为后面项目开发做好准备path、Buffer、event、fs。
- ### 4-1 path 路径
    - 1.path 是 node.js 内置模块，使用时需要先引入
        ```js
        const path = require('path')
        ```
    ```
    normalize join resolve
    basename extname dirname
    parse format
    sep delimiter win32 posix
    ```
    - 2.path.normalize() 路径规范化
        - 作用：帮我们把路径做一些简单的处理，可能有时候 我们写的路径有一些小的问题，小的瑕疵，它能自动识别 并 帮我们改成标准的写法
        ```js
        const { normalize } = require('path');              // ES6 语法
        const   normalize   = require('path').normalize;    // ES5 语法

        console.log(normalize('/usr//local/bin'))           // usr/local/bin  比如说不小心多写了一个 '/'
        console.log(normalize('/usr/local/../bin'))         // usr/bin        比如直接在路径里写回到上一层
        ```
    - 3.path.join() 拼接路径
        ```js
        const path = require('path')

        console.log(path.join('/usr/', '/local', '/bin/'));     // \usr\local\bin\
        console.log(path.join('/usr', '../local', 'bin/'));     // \local\bin\
        ```
    - 4.path.resolve() 获取绝对路径
        ```js
        const path = require('path')

        console.log(path.resolve('./'));   // C:\Users\Administrator\Desktop\nodejs\js  获取当前路径的绝对路径
        ```
    - 5.basename extname dirname
        ```js
        const path = require('path')

        const filePath = '/usr/local/bin/no.txt'

        console.log(path.basename(filePath));   // 文件名
        console.log(path.dirname(filePath));    // 所在文件夹路径
        console.log(path.extname(filePath));    // 拓展名
        ```
    - 6.parse format
        - parse format 是一对互逆的操作
            - parse 把文件名解析成 basename extname dirname
            - format 是 parse 的逆操作
        ```js
        const path = require('path')

        const filePath = '/usr/local/node_modules/n/package.json'
        const ret = path.parse(filePath);

        console.log(ret);
        console.log(format(ret));

        // 返回内容
        { 
            root: '/',
            dir: '/usr/local/node_modules/n',
            base: 'package.json',
            ext: '.json',
            name: 'package' 
        }

        /usr/local/node_modules/n/package.json
        ```
        - 一般情况下 format 用的比较少，但是 如果你得到了 path.parse() 的结果，然后需要改其中的一些信息，再转回 filePath 的形式，用 format 就会比 字符串查找的方式简单多了。

    - 7.sep delimiter win32 posix 操作系统相关的属性方法
        - path.sep 提供平台特定的路径片段分隔符
            - Windows 上是 \
            - POSIX 上是 /
        - path.delimiter 是 PATH 路径定界符
            - ; 用于 Windows
            - : 用于 POSIX
        - path.win32 属性提供对特定于 Windows 的 path 方法的实现的访问
        - path.posix 属性提供对 path 方法的 POSIX 特定实现的访问
            - posix 是指 可移植性操作系统接口
        ```js
        const path = require('path')

        console.log('sep: ', path.sep)          // 打印: '/'
        console.log('sep: ', path.win32.sep)

        console.log('sep: ', process.env.PATH)
        // 打印: '/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin'

        console.log('sep: ', path.delimiter)
        console.log('sep: ', path.win32.delimiter)      // 看 win 上是怎么实现的
        console.log('sep: ', path.posix.delimiter)      // 看 posix 上是怎么实现的

        process.env.PATH.split(path.delimiter);
        // 返回: ['/usr/bin', '/bin', '/usr/sbin', '/sbin', '/usr/local/bin']
        ```
    - 8.几个类似的路径 的区别
        ```js
        const path = require('path')

        const mod = require('./10-process-env.js')

        console.log('__dirname     ', __dirname)
        console.log('process.cwd() ', process.cwd())
        console.log('./            ', path.resolve('./'))
        ```
        - 1.当你 cd 到 demos 目录下时，打印结果
        ```
        __dirname      /user/Samaritan/nodejs/demos
        process.cwd()  /user/Samaritan/nodejs/demos
        ./             /user/Samaritan/nodejs/demos
        ```
        - 2.当你 cd 到 demos 的上层目录下时，打印结果
        ```
        __dirname      /user/Samaritan/nodejs/demos
        process.cwd()  /user/Samaritan/nodejs
        ./             /user/Samaritan/nodejs
        ```
        - 总结：
            - ```__dirname``` 和 ```__filename``` 总是返回文件的绝对路径
            - ```process.cwd()``` 总是返回执行 node 命令所在的文件夹，跟 ```pwd``` 一样
            - ```./```
                - 在 require 方法中总是相对当前文件所在的文件夹
                - 在其他地方 和 process.cwd() 一样，相对 node 命令所在的文件夹

- ### 4-3 Buffer
    - 背景：
        - node 操作频率比较高的两个东西，一个是 **file**，另一个是 **网络**，这两个的共同点都是要操作 **二进制数据**，所以就引入了 **Buffer** 来处理
        - 在引入 TypedArray 之前，JavaScript 语言没有用于读取或操作二进制数据流的机制。
        - Buffer 是一个很像 数组 的东西(TypeArray)，很多 Api 也类似
    - 1.**Buffer 是用于处理二进制数据流的**
    - 2.**实例类似整数数组，大小固定**
        - 里面都是 0~255 的数字
        - 16进制是数字来表示
        - Buffer 大小是固定的。不能像数组一样，不能随便修改长度，追加内容
        - 实例化之后，是多大就多大，不能进行变更了
    - 3.**C++ 代码在 V8 堆外分配物理内存**
        - Buffer 所用的 堆内存，并不是 V8 来分配的，而是C++ 代码在 V8 堆外分配物理内存
    - 4.**Buffer Api**
        ```js
        const buf1 = Buffer.alloc(10)
        // 创建一个长度为10，且用零填充的 Buffer

        const buf2 = Buffer.alloc(10, 1)
        // 创建一个长度为10，且用 0x1 填充的 Buffer。其中 0x1 为 1 的16进制写法

        const buf3 = Buffer.allocUnsafe(10)
        // 创建一个长度为10，且未初始化的 Buffer
        // 这个方法比调用 Buffer.alloc() 更快
        // 但返回的 Buffer 实例可能包含旧数据
        // 因此需要使用 fill() 或者 write() 重写

        const buf4 = Buffer.from([1,2,3])
        // 创建一个包含 [0x1, 0x2, 0x3] 的 Buffer

        const buf5 = Buffer.from('test')
        // 创建一个包含 UTF-8 字节 [0x74, 0xc3, 0xa9, 0x73, 0x74] 的 Buffer。

        const buf6 = Buffer.from('test', 'latin1')
        // 创建一个包含 test 的字节，并且是用 Latin-1 方式编码的
        ```
    - 5.Buffer 静态属性方法，本身被放在 Buffer 类中的，所以不用实例化
        ```
        Buffer.byteLength
        Buffer.isBuffer()
        Buffer.concat()
        ```
        - Buffer.byteLength
            - 返回字符串的实际 **字节** 长度
            - 与 **String.prototype.length** 不同，后者返回字符串的 **字符数**
        ```js
        const str = '我+你=我爱你'

        console.log(`${str}: ${str.length} 个字符， `+
                    `${Buffer.byteLength(str, 'utf8')} 个字节`)

        // 打印：我+你=我爱你: 7 个字符, 17个字节
        ```
        - Buffer.isBuffer() 判断是否为 Buffer
        ```js
        console.log(Buffer.isBuffer({}))    // false
        console.log(Buffer.isBuffer(Buffer.from([1,2,3])))   // true
        ```
        - Buffer.concat()  拼接Buffer
        ```js
        const buf1 = Buffer.from('This ')
        const buf2 = Buffer.from('is ')
        const buf3 = Buffer.from('a ')
        const buf4 = Buffer.from('test ')
        const buf5 = Buffer.from('! ')

        const buf = Buffer.concat([buf1, buf2, buf3, buf4, buf5])

        console.log(buf.toString())     // This is a test !
        ```
    - 6.Buffer 实例 Api，需要先实例化一个Buffer, 才能使用
        ```
        buf.length
        buf.toString()
        buf.fill()
        buf.equals()
        buf.indexOf()
        buf.copy()
        ```
        ```js
        // buf.length 它返回的值，不一定是指里面有多少个字符，而是 buffer 实际占用字节数
        const buf = Buffer.from('This is a test !')
        console.log(buf.length)  // 16
        // 例如，我申请10个长度的 Buffer，但是我只在里面放一个字符，那么它仍然长度为10
        const buf2 = Buffer.alloc(10)
        buf2[0] = 2
        console.log(buf2.length)    // 10


        // buf.toString()  默认以 utf-8 方式解码，也可以指定解码方式
        console.log(buf.toString())     // This is a test !
        console.log(buf.toString('base64'))     // VGhpcyBpcyBhIHRlc3QgIQ==


        // buf.fill() 接收的参数：填充的 value, 从第几个开始，填充到第几个。如果只传入了 value 则自动填充完所有
        const buf3 = Buffer.allocUnsafe(10)
        console.log(buf3)                   // <Buffer 00 00 00 00 00 00 00 00 18 34>
        console.log(buf3.fill(10, 2, 6))    // <Buffer 00 00 0a 0a 0a 0a 00 00 18 34>


        // buf.equals()  判断两个Buffer内容是否相等
        // 仅仅是判断两个Buffer是否相等，不判断他们是不是 同一个Buffer (指向同一块内存)
        const buf4 = Buffer.from('test')
        const buf5 = Buffer.from('test')
        const buf6 = Buffer.from('test!')
        console.log(buf4.equals(buf5))      // true
        console.log(buf4.equals(buf6))      // false
        

        // buf.indexOf()  buf 中首次出现 value 的索引，如果 buf 没包含 value 则返回 -1
        console.log(buf4.indexOf('es'))     // 1
        console.log(buf4.indexOf('esa'))    // -1
        // 还有 buf.lastIndexOf() 用法一样，返回 最后一次出现的索引




        // buf.copy()  拷贝buffer
        // buf.copy(b, 0, i) 把buf拷贝到 b 里面去，从 b[0] 开始写入，写入的内容来源从 buf[i] 开始拷贝
        const buf = Buffer.from('中文字符串！')

        for(let i = 0; i < buf.length; i += 5 ){    // 把字符串拆分，每5个字节分成一个
            const b = Buffer.allocUnsafe(5)
            buf.copy(b, 0, i)

            console.log(b.toString())
        }
        // 打印：
        // 中�
        // �字�
        // ��串
        // ！


        // 通过 StringDecoder 解决中文乱码问题
        const StringDecoder = require('string_decoder').StringDecoder;  // StringDecoder 也是node的内置模块
        const decoder = new StringDecoder('utf8');  // 实例化 StringDecoder, 并传入解码方式

        for(let i = 0; i < buf.length; i += 5 ){
            const b = Buffer.allocUnsafe(5)
            buf.copy(b, 0, i)

            console.log(decoder.write(b))
        }
        // 打印：
        // 中
        // 文字
        // 符串
        // ！
        ```
        
        - StringDecoder 解码原理
            - StringDecoder 不会知道自己在处理 宽字节 的东西，它会自动检测，看看多少个能打印出来
            - 在上面的例子中，中文是 每3个字节为一个字符，它尝试性测试到了 每3个字节 能正常打印，所以后面都套用这个规则来 解码
            - 测试到 0~2个字节可以打印一个，所以，即使第一次除开0~2 个字节后，还有2个字节
            - 但是发现，2个字节没法正常解码，所以，就会先把剩下的2个字节先存起来，留到下一次用
            - 下一次：把上一次的 3~4 个字节，跟下一次的 第0个 字节拼接，发现能正常解码，于是就这样输出


- ### 4-6 Event 事件
    - 什么时候会用到 ```Event``` 事件呢？
        - 主进程的业务逻辑，遇到要调用 I/O 操作时，就会异步调用 系统底层的 I/O 进行处理，当处理完后，它会告诉主进程 说"**已经处理完了,可以进行下一步了**"，主进程接收到通知后，就会继续往下执行
        - 那么问题来了，他是怎么做到 通知主进程 "**已经处理完了**" 的呢？
        - 答：通过 **触发事件** ```EventEmitter``` 类的实例。
    - 所有能触发事件的对象都是 ```EventEmitter``` 类的实例，你要让你的方法有 **事件触发的能力** 就要继承 ```EventEmitter``` 类。这些对象开放了一个 ```eventEmitter.on()``` 函数，允许将一个或多个函数绑定到会被对象触发的事件名上。
    - 例子，一个绑定了监听器的 ```EventEmitter``` 实例。```eventEmitter.on()``` 方法用于注册监听器，```eventEmitter.emit()``` 方法用于触发事件。
        ```js
        const EventEmitter = require('events')

        class CustomEvent extends EventEmitter {}

        const ce = new CustomEvent()

        ce.on('test', () => {
            console.log('this is a test!')
        })

        setInterval(() => {
            ce.emit('test')  // 触发绑定在 ce 实例上的 test 事件
        }, 500)
        ```
    - 在触发事件时，如何传递参数？
        ```js
        const EventEmitter = require('events')

        class CustomEvent extends EventEmitter {}

        const ce = new CustomEvent()

        ce.on('error', (err, time, num) => {
            console.log(err)    // error msg...
            console.log(time)   // 1560847624263
            console.log(num)    // 123
        })

        ce.emit('error', new Error('oops!'), Date.now(), 123)  
        // 由于 eventEmitter.emit() 允许传递多个参数，所以直接在后面跟着写就行了，参数个数不限
        ```
    - 只触发一次的事件
        - 在有的情况下，一个事件，可能在N种情况下，都会被触发，但是我只要他 能且只能 被触发一次就可以了。那么该如何实现呢？
        - 把上面第二个例子改成这样，即可
        ```js
        const EventEmitter = require('events')

        class CustomEvent extends EventEmitter {}

        const ce = new CustomEvent()

        ce.once('test', () => {     // 把这里原来的 on() 方法，改成 once() 即可。跟 jquery 类似
            console.log('this is a test!')
        })

        setInterval(() => {
            ce.emit('test')
        }, 500)
        ```
    - 取消事件绑定
        - 在有的情况下，有的事件 我只需要触发两次。或者有的场景下，我已经绑定的事件，需要移除掉，那么我们该怎么办呢？
        - 类似于浏览器里的，```removeEventListener()```
        ```js
        const EventEmitter = require('events')

        class CustomEvent extends EventEmitter {}

        function fn1(){
            console.log('fn1')
        }

        function fn2(){
            console.log('fn2')
        }

        const ce = new CustomEvent()

        ce.on('test', fn1)
        ce.on('test', fn2)

        setTimeout(() => {
            ce.removeListener('test', fn1)    // 移除 test 事件下面的 fn1 function
            ce.removeListener('test', fn2)

            ce.removeAllListeners('test')     // 移除 test 事件下的所有 事件处理函数
        },1500)
        ```


- ### 4-8 fs 文件系统
    - fs 是什么？
        - fs 是 file system 的缩写，文件系统。处理文件时，需要用到它
        - fs 主要是对 POSIX 函数接口的封装
        - 使用时，先通过 ```require('fs')``` 引入即可，是 node 内置模块
    - 虽然 node 提倡我们使用 **异步** 进行文件操作，但是 fs 都提供了 同步和异步 的方法
        - 异步方法中的，**最后一个参数** 都必须是回调函数，而 回调函数中的 **第一个参数** 都 必须要保留给异常。看下面例子
        ```js
        const fs = require('fs')

        fs.unlink('/tmp/hello', (err) => {  // fs.unlink 是删除文件
            if (err) throw err;
            console.log('成功删除 /tmp/hello')
        })
        ```
    - fileSystem 接口目录
        - [1.fs.readFile() 读文件](#1.fs.readFile()-读文件)
        - [2.fs.writeFile() 写文件](#2.fs.writeFile()-写文件)
        - [3.fs.stat() 文件信息](#3.fs.stat()-文件信息)
        - [4.fs.rename() 重命名](#4.fs.rename()-重命名)
        - [5.fs.unlink() 删除文件](#5.fs.unlink()-删除文件)
        - [6.fs.readdir() 读取文件目录](#6.fs.readdir()-读取文件目录)
        - [7.fs.mkdir() 创建目录](#7.fs.mkdir()-创建目录)
        - [8.fs.rmdir() 删除文件夹](#8.fs.rmdir()-删除文件夹)
        - [9.fs.watch() 监听](#9.fs.watch()-监听)
        - [10.fs.readStream()](#10.fs.readStream())
        - [11.fs.writeStream()](#11.fs.writeStream())
        - [12.解决地狱回调的问题](#12.解决地狱回调的问题)
    - #### 1.fs.readFile() 读文件
        - ```fs.readFile()``` 是异步读取
            ```js
            const fs = require('fs')

            fs.readFile('./filename.js', 'utf8', (err, data) => {
                //    参数 filePath, encoding , 回调函数 error, data 读到的内容
                if (err) throw err;

                console.log(data)
            })
            ```
            - 如果没有写 编码参数，也可以用 ```data.toString()``` 转成字符串
        - ```fs.readFileSync()``` 是同步读取
            ```js
            const fs = require('fs')

            const data = fs.readFileSync('./filename.js', 'utf8');
            // 因为是同步读取，所以直接返回文件内容，不用回调函数

            console.log(data)
            ```
        - 同步 与 异步 的优缺点
            - 看起来 同步读取 跟 异步读取，都需要等待文件读取 的这个等待时间，似乎都一样，需要等待。
            - 那么我们在做项目开发的时候，是不是用 ```fs.readFile()``` 跟 ```fs.readFileSync()``` 都是一样的呢？ **反正都需要等待**
            - 事实上，这两种方式来响应用户请求，如果只有一个用户请求，那就没有什么区别，都需要等待
            - 但是，如果是N个用户请求，那就不一样了。用户多了以后，如果使用 ```fs.readFileSync()``` 同步读取，那么如果读取的文件比较大，就会 **阻塞主进程** 导致 服务器无法响应别的用户请求了
            - 而 如果是使用 ```fs.readFile()``` 这种异步方式，主进程接到读文件的命令后，就会交给系统底层 I/O 去执行，执行完了才告诉主进程，这种方式 **不会阻塞主进程** ，能够响应N个用户的请求
            - 所以，**能用异步就尽量用异步**，因为异步是node推荐的方式

    - #### 2.fs.writeFile() 写文件
        ```js
        const fs = require('fs')

        fs.writeFile('./text.txt', 'this is a test', {encoding: 'utf8'}, err => {
            // 参数：filePath/filename, 写入的内容，编码，回调函数
            // 上面的 {encoding: 'utf8'} 也可以直接写成 'utf8'
            if (err) throw err;

            console.log('写入成功')
        })
        ```
        - 除了可以写字符串，也可以直接写 Buffer
            ```js
            const fs = require('fs')

            const buf = Buffer.from('this is a test')

            fs.writeFile('./text.js', content, err => {
                // 如果写入的是Buffer，他就会忽略编码，也不用写编码了
                if (err) throw err;

                console.log('写入成功')
            })
            ```
    - #### 3.fs.stat() 文件信息
        ```js
        const fs = require('fs')

        fs.stat('./text.js', (err, stats) => {
            if (err) {
                console.log('文件不存在')
                throw err;
                return;
            }

            console.log(stats.isFile())         // 是否是文件
            console.log(stats.isDirectory())    // 是否是目录

            console.log(stats)
        })
        ```
        - 不建议在调用 fs.open()、 fs.readFile() 或 fs.writeFile() 之前使用 fs.stat() 检查文件是否存在。 而是应该直接打开、读取或写入文件，如果文件不可用则处理引发的错误。
        - 要检查文件是否存在但随后并不对其进行操作，则建议使用 fs.access()。
    - #### 4.fs.rename() 重命名
        ```js
        const fs = require('fs')

        fs.rename('./text', 'text.txt', err => {
            if (err) throw err;

            console.log('重命名成功')
        })
        ```
    - #### 5.fs.unlink() 删除文件
        ```js
        const fs = require('fs')

        fs.unlink('./text.txt', (err) => {
            if (err) throw err;
            console.log('删除成功')
        })
        ```
    - #### 6.fs.readdir() 读取文件目录
        ```js
        const fs = require('fs')

        fs.readdir('./', (err, files) => {   // files 是目录下文件名
            if (err) throw err;

            console.log(files)
        })
        ```
    - #### 7.fs.mkdir() 创建目录
        ```js
        const fs = require('fs')

        fs.mkdir('test', err => {
            if (err) throw err;

            console.log('创建成功')
        })
        ```
    - #### 8.fs.rmdir() 删除文件夹
        ```js
        const fs = require('fs')

        fs.rmdir('./test', err => {})
        ```
    - #### 9.fs.watch() 监听
        - ```fs.watch()``` 是监听目录，```fs.watchFile()``` 是监听某一个文件
        - 这个 watch 就是 webpack 里面的 watch，用于监听某目录下的文件是否有改动 (增删改)，经常**被用于做本地构建**
        ```js
        const fs = require('fs')

        fs.watch('./', {recursive: true}, (eventType, filename) => {
            // 参数：目录path，是否递归(true则监听目录下的所有子文件夹)，回调函数里 改动类型(增删改)，被改动的文件名
            console.log(eventType, filename)
        })
        ```
    - #### 10.fs.readStream() 
        - 什么是 Stream ？
            - 我们一般翻译成 "流"
            - Stream 是有方向的数据。
            - 两个关键点：一有方向，二数据。
            - 从一个文件，流向另一个文件，流的东西是什么呢？就是数据。
        - 在过去，我们操作文件，都是把数据存在内存中，然后再进行操作。
        - 但是现在，除了可以放在内存中，我们还以把数据通过流的方式，来操作。
        - **就像家里的自来水管一样，数据一边流出来，一边给你使用，生产一点就给你使用一点。**而过去就类似于，要先把东西都存在内存中，然后才可以操作。但是现在有了流这种方式，就有更多一种的选择了。
        - Stream 流 的优势
            - 流 在有些场景下，优势是非常明显的。
            - 比如说，看电影，最开始电脑内存只有 512M 的时候，我们也可以看 2G 的电影，为什么？理论上来说，电影要想读的话，要把整个都放进内存中，而你内存只有 512M 我怎么看？
            - 这种情况下，我如果用了 stream 就好解决了。我一点点读，然后往内存里 一点点放，放给你一点点看，我们是一点点流嘛！就好像，我一个 3升 的水桶，怎么用来装 5升 的水呢？我一点点给你装进去，你那边一点点消费掉，总共流过了 5升 水，但不会同时给你 5升。
        ```js
        const fs = require('fs')

        const rs = fs.createReadStream('./text.txt')  // 创建一个可读流。数据，就是该文件的内容

        rs.pipe(process.stdout)     // process.stdout 输出到控制台, 也就是命令行里
        // 方向。所有的 stream 都有 pipe() 方法，意思是往谁里面倒
        ```
    - #### 11.fs.writeStream()
        - writeStream() 也不是我放在内存中，一次性都给你了；而是，我生产一点，就写给你一点
        ```js
        const fs = require('fs')

        const ws = fs.createWriteStream('./text.txt');  // 创建一个可写流

        // 下面我们模拟，生产特别慢，每 200ms 才能生产一个数据以供消费
        const tid = setInterval(() => {
            const num = parseInt(Math.random() * 10)
            console.log(num)
            if (num < 8) {
                ws.write(num + '')  // ws.write 往里面写入东西。转字符串
            } else {
                clearInterval(tid)
                ws.end()        // 写完了
            }
        }, 200)

        ws.on('finish', () => {     // 监听 写入结束事件 finish
            console.log('写完了')
        })
        ```
    - #### 12.解决地狱回调的问题
        - 在上面，我的写的逻辑都很简单，只是一个异步操作而已。
        - 在复杂场景里面，都是一个异步里面，调另外一个异步，然后再调另外一个异步... 无限调异步下去，就形成了 **回调地狱**。代码可读性非常差，如：
            ```js
            () => {
                () => {
                    () => {
                        // ...
                    }
                }
            }
            ```
        - 但是，现在我们可以通过 Promise 来解决这个问题了。
        - **Promise 使得异步流程可以写成同步流程**, 增加代码可读性
            ```js
            const fs = require('fs')
            const promisify = require('util').promisify

            const read = promisify(fs.readFile)  // fs.readFile(filePath, callback) 是一个异步操作，这里我们把它改成了 promise

            read('./text.txt').then(data => {
                console.log(data.toString())
            }).catch(err => {
                console.log(err)
            })
            ```
        - 我们还可以通过，Async 让它变得更简单
            ```js
            const fs = require('fs')
            const promisify = require('util').promisify

            const read = promisify(fs.readFile)

            async function test(){
                try{
                    const content = await read('./text.txt')
                    console.log(content.toString())
                } catch (err) {
                    console.log(err)
                }
            }

            test()
            ```
            -当然，这里看起来上面的例子 有点小题大作了(并没有看起来变得简单)，但是，如果在更复杂的逻辑里面，上面的方法就能让代码变得的简单了

## 第5章 项目初始化
- ### 5-1 .gitignore
    - 项目开始之前了解一下项目初始化知识，做开实战项目开始准备
        - 1.gitignore：只上传有必要的代码到 github
        - 2.npmignore：只上传有用的内容到 npm
        - 3.editorconfig：统一代码风格
    - #### 1.gitignore
        - .gitignore 是什么？
            - 当向 github 上传代码时，自动忽略掉某些文件，不上传，这些忽略规则被写在 .gitignore 中
        - [.gitignore 官方文档](https://git-scm.com/docs/gitignore)
        - 语法规则
            - 前面 ``` / ``` 代表项目根目录
            - 最后加 ``` / ``` 代表是目录
            - ``` ! ``` 代表取反，不忽略该文件
                - 使用场景：忽略掉整个文件夹，但是不忽略其中的某一个文件
            - ``` * ``` 代表任意个字符
            - ``` ? ``` 匹配任意一个字符
            - ``` ** ``` 匹配多级目录
            - ``` # ``` 注释
        - EXAMPLES
            ```.gitignore
            logs
            *.logs
            npm-debug.log*
            node_modules/
            *.swp
            .idea/
            .DS_Store

            # 忽略掉整个文件夹，但是不忽略其中的某一类的文件
            build/
            !build/**/index.js
            ```
    - #### 2.npmignore
        - .npmignore 是什么？
            - 上传 NPM 时，会自动忽略掉的文件 的配置文件。
        - [.npmignore 官方文档](https://docs.npmjs.com/misc/developers#keeping-files-out-of-your-package)
        - 注意：
            - 如果项目中没有 .npmignore ，但是有 .gitignore ，那么他会自动使用 .gitignore
        - EXAMPLES
            ```
            node_modules
            src
            test
            ```
        - 默认情况下，将忽略以下路径和文件，因此无需.npmignore显式添加它们：
            ```
            .*.swp
            ._*
            .DS_Store
            .git
            .hg
            .npmrc
            .lock-wscript
            .svn
            .wafpickle-*
            config.gypi
            CVS
            npm-debug.log
            ```
        - 以下路径和文件永远不会被忽略，因此添加它们 .npmignore是没有意义的：
            ```
            package.json
            README （及其变种）
            CHANGELOG （及其变种）
            LICENSE / LICENCE
            ```
            
    - #### 3.editorconfig  统一代码风格
        - .editconfig 是什么?
            - 「官方解释」
                - EditorConfig有助于为跨越各种编辑器和IDE的同一项目的多个开发人员维护一致的编码样式。
            - 很多时候我们需要跨团队合作，或者一个项目大家都贡献代码
            - 由于大家 编辑器都不一样，代码风格不一样。如代码缩进，有人用 Tab，有人用4个空格，有人用2个空格
            - 也可能，每个项目的代码风格要求不一样，在切换项目开发时，如果每次都要改编辑器的代码风格，就会很烦
            - .editconfig 就是来解决这些问题的
        - [EditorConfig 官网](https://editorconfig.org/)
        - EXAMPLES
            - 下面是一个示例 .editorconfig 文件设置Python和JavaScript文件的行尾和缩进样式。
            ```.editorconfig
            # EditorConfig is awesome: https://EditorConfig.org

            # top-most EditorConfig file
            # 可以做每个文件夹都写一个 .editorconfig，但是如果 root = true 即表示我这里是顶层了，不再往上找了，.editorconfig 文件合并也合并到我这里为止 (类似于CSS的覆盖关系)
            root = true

            # Unix-style newlines with a newline ending every file
            [*]                             # 所有文件都匹配
            end_of_line = lf                # Unix 还是 Windows 的回车
            insert_final_newline = true     # 最后一行回车

            # Matches multiple files with brace expansion notation
            # Set default charset
            [*.{js,py}]
            charset = utf-8
            # .js .py 都要用 utf-8 编码写

            # 4 space indentation
            [*.py]
            indent_style = space
            indent_size = 4
            # 缩进要用4个空格

            # Tab indentation (no size specified)
            [Makefile]
            indent_style = tab
            # Makefile 文件缩进用 tab

            # Indentation override for all JS under lib directory
            [lib/**.js]
            indent_style = space
            indent_size = 2
            # lib 文件夹下的所有 js 文件，缩进要用2个空格
            trim_trailing_whitespace：true # 删除换行符前面的任何空白字符

            # Matches the exact files either package.json or .travis.yml
            [{package.json,.travis.yml}]
            indent_style = space
            indent_size = 2
            ```
            - .editorconfig 后面写的会覆盖前面写的，类似于css 的覆盖关系

- ### 5-2 ESLint
    - 在这个文章里面 我也有讲到ESLint 可以参照阅读 [《5-6 EsLint 在 Webpack 中的配置》](https://github.com/946629031/hello-webpack4#5-6-eslint-%E5%9C%A8-webpack-%E4%B8%AD%E7%9A%84%E9%85%8D%E7%BD%AE)
    - 什么是 ESLint ?
        - [官方解释 什么是 ESLint ?](https://eslint.cn/docs/about/)
    - [eslint 配置规则 官方文档](https://eslint.cn/docs/user-guide/configuring)
        - Configuring Rules
            > ESLint 附带有大量的规则。你可以使用注释或配置文件修改你项目中要使用的规则。要改变一个规则设置，你必须将规则 ID 设置为下列值之一：
            - "off" 或 0 - 关闭规则
            - "warn" 或 1 - 开启规则，使用警告级别的错误：warn (不会导致程序退出)
            - "error" 或 2 - 开启规则，使用错误级别的错误：error (当被触发的时候，程序会退出)
    - ESLint 示例
        ```js
        // .eslintrc.js
        module.exports = {
            "extends": "eslint:recommended",  // 继承 使用 eslint 的推荐配置
            "root": true, // 跟上面 .editorConfig 一样，告诉它这里是 eslint 配置文件的根目录，不再往外层找
            "rules": {    // 对上面继承来的配置规则，做自己修改
                "no-console": ["error", {   // 不允许使用 console, 如果使用了 报错等级 error
                    "allow": ["warn", "error", "info"]    // 但是允许使用 console.warn ... 等 这三个
                }]
            },
            "parser": "babel-eslint",   // 指定语法解析器。它默认有自己的解析器
            "parserOptions": {          // 解析选项
                "ecmaVersion": 6,       // 指定 ECMA 6 版本
                "sourceType": "script"  // 指定源码类型，可选项"script"和"module"，默认是"script"
            },
            "globals": {  // 执行代码时脚本需要访问的额外全局变量
                "window": true  // 允许全局使用 window
            },
            "env": {      // 指定脚本的运行环境
                "browser": false,
                "node": true,
                "es6": true,
            }
        }
        ```
    - 临时取消 ESLint 的规则警告，让 ESLint 在这一代码块中**失效**
        ```js
        /* eslint-disable */

        alert('foo');

        /* eslint-enable */
        ```
        - 也可以 指定取消哪些 ESLint 规则
            ```js
            /* eslint-disable no-alert, no-console */

            alert('foo');
            console.log('bar');

            /* eslint-enable no-alert, no-console */
            ```
        - 取消一行的 ESLint 警告
            ```js
            console.log(123)    // eslint-disable-line

            // eslint-disable-next-line
            console.log(123)
            ```
    - #### 使用 命令行 操作 ESLint
        - 全局安装ESLint ```npm install eslint -g```
        - ```eslint --init``` 初始化生成 .eslintrc.js 配置文件
        - ```eslint --fix [file.js][dir]``` 自动修复
            - 如 ```eslint --fix src```, 自动修复src目录下的所有文件
    - #### 通过 NPM Scripts 来操作 ESLint
        ```js
        // package.json
        {
            "scripts": {
                "lint": "eslint .",   // 使用 eslint 验证当前目录下的所有文件
                "fix"： "eslint --fix ." // 自动修复 eslint 能识别的错误
            }
        }
        ```
        - 然后通过 命令行 ```npm run lint``` 或者 ```npm run fix``` 即可
    - #### 如果不符合 ESLint 规范，则强制不能提交
        - 可以通过 git 钩子，在 ```git commit``` 之前 就会执行这个命令，如果错了的话 就不允许提交
        - **pre-commit**
            - pre-commit 是什么？
                - [pre-commit 官网文档](https://www.npmjs.com/package/pre-commit)
                - 或者也可以通过 pre-commit，它会自动帮我们配置一个 git 钩子
                - 在 ```git commit``` 之前 就会执行这个命令，如果命令不通过的话 就不允许提交
            - pre-commit 怎么用？
                - 安装 ```npm i -D pre-commit```, 还需要安装 ```npm i -D eslint babel-eslint```
                - 配置
                    ```js
                    // package.json
                    {
                        "scripts": {
                            "lint": "eslint .",   // 使用 eslint 验证当前目录下的所有文件
                            "fix"： "eslint --fix ." // 自动修复 eslint 能识别的错误
                        },
                        "pre-commit": [
                            "fix",  // 先执行 自动修复
                            "lint"  // 然后再 验证是否符合 eslint 规则
                        ]
                    }
                    ```
                - 这时候再执行 ```git add .``` ```git commit -m 'test'```
                    - 在执行 commit 之后，如果有 eslint 报错，就会阻止提交代码了
            - ```.eslintignore```
                - 忽略掉某些文件，不做 eslint 规则校验。
                    - 如，build 构建打包后的代码，已经被压缩过了，所以在做 eslint 校验的时候 是肯定会报错的，这种就不需要做校验了
                ```js
                // .eslintignore
                build/
                node_modules
                test
                ```

## VSCode 中 Node.js 语法 提示插件
- ```npm i @types/node```
- ```npm install -g typings```
    - ```typings --version``` 测试是否安装成功
- ```typings install dt~node --global --save```
- 安装成功！！ 可以去 编辑器里测试一下了。

- 2.通过上面的命令，typings这个包就下载下来了，
    - 然后我们到项目开发目录，打开终端，输入：```typings init```
    - 这时当前目录下会出现一个typings.json的文件，这个文件就是typing的配置文件, 
    - 类似npm的package.json 然后在改目录命令窗口下输入以下命令，安装js插件的提示文件，如下：
    - ```typings install dt~node --global--save``` node 提示
    - ```typings install dt~jquery --global --save``` jquery 提示
    - （–global：代表全局文件，有些包必须得加上这个参数才行）
    - （–save ：表示将此次的安装信息记录到上面讲的typings.json中)
- [参考](https://www.jianshu.com/p/bc6220792e80)

## 第6章 静态资源服务器
>
> 第一个实战项目，自己实现一个静态资源服务器，主要内容包括
> - 1.HTTP 协议
> - 2.基础API应用
> - 3.回调地狱解决方案 npm 包版本 & 发布
> 


> - 实战项目1 - 「静态资源服务器」
>     - 要求：
>         - NodeJS
>         - 在任意目录下，执行命令，即可把该目录变成 静态资源服务器 的根目录
>         - 通过 URL 即可访问里面的文件夹 和文件内容
>         - 如 anywhere, 这是业界比较出色的实现方案


- ### 6-1 静态资源服务器 01
    - [NodeJS 创建http服务器](https://nodejs.org/en/docs/guides/getting-started-guide/)
    ```js
    // app.js
    const http = require('http');

    const hostname = '127.0.0.1';
    const post = 3000;

    const server = http.createServer((req, res) => {
        res.statusCode = 200;
        res.setHeader('Content-Type', 'text/plain');    // text/plain 普通文本
        res.end('Hello World\n');   // req, res 都是可写流。如果要写多条信息，就要 .write() .write() ... .end()
    });

    server.listen(port, hostname, () => {
        console.log(`Server running at http://${hostname}:${port}/`);
    })
    ```
    - 上面写完后，执行 ```node run app.js``` 即可启动 http 服务了

- ### 6-2 使用 supervisor 监听目录，如果文件有变化 则自动重启服务器
    ```js
    // app.js
    const http = require('http');

    const hostname = '127.0.0.1';
    const port = 3000;

    const server = http.createServer((req, res) => {
        res.statusCode = 200;
        res.setHeader('Content-Type', 'text/html');     // 将内容显示为 HTML

        res.write('<html>');
        res.write('<body>');
        res.write('Hello HTTP !');
        res.write('</body>');
        res.end('</html>');
    });

    server.listen(port, hostname, () => {
        console.log(`Server running at http://${hostname}:${port}/`);
    })
    ```
    - 存在的问题
        - 像上面这例子，我们在开发过程中，如果修改了其中的内容，则需要不断的 手动重启服务器 ```node run app.js```，显得非常麻烦。
        - 那么有没有什么方法，可以让他 **自动监听目录下的文件，如果文件有变化，则自动重启服务** 呢？
        - 可以通过 **supervisor** , 来监听
    - #### supervisor 使用
        - 安装 ```npm i -g supervisor```
        - ```supervisor app.js``` 通过 supervisor 启动服务
        - 即可，自动监听目录下的文件，如果文件有变化，则自动重启服务


- ### 6-3 实现 静态资源服务器
    - 当用户请求来了一个 URL，我们要判断 URL 想要访问的地址
        - 如果是个文件夹 我们就返回 文件夹的文件列表；
        - 如果请求的是文件，我们就返回文件内容。
        - 那么 这个需求，我们要怎么实现呢？
    - 总体思路：
        - 1.获取 用户请求的路径 是什么
            - 用户请求的东西，都放在 req 中。可以启动 Chrome调试工具 查看 req 里面的内容
        - 2.根据用户请求的 url，判断他要访问的是 文件 还是文件夹。通过 ```fs.stat()```
    ```js
    // app.js
    const http = require('http');
    const path = require('path');
    const fs = require('fs');
    const conf = require('./defaultConfig.js');

    const server = http.createServer((req, res) => {
        const url = req.url;    // 获取用户请求的 url
        const filePath = path.join(conf.root, url);
        // const filePath = path.join(conf.root, req.url);   // 上面两句可以合成并成一句

        fs.stat(filePath, (err, stats) => {
            if (err) {  // if err 则表示文件不存在，返回404
                res.statusCode = 404;
                res.setHeader('Content-Type', 'text/plain');
                res.end(`${filePath} is not a directory or file`);
                return;
            }

            // 如果不是404，则判断是文件还是目录
            if (stats.isFile()) {   // 如果是文件，就返回文件内容
                res.statusCode = 200;
                res.setHeader('Content-Type', 'text/plain');    // 文件内容通过文本形式返回

                fs.createReadStream(filePath).pipe(res);   // 将文件内容 通过流的形式返回给客户端
                // fs.readFile(filePath, (err, data) => { res.end(data) })
                // 虽然上面一句，也可以通过 fs.readFile() 方法写，也是异步读取的
                // 但是 fs.readFile() 是超级慢的，他要把所有的内容都读出来，才能往 response里面放，返回给客户端。响应速度是超级慢的

            } else if (stats.isDirectory()) {   // 如果是文件夹，就返回文件列表
                fs.readdir(filePath, (err, files) => {
                    res.statusCode = 200;
                    res.setHeader('Content-Type', 'text/plain');
                    res.end(files.join(','));   // files 是文件列表的数组，文件名通过 , 隔开
                })
            }
        })
    });

    server.listen(port, hostname, () => {
        console.log(`Server running at http://${hostname}:${port}/`);
    })
    ```
    ```js
    // defaultConfig.js
    module.exports = {
        root: process.cwd(),    // 获取当前文件夹路径，执行 node 命令所在的文件夹
        hostname: '127.0.0.1',
        port: 9527
    }
    ```
    - 到这里，基本功能已经实现了
- ### 6-4 promisify 化 静态资源服务器
    - 在上面 6-3 的代码中，我们用了很多的回调
    - 所以，我们可以用 promisify 来把 回调去掉。**Promise 使得异步流程可以写成同步流程, 增加代码可读性**
    ```js
    const http = require('http');
    const path = require('path');
    const fs = require('fs');

    const promisify = require('util').promisify;    // 引入 promisify
    const stat = promisify(fs.stat);                // 异步函数 promisify 化
    const readdir = promisify(fs.readdir);          // 异步函数 promisify 化

    const hostname = '127.0.0.1';
    const port = 9556;
    const root = __dirname;
    // const root = process.cwd();

    const server = http.createServer((req, res) => {
        const filePath = path.join(root, req.url);

        handle(req, res, filePath);
    })

    server.listen(port, hostname, () => {
        console.log(`Server is running at http://${hostname}:${port}/`);
    })

    async function handle(req, res, filePath){
        try{
            const stats = await stat(filePath);     // 因为 promisify 后，要 await 异步函数回调，所以才把主逻辑抽离到 async function 中

            if (stats.isFile()) {
                res.statusCode = 200;
                res.setHeader('Content-Type', 'text/plain');
                fs.createReadStream(filePath).pipe(res);
            } else if (stats.isDirectory()) {
                const files = await readdir(filePath);    // 这里如果有错误，统一让它抛到外层的 try catch 去捕获异常 就好了，这里不做处理了
                res.statusCode = 200;
                res.setHeader('Content-Type', 'text/plain');
                res.end(files.join(','));
            }
        } catch (err) {
            console.error(err);

            res.statusCode = 404;
            res.setHeader('Content-Type', 'text/plain');
            res.end(`${filePath} is not a directory or file \n ${err}`);    // 将错误输出到浏览器
        }
    }
    ```
    - **注意**：
        - 将错误输出到浏览器，虽然方便了我们调试，但是也可能会暴露 堆栈信息，别有用心的人 能对此分析 并加以利用，所以这是非常危险的。
        - 所以，我们可以做个判断，在开发模式下 才将错误输出到浏览器
- ### 6-5 使用 HTML模板 生成动态网页
    - 存在的问题：
        - 到目前为止，服务器端的功能是实现了，但是在浏览器上 并不能通过点击 来切换目录，只是一些 纯文本的东西。
        - 那么怎么才能解决这个问题呢？ 拼接字符串来实现 html 是可以的，但是维护性比较差。所以我们可以通过 **[handlebars](https://handlebarsjs.com/) web模板引擎** 来解决这个问题
    - 1.安装 ```npm i handlebars```
    - 2.通过 handlebars HTML模板 生成动态网页
    ```js
    const http = require('http');
    const Handlebars = require('handlebars');       // 引入 handlebars
    const path = require('path');
    const fs = require('fs');
    const colors = require('colors');

    const promisify = require('util').promisify;
    const stat = promisify(fs.stat);
    const readdir = promisify(fs.readdir);

    const hostname = '127.0.0.1';
    const port = 9556;
    const root = __dirname;
    // const root = process.cwd();

    const tplPath = path.join(__dirname, './template/dir.html');
    const source = fs.readFileSync(tplPath);    // 读取模板文件
    // 为什么用同步读取？  1.下面的逻辑要正常工作，需要这一步为前提 
    // 2.只需要读取一次即可，之后直接在内存中读取即可，因为每次的处理 模板文件都不变
    const template = Handlebars.compile(source.toString());   // 生成 template

    const server = http.createServer((req, res) => {
        const filePath = path.join(root, req.url);
        handle(req, res, filePath);
    })

    server.listen(port, hostname, () => {
        console.log(`Server is running at http://${hostname}:${port}/`);
    })

    async function handle(req, res, filePath){
        try{
            const stats = await stat(filePath);

            if (stats.isFile()) {
                res.statusCode = 200;
                res.setHeader('Content-Type', 'text/plain');
                fs.createReadStream(filePath).pipe(res);
            } else if (stats.isDirectory()) {
                const files = await readdir(filePath);
                res.statusCode = 200;
                res.setHeader('Content-Type', 'text/html');
                // res.end(files.join(','));

                const dir = path.relative(root, filePath);
                const data = {      // 制作 template 数据
                    title: path.basename(filePath),
                    files,
                    dir: dir ? `/${dir}` : ''
                }
                console.log('filePath', filePath.green)     // 这里的 .green 是利用 colors库 使得输出到 命令行里的字体变色
                console.log('dir', dir.green)
                res.end(template(data));    // 将数据和模板 返回给客户端
            }
        } catch (err) {
            // console.error(err);
            res.statusCode = 404;
            res.setHeader('Content-Type', 'text/plain');
            res.end(`${filePath} is not a directory or file \n ${err}`);
        }
    }
    ```
    ```html
    // ./template/dir.html  模板文件

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>{{title}}</title>
    </head>
    <body>
        
    {{#each files}}
        <a href="{{../dir}}/{{this}}">{{this}}</a>
    {{/each}}


    <style>
        a{ display: block; }
    </style>
    </body>
    </html>
    ```
- ### 6-7 自动传递 Content-Type && 根据不同文件类型显示不同icon
    - 在浏览器里，加载到的资源 的 Response Headers 里面可以查看 该资源的 Content-Type (文件类型)
    - 存在的问题：
        - 但是，在我们上面的例子中，if isFile() 无论什么情况都是返回 text/plain (普通文本) 类型的
        - 无论点击什么，都是返回文本，不能做到 点击图片显示图片；点击音视频文件，播放该文件
        - 那么，有没有什么办法能让他智能一点，自动识别文件类型，然后返回相应的 Content-Type 呢？ 
        - 如果能识别文件类型，我们还可以 根据不同文件类型显示不同icon，让用户体验更好
    - 这种对于关系 被称为 MINE 和 MIME type 的对应关系
        ```js
        // mime.js
        const path = require('path');

        const mimeTypes = {        // 部分 MINE 和 MIME type 的对应关系
            'css': 'text/css',
            'gif': 'image/gif',
            'html': 'text/html',
            'ico': 'image/x-icon',
            'jpeg': 'image/jpeg',
            'jpg': 'image/jpeg',
            'js': 'text/javascript',
            'json': 'application/json',
            'pdf': 'application/pdf',
            'png': 'image/png',
            'svg': 'image/svg+xml',
            'swf': 'application/x-shockwave-flash',
            'tiff': 'image/tiff',
            'txt': 'text/plain',
            'wav': 'audio/x-wav',
            'wma': 'audio/x-ms-wma',
            'wmv': 'audio/x-ms-wmv',
            'xml': 'text/xml',
        }

        module.exports = (filePath) => {
            let ext = path.extname(filePath)
            .split('.')     // 如 jquery.min.JS 有可能返回的是 ".min.JS"
            .pop()
            .toLowerCase();
            
            
            if (!ext) {   // 如果文件没有 拓展名
                ext = filePath;
            }
            // console.log('ext', ext)

            return mimeTypes[ext] || mimeTypes['txt'];
            // 如果能读取到，则返回对应 mimeTypes, 否则都按照 普通文本返回
        }
        ```
        ```js
        // 6-5.handlebars_static_server.js
        const http = require('http');
        const Handlebars = require('handlebars');
        const path = require('path');
        const fs = require('fs');
        const colors = require('colors');
        const mime = require('./6-7.mime');     // 引入 mime.js 处理文件

        const promisify = require('util').promisify;
        const stat = promisify(fs.stat);
        const readdir = promisify(fs.readdir);

        const hostname = '127.0.0.1';
        const port = 9556;
        const root = __dirname;

        const tplPath = path.join(__dirname, './template/dir.html');
        const source = fs.readFileSync(tplPath);
        const template = Handlebars.compile(source.toString());

        const server = http.createServer((req, res) => {
            const filePath = path.join(root, req.url);
            handle(req, res, filePath);
        })

        server.listen(port, hostname, () => {
            console.log(`Server is running at http://${hostname}:${port}/`);
        })

        async function handle(req, res, filePath){
            try{
                const stats = await stat(filePath);

                if (stats.isFile()) {
                    res.statusCode = 200;
                    res.setHeader('Content-Type', mime(filePath));    // 使用 mime.js 的处理结果，自动识别
                    fs.createReadStream(filePath).pipe(res);
                } else if (stats.isDirectory()) {
                    const files = await readdir(filePath);
                    res.statusCode = 200;
                    res.setHeader('Content-Type', 'text/html');

                    const dir = path.relative(root, filePath);
                    const data = {      // 制作 template 数据
                        title: path.basename(filePath),
                        files,
                        dir: dir ? `/${dir}` : ''
                    }
                    res.end(template(data));    // 将数据和模板 返回给客户端
                }
            } catch (err) {
                res.statusCode = 404;
                res.setHeader('Content-Type', 'text/plain');
                res.end(`${filePath} is not a directory or file`);
            }
        }
        ```
    - 到这里，自动传递 Content-Type 就完成了。
    - 下面讲解，怎么 **根据不同文件类型显示不同icon**
    ```js
    const http = require('http');
    const Handlebars = require('handlebars');
    const path = require('path');
    const fs = require('fs');
    const colors = require('colors');
    const mime = require('./6-7.mime');

    const promisify = require('util').promisify;
    const stat = promisify(fs.stat);
    const readdir = promisify(fs.readdir);

    const hostname = '127.0.0.1';
    const port = 9556;
    const root = __dirname;

    const tplPath = path.join(__dirname, './template/dir.html');
    const source = fs.readFileSync(tplPath);    // 读取模板文件
    const template = Handlebars.compile(source.toString());   // 生成 template

    const server = http.createServer((req, res) => {
        const filePath = path.join(root, req.url);
        handle(req, res, filePath);
    })

    server.listen(port, hostname, () => {
        console.log(`Server is running at http://${hostname}:${port}/`);
    })

    async function handle(req, res, filePath){
        try{
            const stats = await stat(filePath);

            if (stats.isFile()) {
                res.statusCode = 200;
                res.setHeader('Content-Type', mime(filePath));
                fs.createReadStream(filePath).pipe(res);
            } else if (stats.isDirectory()) {
                const files = await readdir(filePath);
                res.statusCode = 200;
                res.setHeader('Content-Type', 'text/html');

                const dir = path.relative(root, filePath);
                const data = {      // 制作 template 数据
                    title: path.basename(filePath),
                    dir: dir ? `/${dir}` : '',
                    files: files.map(file => {    // 求每个文件的 文件类型
                        return {
                            file,
                            icon: mime(file)
                        }
                    })
                }
                console.log('filePath', filePath.green)
                console.log('dir', dir.green)
                res.end(template(data));    // 将数据和模板 返回给客户端
            }
        } catch (err) {
            // console.error(err);

            res.statusCode = 404;
            res.setHeader('Content-Type', 'text/plain');
            res.end(`${filePath} is not a directory or file`);
        }
    }
    ```
    ```html
    // ./template/dir.html  模板文件

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>{{title}}</title>
    </head>
    <body>
        
    {{#each files}}
        <a href="{{../dir}}/{{file}}">【{{icon}}】{{file}}</a>
    {{/each}}

    <style>
        a{ display: block; }
    </style>
    </body>
    </html>
    ```
    - 执行后，用浏览器访问，得到下面结果
    ```
    // 执行结果
    【text/javascript】02-cusmod.js
    【text/javascript】03-require.js
    【text/javascript】04-require_cache.js
    【text/javascript】05-main.js
    ...
    ```
    - 写到这里，那么如何把 html 里的文件名，换成 图片呢？
    - 在 mime.js 里面，写 每个图片的地址 即可，然后在 html 模板里面去读取该 图片地址
    ```js
    // mime.js
    const path = require('path');

    const mimeTypes = {        // 部分 MINE 和 MIME type 的对应关系
        'css': {
            text: 'text/css',
            icon: 'http://image-location'  // 这里写图片路径
        },
        'gif': 'image/gif',
        'html': 'text/html',
        'ico': 'image/x-icon',
        'jpeg': 'image/jpeg',
        'jpg': 'image/jpeg',
        'js': 'text/javascript',
        'json': 'application/json',
        'pdf': 'application/pdf',
        'png': 'image/png',
        'svg': 'image/svg+xml',
        'swf': 'application/x-shockwave-flash',
        'tiff': 'image/tiff',
        'txt': 'text/plain',
        'wav': 'audio/x-wav',
        'wma': 'audio/x-ms-wma',
        'wmv': 'audio/x-ms-wmv',
        'xml': 'text/xml',
    }

    module.exports = (filePath) => {
        let ext = path.extname(filePath)
        .split('.')     // 如 jquery.min.JS 有可能返回的是 ".min.JS"
        .pop()
        .toLowerCase();
        
        
        if (!ext) {   // 如果文件没有 拓展名
            ext = filePath;
        }
        // console.log('ext', ext)

        return mimeTypes[ext] || mimeTypes['txt'];
        // 如果能读取到，则返回对应 mimeTypes, 否则都按照 普通文本返回
    }
    ```
- ### 6-8 服务器 压缩文件 Content-Encoding 和 Accept-Encoding
    - 在网页中，打开 ```控制台 - Network - 选择文本文件(.html, .css, .md ... 等) - 在 Request Headers / Response Headers ```
    - 里面都有 ```Accept-Encoding: gzip, deflate, br``` 或者 ```Content-Encoding: gzip```
    - Accept-Encoding: gzip, deflate
        - 接受的编码格式
        - gzip, deflate 都是常见的压缩算法
    - 什么意思呢？
        - 了解 HTTP 协议的同学肯定知道，**Accept-Encoding** 是当我们的浏览器 向服务器发起文件请求 的时候，会告诉服务器 我支持的几种压缩方式，如 ```Accept-Encoding: gzip, deflate, br```
        - 意思是，随便你用这 3种方式中的任意一种 来压缩，我都能解压
        - 然后，服务器收到请求，一看你要的是 文本文件，而且支持 ```gzip, deflate, br``` 这三种压缩方式，然后 我就挑一种 我认为最好的方式压缩，**把 压缩后的内容进行传输**， 同时 我告诉浏览器 我用的哪种方式进行压缩，如 ```Content-Encoding: gzip```
        - 浏览器，接收到内容后，根据服务器给定 压缩算法 进行解压，然后呈现内容
        - **好处**： 减少了 HTTP 的传输量，这个在我们做**性能优化**的时候 是非常有用的
    - 下面，我们来实现一下 这种压缩方式
    ```js
    // compress.js
    const {createGzip, createDeflate} = require('zlib');

    module.exports = (rs, req, res) => {    // rs: 要被压缩的readStream, rq: 请求参数, res: respond
        const acceptEncoding = req.headers['accept-encoding'];    // 获取浏览器支持的压缩方式

        // 如果没有 acceptEncoding 或者 acceptEncoding 是服务器不支持的类型(这里只支持 gzip 和 deflate)
        if (!acceptEncoding || !acceptEncoding.match(/\b(gzip|deflate)\b/)) {
            return rs;
        } else if (acceptEncoding.match(/\bgzip\b/)){   // 优先使用 gzip，因为 gzip 压缩效果比较好
            res.setHeader('Content-Encoding', 'gzip');
            return rs.pipe(createGzip());   // 这样子就能把处理好的流 返回给我们
        } else if (acceptEncoding.match(/\bdeflate\b/)){
            res.setHeader('Content-Encoding', 'deflate');
            return rs.pipe(createDeflate());
        }
    }
    ```
    ```js
    // defaultConfig.js
    module.exports = {
        root: process.cwd(),
        hostname: '127.0.0.1',
        port: 9527,
        compress: /\.(html|js|css|md)/,      // 压缩文件的类型
    }
    ```
    ```js
    // 6-8.js
    const http = require('http');
    const path = require('path');
    const fs = require('fs');
    const handlebars = require('handlebars');
    const promisify = require('util').promisify;
    const stat = promisify(fs.stat);
    const readdir = promisify(fs.readdir);
    const mime = require('./mime');
    const compress = require('./compress');

    const config = require('./defaultConfig');
    const tplPath = path.join(__dirname, './template.html');
    const source = fs.readFileSync(tplPath);
    const template = handlebars.compile(source.toString());

    const server = http.createServer((req, res) => {
        const filePath = path.join(config.root, req.url);
        console.log('filePath', req.url)
        handle(req, res, filePath);
    });

    server.listen(config.port, config.hostname, ()=>{
        console.log(`Server is running ai http://${config.hostname}:${config.port}`);
    })

    async function handle (req, res, filePath) {
        try {
            const stats = await stat(filePath);

            if(stats.isFile()){
                res.statusCode = 200;
                res.setHeader('Content-Type', mime(filePath));

                // fs.createReadStream(filePath).pipe(res);     // 没压缩时是这样写的
                let rs = fs.createReadStream(filePath);
                if(filePath.match(config.comperss)){            // 如何匹配文件类型，就 调用压缩方法
                    rs = compress(rs, req, res);
                }
                rs.pipe(res);

            }else if(stats.isDirectory()){
                const files = await readdir(filePath);
                res.statusCode = 200;
                res.setHeader('Content-Type', 'text/html');
                // res.end(files.join());

                const dir = path.relative(config.root, filePath);
                console.log('root',config.root);
                console.log('filePath',filePath);
                console.log('dir', typeof(dir), dir);
                data = {
                    title: path.basename(filePath),
                    dir: dir ? `/${dir}` : '',
                    files: files.map(file => {
                        return {
                            file,
                            type: mime(file)
                        }
                    })
                };
                res.end(template(data));
            }
        } catch (err) {
            // console.log(err);

            res.statusCode = 404;
            res.setHeader('Content-Type', 'text/plain');
            res.end(`${filePath} is not a directory or file \n ${err}`);
            throw err;
        }
    }
    ```
    ```html
    // template.html

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>{{title}}</title>
    </head>
    <body>
        <ul>
            {{#each files}}
            <li><a href="{{../dir}}/{{file}}">【{{type}}】{{file}}</a></li>
            {{/each}}
        </ul>
        
    </body>
    </html>
    ```
    ```js
    // mime.js
    const path = require('path');

    const mimeTypes = {
        'css': 'text/css',
        'gif': 'image/gif',
        'html': 'text/html',
        'ico': 'image/x-icon',
        'jpeg': 'image/jpeg',
        'jpg': 'image/jpeg',
        'js': 'text/javascript',
        'json': 'application/json',
        'pdf': 'application/pdf',
        'png': 'image/png',
        'svg': 'image/svg+xml',
        'swf': 'application/x-shockwave-flash',
        'tiff': 'image/tiff',
        'txt': 'text/plain',
        'wav': 'audio/x-wav',
        'wma': 'audio/x-ms-wma',
        'wmv': 'audio/x-ms-wmv',
        'xml': 'text/xml',
    }

    module.exports = (filePath) => {
        let ext = path.extname(filePath).split('.').pop().toLowerCase();

        if(!ext){
            ext = filePath;
        }
        return mimeTypes[ext] || mimeTypes['txt'];
    }
    ```
    - 这时候，可以运行服务，然后点开浏览器，查看里面 Content-Encoding 和 Accept-Encoding，然后 **对照前后压缩效果**，快去试试吧 ^.^ ~


- ### 6-9 range 范围请求 / http tpc range
    - 什么是 range ?
        - range 中文译名 范围请求
        - 表示，当我们的客户端向服务器**发起请求，可以声明我请求的内容范围**，比如说 “是请求多少个字节 到 多少个字节”，而不是要求 一次性的要把所有的内容都拿回来，
        - 服务器得到了响应的请求之后，去读取到对应的文件，再读取到 对应的字节，就可以返回给客户端了。
    - 如何实现 range？ 只需三步
        - 1.在请求时候，```Request Headers``` 里面放一个 ```range``` 字段，用来声明我想要的范围。
            - ```range : bytes = [start]-[end]``` 从多少到多少
            - 也可以用逗号分隔，请求多个范围
            - 当然，如果请求的范围是不对的，比如说 start 是从 -10 开始，或者 end 超出了最大长度，或者 start 比 end 还大。
                - 这种情况下，服务器可以直接返回 200，然后把所有内容返回客户端
                - 也可以 返回 Status Code : 416，表示你请求的内容我不认识。因为 http 状态码中，4 开头的都是表示客户端错误
        - 2.在响应中，要加一个响应头 ```Response Headers``` ```Accept-Ranges:bytes```，表示说 我服务器可以处理的格式 为 bytes 字节
        - 3.在 ```Response Headers``` 中返回一个 ```Content-Range:bytes start-end/total```
            - 意思是 我返回给你的是字节，目前是从多少开始 到 多少结束，而且总量是多少
            - 也可以加个 ```Content-Length```，表示这次给了你的长度一共有多少
    ```js
    // 6-9.range.js
    module.exports = (totalSize, req, res) => {
        const range = req.headers['range'];
        if (!range){    // 如果拿不到 range
            return {code: 200};   // 表示处理不了，直接返回 200，正常的返回就好了。
        }

        const sizes = range.match(/bytes=(\d*)-(\d*)/);   // * 号表示 重复零次或多次，可以有 也可以没有
        // 用 match 如果匹配到的话，会返回长度为3 的数组，第一个表示匹配到的内容，第二个表示 第一个 \d* , 第三个表示 第二个 \d*
        const end = sizes[2] || totalSize - 1;
        const start = sizes[1] || totalSize - end;

        // 接下来我们要判断一些非法条件
        if (start > end || start < 0 || end > totalSize){
            return {code: 200};
        }

        // 下面是可以处理时，返回的结果
        res.setHeader('Accept-Ranges', 'bytes');
        res.setHeader('Content-Ranges', `bytes ${start}-${end}/${totalSize}`);
        res.setHeader('Content-length', end - start);
        return {
            code: 206,   // partial content 表示部分内容
            start: parseInt(start),
            end: parseInt(end)
        };
    }
    ```
    - 下面，我们回到上一节中的 6-8.js ，改写里面的代码
    ```js
    // 6-9.js
    const http = require('http');
    const path = require('path');
    const fs = require('fs');
    const handlebars = require('handlebars');
    const promisify = require('util').promisify;
    const stat = promisify(fs.stat);
    const readdir = promisify(fs.readdir);
    const mime = require('./mime');
    const compress = require('./compress');
    const range = require('./range');       // 第一步，引入 range

    const config = require('./defaultConfig');
    const tplPath = path.join(__dirname, './template.html');
    const source = fs.readFileSync(tplPath);
    const template = handlebars.compile(source.toString());

    const server = http.createServer((req, res) => {
        const filePath = path.join(config.root, req.url);
        console.log('filePath', req.url)
        handle(req, res, filePath);
    });

    server.listen(config.port, config.hostname, ()=>{
        console.log(`Server is running ai http://${config.hostname}:${config.port}`);
    })

    async function handle (req, res, filePath) {
        try {
            const stats = await stat(filePath);

            if(stats.isFile()){
                res.setHeader('Content-Type', mime(filePath));

                // fs.createReadStream(filePath).pipe(res);     // 没压缩时是这样写的
                
                // 6-8.js 原来的写法
                // let rs = fs.createReadStream(filePath);
                // if(filePath.match(config.comperss)){            // 如果匹配文件类型，就 调用压缩方法
                //     rs = compress(rs, req, res);
                // }
                // rs.pipe(res);

                // 现在使用 range 的写法，思路：改写成 读一部分，然后返回一部分的方法
                let rs;
                const {code, start, end} = range(stats.size, req, res);  // totalSize, req ,res
                if (code === 200){  // 如果 range 处理不了
                    res.statusCode = 200;
                    rs = fs.createReadStream(filePath);
                } else {    // 如果 range 能处理
                    res.statusCode = 206;
                    rs = fs.createReadStream(filePath, {start, end});  // 传入filePath, 从多少开始读，读到多少结束
                }
                if(filePath.match(config.comperss)){            // 下面还是走压缩的流程。如果匹配文件类型，就 调用压缩方法
                    rs = compress(rs, req, res);
                }
                rs.pipe(res);

            }else if(stats.isDirectory()){
                const files = await readdir(filePath);
                res.statusCode = 200;
                res.setHeader('Content-Type', 'text/html');
                // res.end(files.join());

                const dir = path.relative(config.root, filePath);
                console.log('root',config.root);
                console.log('filePath',filePath);
                console.log('dir', typeof(dir), dir);
                data = {
                    title: path.basename(filePath),
                    dir: dir ? `/${dir}` : '',
                    files: files.map(file => {
                        return {
                            file,
                            type: mime(file)
                        }
                    })
                };
                res.end(template(data));
            }
        } catch (err) {
            // console.log(err);

            res.statusCode = 404;
            res.setHeader('Content-Type', 'text/plain');
            res.end(`${filePath} is not a directory or file \n ${err}`);
            throw err;
        }
    }
    ```
    - 做完上面操作之后，可以使用 CURL 工具来分析一下
        - CURL 在平时分析网络的时候 还是挺好用的
        - 安装 CURL ```npm i curl -g```
        - 命令行输入 ```CURL http://127.0.0.1:9527/LINCENE``` , 意思是使用 CURL 分析访问 本地服务器的 LINCENE 文件的情况
            - ```CURL http://127.0.0.1:9527/LINCENE``` 是会拿到全量的内容
        - ```curl -I http://127.0.0.1:9527/app.js``` 只看 header
            - 返回
            ```
            TP/1.1 200 OK
            Content-Type: text/javascript
            Date: Tue, 09 Jul 2019 03:49:14 GMT
            Connection: keep-alive
            ```
        - ```curl -i http://127.0.0.1:9527/app.js``` 会把内容 和 header 都拿到
            - 返回
            ```
            TP/1.1 200 OK
            Content-Type: text/javascript
            Date: Tue, 09 Jul 2019 03:51:01 GMT
            Connection: keep-alive
            Transfer-Encoding: chunked

            const http = require('http')

            const hostname = '127.0.0.1';
            const port = 9563;

            const server = http.createServer((req, res) => {
                res.statusCode = 200;
                res.setHeader('Content-Type', 'text/html');
                res.write('<html>')
                res.write('<h1>Hello World !</h1>');
                res.end('<html>')
            });

            server.listen(port, hostname, () => {
                console.log(`Server running at http://${hostname}:${port}/`)
            })
            ```
        - **指定 range**,
            - ```curl -r 0-10 -i http://127.0.0.1:9527/app.js``` 指定 range 范围为 0-10
            - 返回
            ```
            TP/1.1 200 OK
            Content-Type: text/javascript
            Accept-Ranges: bytes
            Content-Ranges: bytes 0-10/415
            Content-length: 10
            Date: Tue, 09 Jul 2019 03:56:48 GMT
            Connection: keep-alive

            const http
            ```
        - 到这里，我们就能拿到一个文件的 **部分内容** 了


- ### 6-10 http 缓存
    - 在我们之前写的代码中，浏览器发起一个请求，请求到了服务器，服务器解析出来响应结果，然后把响应发回给浏览器
    - 但是 了解 http 的同学可能知道，http 协议中工作的时候会更加智能一些，尤其是针对静态资源的情况下，会极大程度的利用缓存
    - #### **缓存是什么？它是哪来的呢？它又是怎么工作的呢？**
        <!-- ![http-cache](https://github.com/946629031/hello-node.js/blob/master/img/2.http-cache.jpg) -->
        - 1.第一次访问 / 请求
            - 1.用户发起请求
            - 2.浏览器会检查本地是否存在缓存
            - 3.如果本地不存在缓存，第一次请求，没有缓存。那么我就会真的向服务器**发送请求**了
            - 4.然后，服务器会协商缓存内容，并且返回相应
            - 5.浏览器**协商了缓存内容，并拿到响应**之后，就会把当前的响应 **缓存到本地**，下次再发一样的请求时候，就会先用本地缓存了
        - 2. 第二次以上发请求
            - 1.**用户发起请求**
            - 2.**检查本地缓存**
            - 3.发现有缓存。如果有缓存了，是否就意味着 **不向服务器发送请求，而直接用缓存了呢？**
            - 4.也不是，它会检查一下缓存是否失效
                - 怎么知道缓存是否失效？
                    - 就是靠的 ```Response Headers``` 里面的 ```Expires 或 Cache-Control```
                    - 其中 ```Expires``` 是比较老的响应头了，现在基本都用 ```Cache-Control```
                    - ```Cache-Control``` 是什么意思？
                        - ```Cache-Control``` 一般写的是相对时间
                        - 我每次给你最新的内容之后，我可以规定一个时间，比如说："有的资源有效期是10年，有的1天，有点十分钟..."
                        - 在这段时间内，我的内容不会变
                        - 在规定时间内，你可以不用问我了，直接用本地缓存就行
                    - ```Expires``` 是什么？
                        - ```Expires``` 一般写的都是绝对时间, 如："在2020年1月1日前，你不用来问我"
                        - 但是这个问题比较大，因为根据不同的 时区，返回的时间 并不会那么的精确，所以现在一般都用 ```Cache-Control``` 这种相对时间
            - 5.如果缓存没有失效，就直接用缓存的内容，不再发送请求了，这样就快了非常多
            - 6.如果缓存失效了
                - 如果缓存失效了，是不是就要跟服务器 拿到完整的内容了呢？
                - 也不是。
                - 我是说，10分钟之内不用来问我，但是如果过了10分钟，你可以来问我一下
                - 我每次在 给你协商缓存，返回内容的时候，我会给你一个标识，可能是我这个文件的修改时间，也可能是我这个文件的哈希码
                - 我会告你我的 文件修改时间 或者 哈希码
                - 如果缓存失效了，你把 文件修改时间 或 哈希码 告诉我(服务器)
                    - 比如说，我告诉你，我是今天3点修改
                    - 下次你再发请求验证的时候，你告诉我 **你上次拿到的时间是什么**
                    - 我来验证一下，和我当前的修改时间是否一致
                        - 比如说，我的修改时间是 今天下午3点
                        - 当你6点发请求来的时候，你告诉我 "上次我拿到的修改时间是 今天下午3点，我来验证一下"
                        - 6-1 然后服务器 对比了一下，发现从 3点到6点 也没变过，我的修改时间还是下午3点，我没变过 **Server未改变**
                            - **更新一下缓存时间**，这次再往后推10分钟
                            - 并且返回一个 **304 状态码**
                            - 但是不返回内容，内容你就直接用缓存就好了
                        - 6-2 如果 发现时间不一样，就是 **Server改变**
                            - 那么我会告诉你，新的结果，新的修改时间了 或者 新的哈希码 **协商缓存，返回响应**
        - **总结：**
            - 这种工作方式，可以省掉非常多的传输情况，尤其是对于大量使用的 **静态资源**
            - 比如 一个 图片、logo ，在 网页A 或者 网页B 上使用，地址都是一样的，没必要每次都重新请求，请求完一次后 就直接用本地缓存就好了，像这种情况我们一般都会缓存 10年、20年
            - 那如果，在10年内 我真的换了 logo 怎么办？
                - 我们修改路径 或者 文件名就行了，文件名后加个v2。之前是v1版本，现在是v2版本，这样就会被当成了全新的资源了
    - #### 缓存 Header
        - ```Expires, Cache-Control```
            - 这两个都是用来判断本地缓存是否失效的
            - Expires，返回的是一个绝对时间。
            - Cache-Control，返回相对时间。相对你上一次访问 加上一个时间 (比如说10分钟)
            - Expires 由于不同时区，在同一个时刻发送请求，时间不一样...等等原因，用的人越来越少。现在大部分都用 Cache-Control
        - ```If-Modified-Since / Last-Modified```
            - 如果不是第一次发起的请求的时候 (第二次，第三次...)，就会把上次服务器告诉我的修改时间 放到 ```Request Headers``` 里面
            - If-Modified-Since，意思是："你从这个时间之后是否有修改过？"
            - 服务器拿到这个时间后一看，上次我给你的是下午3点，你现在来请求还是下午3点，嗯，没改过，你就用你本地缓存就好了
            - 如果改过的话，我就再给你一个最新的 ```Last-Modified```
        - ```If-None-Match / Etag```
            - 除了用修改时间 ```If-Modified-Since / Last-Modified```，我们还可以用这一对值，生成 Hash 值 (或者其它的类似的值，只要文件改变，该值就改变 的这种原理)
            - 服务器在每次 ```Response Headers``` 里面都会放 ```Etag```, 告诉你我最新的值
            - 每次客户端发送请求，都会在 ```Request Headers``` 里问 ```If-None-Match``` 是否匹配
        - **注意**
            - ```If-Modified-Since / Last-Modified``` 和 ```If-None-Match / Etag``` 这个选一个使用即可，因为他们产生的作用是一样的
    - 代码
        ```
        项目目录
        + |- /node_modules
        + |- /static
            |- template.html
        + |- /function
            |- cache.js
            |- compress.js
            |- defaultConfig.js
            |- mime.js
            |- range.js
        |- app.js
        |- package.json 
        ```
        ```js
        // 6-10.defaultConfig.js
        module.exports = {
            root: process.cwd(),
            hostname: '127.0.0.1',
            port: 9527,
            compress: /\.(html|js|css|md)/,
            cache: {
                maxAge: 600,   // 缓存有效时间。这里的意思是 缓存在600秒内有效
                expires: true, // 是否支持 expires 。一般情况下都不支持，现在只是为了测试
                cacheControl: true,
                lastModified: true,
                etag: true
            }
        }
        ```
        ```js
        // function/cache.js
        const {cache} = require('./defaultConfig');

        function refreshRes(stats, res) {
            const {maxAge, expires, cacheControl, lastModified, etag} = cache;

            if (expires) {          // 如果支持expires
                res.setHeader('Expires', (new Date(Date.now() + maxAge * 1000)).toUTCString());
                // 获取现在的时间 + 缓存有效期时间 (*1000 转为毫秒)，最后转成 UTC 时间
            }

            if (cacheControl) {     // 如果支持 cacheControl
                res.setHeader('Cache-Control', `public, max-age=${maxAge}`);
                // public 表示静态资源是共用的，再告诉你 max-age 缓存有效期是多少
            }

            if (lastModified) {
                res.setHeader('Last-Modified', stats.mtime.toUTCString());
                // 文件的上次修改时间，在 stats.mtime 可以取得。然后转 UTC 时间字符串
            }

            if (etag) {
                res.setHeader('ETag', `${stats.size}-${stats.mtime.toUTCString()}`);
                // 大小 - 修改时间
            }
        }

        module.exports = function isFresh(stats, req, res) {
            refreshRes(stats, res);

            // 下面来读一下浏览器发来的信息
            const lastModified = req.headers['if-modified-since'];
            const etag = req.headers['if-none-match'];

            // 如果客户端 这两个信息都没有给我们，就说明 很有可能是第一次请求
            if (!lastModified && !etag) {
                return false;
            }

            // 如果客户端给了我们 lastModified，并且跟我们 refreshRes() 设置的 lastModified 不一样，那就说明了 缓存失效了
            if (lastModified && lastModified !== res.getHeader('Last-Modified')) {
                return false;
            }
            
            // 如果 客户端给我们的 etag 也跟我们设置 etag 的不一样，说明 缓存失效了
            if (etag && etag !== res.getHeader('ETag')) {
                return false;
            }

            return true;    // 如果上面的 if 都不满足，则说明 缓存还是ok的，还在缓存有效期内
        }
        ```
        ```js
        // app.js
        const http = require('http');
        const path = require('path');
        const fs = require('fs');
        const handlebars = require('handlebars');
        const promisify = require('util').promisify;
        const stat = promisify(fs.stat);
        const readdir = promisify(fs.readdir);
        const mime = require('./function/mime');
        const compress = require('./function/compress');
        const range = require('./function/range');

        const config = require('./function/defaultConfig');
        const isFresh = require('./function/cache');     // 引入 isFresh 方法
        const tplPath = path.join(__dirname, './static/template.html');
        const source = fs.readFileSync(tplPath);
        const template = handlebars.compile(source.toString());

        const server = http.createServer((req, res) => {
            const filePath = path.join(config.root, req.url);
            // console.log('filePath',filePath);
            // const filePath = path.resolve(config.root, req.url);
            handle(req, res, filePath).catch(error=>console.log(error.message));
        });

        server.listen(config.port, config.hostname, ()=>{
            console.log(`Server is running at http://${config.hostname}:${config.port}`);
        })

        async function handle (req, res, filePath) {
            try {
                const stats = await stat(filePath);

                if(stats.isFile()){
                    res.statusCode = 200;
                    res.setHeader('Content-Type', mime(filePath));

                    // 在返回 200 前，拦截一下
                    let time444 = isFresh(stats, req, res);
                    if (isFresh(stats, req, res)) {
                        // 如果缓存是有效的
                        res.statusCode = 304;
                        res.end();      // 不返回内容了
                        return
                    }

                    // fs.createReadStream(filePath).pipe(res);     // 没压缩时是这样写的
                        
                    // 6-8.js 原来的写法
                    // let rs = fs.createReadStream(filePath);
                    // if(filePath.match(config.comperss)){            // 如果匹配文件类型，就 调用压缩方法
                    //     rs = compress(rs, req, res);
                    // }
                    // rs.pipe(res);

                    // 现在使用 range 的写法，思路：改写成 读一部分，然后返回一部分的方法
                    let rs;
                    const {code, start, end} = range(stats.size, req, res);  // totalSize, req ,res
                    if (code === 200){  // 如果 range 处理不了
                        rs = fs.createReadStream(filePath);
                    } else {    // 如果 range 能处理
                        rs = fs.createReadStream(filePath, {start, end});  // 传入filePath, 从多少开始读，读到多少结束
                    }
                    if(filePath.match(config.comperss)){            // 下面还是走压缩的流程。如果匹配文件类型，就 调用压缩方法
                        rs = compress(rs, req, res);
                    }
                    rs.pipe(res);

                }else if(stats.isDirectory()){
                    const files = await readdir(filePath);
                    res.statusCode = 200;
                    res.setHeader('Content-Type', 'text/html');
                    // res.end(files.join());

                    const dir = path.relative(config.root, filePath);
                    data = {
                        title: path.basename(filePath),
                        dir: dir ? `/${dir}` : '',
                        files: files.map(file => {
                            return {
                                file,
                                type: mime(file)
                            }
                        })
                    };
                    res.end(template(data));
                }
            } catch (err) {
                // console.log('filePath', filePath);

                res.statusCode = 404;
                res.setHeader('Content-Type', 'text/plain');
                res.end(`${filePath} is not a directory or file \n ${err}`);
                throw err;
            }
        }
        ```
        ```js
        // funciton/compress.js
        const {createGzip, createDeflate} = require('zlib');

        module.exports = (rs, req, res) => {    // rs: 要被压缩的readStream, rq: 请求参数, res: respond
            const acceptEncoding = req.headers['accept-encoding'];    // 获取浏览器支持的压缩方式

            // 如果没有 acceptEncoding 或者 acceptEncoding 是服务器不支持的类型(这里只支持 gzip 和 deflate)
            if (!acceptEncoding || !acceptEncoding.match(/\b(gzip|deflate)\b/)) {
                return rs;
            } else if (acceptEncoding.match(/\bgzip\b/)){   // 优先使用 gzip，因为 gzip 压缩效果比较好
                res.setHeader('Content-Encoding', 'gzip');
                return rs.pipe(createGzip());   // 这样子就能把处理好的流 返回给我们
            } else if (acceptEncoding.match(/\bdeflate\b/)){
                res.setHeader('Content-Encoding', 'deflate');
                return rs.pipe(createDeflate());
            }
        }
        ```
        ```js
        // function/mime.js
        const path = require('path');

        const mimeTypes = {
            'css': 'text/css',
            'gif': 'image/gif',
            'html': 'text/html',
            'ico': 'image/x-icon',
            'jpeg': 'image/jpeg',
            'jpg': 'image/jpeg',
            'js': 'text/javascript',
            'json': 'application/json',
            'pdf': 'application/pdf',
            'png': 'image/png',
            'svg': 'image/svg+xml',
            'swf': 'application/x-shockwave-flash',
            'tiff': 'image/tiff',
            'txt': 'text/plain',
            'wav': 'audio/x-wav',
            'wma': 'audio/x-ms-wma',
            'wmv': 'audio/x-ms-wmv',
            'xml': 'text/xml',
        }

        module.exports = (filePath) => {
            let ext = path.extname(filePath).split('.').pop().toLowerCase();

            if(!ext){
                ext = filePath;
            }
            return mimeTypes[ext] || mimeTypes['txt'];
        }
        ```
        ```js
        // function/range.js
        module.exports = (totalSize, req, res) => {
            const range = req.headers['range'];
            if (!range){    // 如果拿不到 range
                return {code: 200};   // 表示处理不了，直接返回 200，正常的返回就好了。
            }

            const sizes = range.match(/bytes=(\d*)-(\d*)/);   // * 号表示 重复零次或多次，可以有 也可以没有
            // 用 match 如果匹配到的话，会返回长度为3 的数组，第一个表示匹配到的内容，第二个表示 第一个 \d* , 第三个表示 第二个 \d*
            const end = sizes[2] || totalSize - 1;
            const start = sizes[1] || totalSize - end;

            // 接下来我们要判断一些非法条件
            if (start > end || start < 0 || end > totalSize){
                return {code: 200};
            }

            // 下面是可以处理时，返回的结果
            res.setHeader('Accept-Ranges', 'bytes');
            res.setHeader('Content-Ranges', `bytes ${start}-${end}/${totalSize}`);
            res.setHeader('Content-length', end - start);
            return {
                code: 206,   // part of content 表示部分内容
                start: parseInt(start),
                end: parseInt(end)
            };
        }
        ```
        ```html
        // static/template.html

        <!DOCTYPE html>
        <html lang="en">
        <head>
            <meta charset="UTF-8">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <meta http-equiv="X-UA-Compatible" content="ie=edge">
            <title>{{title}}</title>
        </head>
        <body>
            <ul>
                {{#each files}}
                <li><a href="{{../dir}}/{{file}}">【{{type}}】{{file}}</a></li>
                {{/each}}
            </ul>
            
        </body>
        </html>
        ```


- 验证 304 是否成功
    - 第一次在浏览器里输入网页地址，如：http://127.0.0.1:9527/function/compress.js
    - 然后，第二次，在浏览器输入网址的地方，敲回车
        - 这时候，在浏览器 控制台 - Network 里面，就能看到该文件为 304 Not Modified
    - 或者刷新操作也可以 出现 304

- ### 6-11 将 静态资源服务器工具 做成 CLI工具 (命令行工具)
- 需求
    - 就像 anywhere 一样，在命令行上敲 anywhere ，然后帮我们打开一个网页，就是当前文件夹。
    - 也可以写一些参数，来做自定义的配置
- 我们在上面 [6-10 http 缓存](#6-10-http-缓存) 的项目基础上改进
    ```
    项目目录
    |- /node_modules
    |- /static
        |- template.html
    |- /function
        |- cache.js
        |- compress.js
        |- defaultConfig.js
        |- mime.js
        |- range.js
    |- app.js
    |- package.json
    + |- README.md
    + |- index.js
    ```
    ```markdown
    // README.md
    # anydor

    Tiny NodeJS Static Web Server

    ## 安装
    ``
    npm i - g anydoor
    ``

    ## 使用方法
    ``
    anydoor # 把当前文件夹作为静态资源服务器根目录

    anydoor -p 8080 # 设置端口号为 8080

    anydoor -h localhost # 设置 host 为 localhost

    anydoor -d /usr # 设置根目录为 /usr
    ``
    ```
- 问题
    - 我们怎么才能读到命令行中 ```-p 8080``` 或者 ```--port 8080``` 这些参数呢
    - ```process.argv``` 可以读到 命令行上的参数列表
        - 但这种写法是比较麻烦的，如：需要我们分析 -p 和 --port 是同一个指令，之类的，会比较麻烦
    - 现成的工具
        - commander
        - [yargs](https://www.npmjs.com/package/yargs)
- yargs 使用
    - 安装 ```npm i yargs```
    - 使用
    ```js
    // index.js
    const yargs = require('yargs');

    const argv = yargs
        .usage('anywhere [options]')    // 用一句话告诉大家怎么用
        .option('p', {
            alias: 'port',  // 别名。这里会默认，以后生成的变量就是 port, 这里跟 defaultConfig.js 里保持一致即可
            describe: '端口号',
            default: 9527
        })
        .option('h', {
            alias: 'hostname',
            describe: 'host',
            default: '127.0.0.1'
        })
        .option('d', {
            alias: 'root',  // 跟 defaultConfig.js 里保持一致即可
            describe: 'root path',
            default: process.cwd()
        })
        .version()
        .alias('v', 'version')
        .help()  // 根据我们上面写的 option 自动生成 help 信息
        .argv;
    ```


7:30