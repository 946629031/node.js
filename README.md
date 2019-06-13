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
    - [3-1 CommonJS1](#3-1-环境--调试-commonjs1)
    - [3-2 CommonJS2](#3-2-环境--调试-commonjs2)
    - [3-4 引用系统内置模块 & 引用第三方模块](#3-4-环境--调试--引用系统内置模块--引用第三方模块)
    - [3-5 module.exports 与 exports 的区别](#3-5-环境--调试--moduleexports-与-exports-的区别)
    - [3-6 环境 & 调试 —— global变量]()
- []()
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
- ### 3-1 环境 & 调试 ——CommonJS1
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

- ### 3-2 环境 & 调试 ——CommonJS2
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
        
- ### 3-4 环境 & 调试 —— 引用系统内置模块 & 引用第三方模块
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

- ### 3-5 环境 & 调试 —— module.exports 与 exports 的区别
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


- ### 3-6 环境 & 调试 —— global变量
    - global 是什么？
        - global 是 NodeJS 的全局变量
        - 和浏览器非常相像，在浏览器中，我们的 全局方法和属性 就挂载在 window 中
        - 同样的，在 node 中，我们把希望能在全局访问到的 对象、属性、方法 就挂载在 global 中
    - global 自带的属性 和 方法
        - CommonJS
        - Buffer, process, console
        - timer
            - 包括 setTimeout, setInterval, ...等
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

- ### 3-7 环境 & 调试 —— process进程
    - [Process 官方文档](http://nodejs.cn/api/process.html)
    - 什么是 Process ？
        - 进程
    - Process 里面有什么？
        - Process Events - 进程事件
            - uncaughtException
                - 在我们程序执行的时候，有的异常没有被捕获，这样的话有可能 **打断整个进程**，为了防止这种情况，我们可以在 Process 下面 **加最后一层保险。当异常被抛到最外层的时候，我们来捕获一下**，让 Process 可以优雅的退出
        - 参数相关
            - argv, argv0, execArgv, execPath
                ```js
                // 10-process.js
                const {argv, argv0, execArgv, execPath} = process;
                // 这四个对象 都是 process 的子对象
                ```
                - process.argv 其中包含当启动 Node.js 进程时，传入的命令行参数
                    ```js
                    // 10-process-argv.js
                    process.argv.forEach(item => {
                        console.log(item)
                    })
                    ```
                    - 执行 ```node 10-process-argv.js```
                    ```js
                    /usr/local/bin/node     // 表示启动进程所用的命令，也是node安装路径
                    /Users/Samartian/nodejs/demos/10-process-argv.js    // 表示当前执行文件的路径
                    // 上面两条是固定的
                    ```
                    - 当然也可以带自定义参数，如，执行 ```node 10-process-argv.js --test a=1 b=2```
                    ```js
                    /usr/local/bin/node
                    /Users/Samartian/nodejs/demos/10-process-argv.js

                    --test
                    a=1
                    b=2
                    // 命令行传入的参数都会被打印出来
                    ```
























[3-6 0:00]()
