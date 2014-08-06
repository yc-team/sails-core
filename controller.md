controllers
==========

C in MVC

尝尝扮演着models和views的中间人。


Controllers由一个方法的集合组成，称为actions。

比如：在你的应用里面有一个定义的GET的 /hello route可以绑定这个一个方法：

```
//config/routes.js
'/hello': 'IndexController.hello',
```

```
//api/controllers/IndexController.js
hello: function (req, res) {
	return res.send("hello world");
}
```

浏览器访问/hello的时候，页面会显示"hello world".


* controllers在哪里定义？

controllers都在api/controllers/这个文件夹里面定义。
文件名必须是以Controller.js结尾。
Sails的controllers一般都是驼峰命名，首字母都是大写，比如：

```
UserController.js, MyController.js and SomeGreatBigController.js
```


* controller文件长什么样子？

```
module.exports = {
  hi: function (req, res) {
    return res.send("Hi there!");
  },
  bye: function (req, res) {
    return res.redirect("http://www.sayonara.com");
  }
};
```

从例子中{}看出：

1、对应keys就是action的名称
2、values就是对应的方法体

这个controll定义了2个actions：

1、hi：  responds to a request with a string message。
2、bye：重定向到其他的站点。

req和res对象对任何一个用过express的人都比较熟悉。因为sails用Express来操作routing.




* Routing

默认情况下：

按照

```
/:controllerIdentity/:nameOfAction
```

这种规则来触发action。

举例：

在api/controllers/SayController.js：

```
module.exports = {

  bye: function (req, res) {

  	return res.send("bye");
    
  },

  hi: function (req, res) {
    return res.send("hi");
  }

};
```

这样，当sails lift的时候，访问/say/hi和/say/bye的时候会指向对应的SayController的hi action和bye action。

Sails的自动route绑定。



* 自动生成controllers

可以用sails的命令行工具快速地生成一个controller.

语法：

```
sails generate controller <controller name> [action names separated by spaces...]
```

举例：

```
//info: Created a new controller ("comment") at api/controllers/CommentController.js!
sails generate controller comment create tag like
```

我们看一下api/controllers目录下多了一个CommentController.js

```
/**
 * CommentController
 *
 * @description :: Server-side logic for managing comments
 * @help        :: See http://links.sailsjs.org/docs/controllers
 */

module.exports = {
	


  /**
   * `CommentController.create()`
   */
  create: function (req, res) {
    return res.json({
      todo: 'create() is not implemented yet!'
    });
  },


  /**
   * `CommentController.tag()`
   */
  tag: function (req, res) {
    return res.json({
      todo: 'tag() is not implemented yet!'
    });
  },


  /**
   * `CommentController.like()`
   */
  like: function (req, res) {
    return res.json({
      todo: 'like() is not implemented yet!'
    });
  }
};
```