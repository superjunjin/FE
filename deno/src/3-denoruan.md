# 3-denoruan

转载自 [Deno 运行时入门教程：Node.js 的替代品](http://www.ruanyifeng.com/blog/2020/01/deno-intro.html)

## Deno 运行时入门教程：Node.js 的替代品

这几天假期，我学习了一下 [Deno](https://deno.land/)。它是 Node.js 的替代品。有了它，将来可能就不需要 Node.js 了。

这篇文章就是 Deno 的一个初步介绍，尝试回答为什么 Node.js 不能满足需要，以及 Deno 能够带给我们什么？

以下内容主要基于 [Bert Belder](https://www.youtube.com/watch?v=puXyo1jGQys) 和 [Ryan Dahl](https://www.youtube.com/watch?v=1gIiZfSbEAE) 的最新演讲。

### 0 名字

进入主题之前，先说一下 Deno 这个词怎么发音。

两种发音，"德诺"和"蒂诺"，我都听到过。看起来，"蒂诺"这个发音应该更合适一些，因为 Deno 的标志是一只恐龙。恐龙（dinosaur）的英文缩写正是 dino。

### 1 起源

Deno 是 Ryan Dahl 在2017年创立的。

Ryan Dahl 也是 Node.js 的创始人，从2007年一直到2012年，他后来把 Node.js 移交给了其他开发者，不再过问了，转而研究人工智能。

他始终不是很喜欢 Python 语言，久而久之，就想搞一个 JavaScript 语言的人工智能开发框架。等到他再回过头捡起 Node.js，发现这个项目已经背离了他的初衷，有一些无法忽视的问题。

### 2 node缺点

![3-denoruan1](../../../../.gitbook/assets/3-denoruan1.jpg)

首先，过去五六年，JavaScript 语言脱胎换骨，ES6 标准引入了大量新的语法特性。其中，影响最大的语法有两个：==Promise 接口（以及 async 函数）和 ES 模块==。

Node.js 对这两个新语法的支持，都不理想。由于历史原因，Node.js 必须支持回调函数（callback），导致异步接口会有 Promise 和回调函数两种写法；同时，Node.js 自己的模块格式 CommonJS 与 ES 模块不兼容，导致迟迟无法完全支持 ES 模块。

其次，Node.js 的模块管理工具 npm，逻辑越来越复杂；模块安装目录 npm\_modules 极其庞杂，难以管理。==Node.js 也几乎没有安全措施==，用户只要下载了外部模块，就只好听任别人的代码在本地运行，进行各种读写操作。

再次，Node.js 的功能也不完整，==导致外部工具层出不穷==，让开发者疲劳不堪：webpack，babel，typescript、eslint、prettier......

### 3 deno简介

![3-denoruan2](../../../../.gitbook/assets/3-denoruan2.jpg)

由于上面这些原因，Ryan Dahl 决定放弃 Node.js，从头写一个替代品，彻底解决这些问题。deno 这个名字就是来自 Node 的字母重新组合（Node = no + de），表示"拆除 Node.js"（de = destroy, no = Node.js）。

跟 Node.js 一样，Deno 也是一个服务器运行时，但是支持多种语言，可以直接运行 JavaScript、TypeScript 和 WebAssembly 程序。

==它内置了 V8 引擎==，用来解释 JavaScript。同时，==也内置了 tsc 引擎==，解释 TypeScript。它==使用 Rust 语言开发==，由于 Rust 原生支持 WebAssembly，所以它也能直接运行 WebAssembly。它的异步操作不使用 libuv 这个库，而是使用 Rust 语言的 [Tokio](https://github.com/tokio-rs/tokio) 库，来实现事件循环（event loop）。

### 4 why Rust

​ ![3-denoruan3](../../../../.gitbook/assets/3-denoruan3.jpg)

你可能会问，为什么使用 Rust，而不是 C++（Node.js 的开发语言）？

主要原因是 Rust 提供了很多现成的模块，对 Deno 本项目来说，可以节约很多开发时间。

### 5 Deno是箱子（既装了别人，又被别人包装）

![3-denoruan4](../../../../.gitbook/assets/3-denoruan4.jpg)

Deno 本身也是 Rust 的一个模块。如果你想在 Rust 里面使用 V8 引擎，就可以加载 Deno。它等于是一个 V8 的包装层，提供一些底层 API，让你跟 V8 引擎互动。

V8 &gt; Deno &gt; Rust

### 6 单独

![3-denoruan5](../../../../.gitbook/assets/3-denoruan5.jpg)

Deno 只有一个可执行文件，所有操作都通过这个文件完成。它支持跨平台（Mac、Linux、Windows）。

### 7 安全

![3-denoruan6](../../../../.gitbook/assets/3-denoruan6.jpg)

Deno 具有安全控制，默认情况下脚本不具有读写权限。如果脚本未授权，就读写文件系统或网络，会报错。

必须使用参数，显式打开权限才可以。

* `--allow-read`：打开读权限，可以指定可读的目录，比如`--allow-read=/temp`。
* `--allow-write`：打开写权限。
* `--allow-net=google.com`：允许网络通信，可以指定可请求的域，比如`--allow-net=google.com`。
* `--allow-env`：允许读取环境变量。

### 8 浏览器兼容

![3-denoruan7](../../../../.gitbook/assets/3-denoruan7.jpg)

Deno 支持 Web API，尽量跟浏览器保持一致。

它提供 window 这个全局对象，同时支持 fetch、webCrypto、worker 等 Web 标准，也支持 onload、onunload、addEventListener 等事件操作函数。

此外，Deno 所有的异步操作，一律返回 Promise。

### 9 URL 加载模块

![3-denoruan8](../../../../.gitbook/assets/3-denoruan8.jpg)

==Deno 只支持 ES 模块，跟浏览器的模块加载规则一致==。没有 npm，没有 npm\_modules 目录，没有`require()`命令（即不支持 CommonJS 模块），也不需要`package.json`文件。

所有模块通过 URL 加载，比如`import { bar } from "https://foo.com/bar.ts"`（绝对 URL）或`import { bar } from './foo/bar.ts'`（相对 URL）。因此，==Deno 不需要一个中心化的模块储存系统，可以从任何地方加载模块。==

但是，Deno 下载模块以后，依然会有一个总的目录，在本地缓存模块，因此可以==离线==使用。

### 10 模块就是file就是url

![3-denoruan9](../../../../.gitbook/assets/3-denoruan9.jpg)

由于 Deno 只支持从 URL 加载模块，导致 Node.js 的模块加载写法都会失效。

```text
import React from "react";
import { Box, Grid } from "@material-ui/core";
import { initializeApp } from "firebase/app";
```

上面的写法在 Deno 里面都是非法的。

Deno 的所有模块都要通过入口脚本加载，不能通过模块名加载，所以必须带有脚本后缀名。

### 11 开箱即用的TS

![3-denoruan10](../../../../.gitbook/assets/3-denoruan10.jpg)

Deno 原生支持 TypeScript 语言，可以直接运行，不必显式转码。

它的内部会根据文件后缀名判断，如果是`.ts`后缀名，就先调用 TS 编译器，将其编译成 JavaScript；如果是`.js`后缀名，就直接传入 V8 引擎运行。

### 12 命令代替工具

![3-denoruan12](../../../../.gitbook/assets/3-denoruan12.jpg)

Deno 内置了开发者需要的各种功能，不再需要外部工具。打包、格式清理、测试、安装、文档生成、linting、脚本编译成可执行文件等，都有专门命令。

执行`deno -h`或`deno help`，就可以显示 Deno 支持的子命令。

* `deno bundle`：将脚本和依赖打包
* `deno eval`：执行代码
* `deno fetch`：将依赖抓取到本地
* `deno fmt`：代码的格式美化
* `deno help`：等同于`-h`参数
* `deno info`：显示本地的依赖缓存
* `deno install`：将脚本安装为可执行文件
* `deno repl`：进入 REPL 环境
* `deno run`：运行脚本
* `deno test`：运行测试

### 13 安装运行

Deno 的安装可以参考[官网首页](https://deno.land/)，但是你可以直接去 GitHub 仓库的[发布页](https://github.com/denoland/deno/releases)，下载编译好的可执行文件（上图）。

下载 Deno 以后，查看一下版本。

```text
$ deno --version
deno 0.31.0
v8 8.1.108
typescript 3.7.2
```

命令行直接运行`deno`，就会进入 REPL 环境。

```text
$ deno
> console.log(1,2,3)
1 2 3
undefined
>
```

### 14 运行安全

下面，运行一个 TypeScript 的远程脚本，这是官网给出的[例子](https://deno.land/std/examples/curl.ts)。

```text
$ deno run \
https://deno.land/std/examples/curl.ts \
https://example.com
```

上面例子中，Deno 执行远程脚本`curl.ts`，用这个脚本去抓取网址`example.com`。但是，运行后报错，表示没有网络通信的权限。

我们给予 Deno 网络通信的权限，就可以顺利执行。

```text
$ deno run --allow-net \
https://deno.land/std/examples/curl.ts \
https://example.com
```

### 15 为了1.0

![3-denoruan13](../../../../.gitbook/assets/3-denoruan13.jpg)

现在，Deno 最新版本是 0.31。根据规划，1.0 应该会在今年上半年发布。

Deno 还处在密集开发中，功能不稳定，不建议用于生产环境。但是，它已经是一个可用的工具，大家可以多试用，熟悉它的用法。我相信，设计上的诸多优点，将会使它比 Node.js 更具优势。

