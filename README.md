JavaScript Npm Passing Args to Scripts Demo
===========================================

想通过`npm run`来运行一个命令，同时向该命令里面调用的程序传递一些参数，可以使用`--`来分隔。

比如:

```
npm run demo -- hello
npm run demo -- -hello
npm run demo -- --hello
```

```
npm install
```

```
npm run demo -- --my-name
```

输出：

```
> @ demo /Users/freewind/workspace/javascript-npm-passing-args-to-scripts-demo
> node hello.js "--my-name"

Hello, --my-name! (hello.js)
```

```
npm run demo --my-name
```

输出：

```
$ npm run demo --my-name

> @ demo /Users/freewind/workspace/javascript-npm-passing-args-to-scripts-demo
> node hello.js

Hello, undefined! (hello.js)
```

问题
---

Q: 我发现，如果不加`--`，似乎也可以传参数，比如`npm run demo hello`，那为什么还要加`--`呢?

A: 根据我的观察，如果没有加`--`，npm自己会尝试解析所有参数，最后把识别不了的再丢给`demo`里的脚本。
所以，如果参数是`hello`这样的，由于npm不认识它，它会很幸运的被传给`demo`脚本。
但是其它的，比如以`-`或者`--`开头的，都会被npm吃掉。
而加了单独的`--`，npm就知道它后面的参数都不是自己的，所以不会碰，直接传给`demo`
