globals
==========

#### 概要

为了方便，Sails暴露了一些有用的全局变量。



#### sails

在很多情况下，你都期望保留sails这个全局对象可以访问，这样你的应用代码比较干净。
但是，如果你需要disabled所有全局变量，包括sails，你还是可以通过访问：req._sails来访问sails变量的


#### Models 和 Services

你应用里面的models和services会暴露在全局，可以用globalId来访问。

比如: 

* 在api/models/Foo.js里面定义了一个model，这样全局可以用Foo来访问。
* 在api/services/Baz.js里面定义了一个service，这样全局可以用Baz来访问。


#### Async 和 Lodash

sails同时也暴露了lodash as _，还有async as async。这些常用的工具默认就被支持，你不需要npm install来在每一个新项目里面手动安装。
和sails的其他全局变量一样，他们都是可以被disabled。



#### disable全局变量

在config/global.js里面可以通过配置，来决定哪些变量暴露到全局。

1、disable所有的全局变量，可以这样：

```
// config/globals.js
module.exports.globals = false;
```

2、指定某些来disable

```
// config/globals.js
module.exports.globals = {
  _: true,
  async: false,
  models: false,
  services: false
};
```

注意:

> 记住：所有的全局变量包含sails，只有在sails被加载完成后，才可以访问。换句话说：当sails还没有加载完，你没法在一个方法里面使用 sails.models.user 或者 User