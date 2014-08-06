view
==========

[参考](https://github.com/balderdashy/sails-docs/blob/master/concepts/Views/Views.md)

默认的模板支持是EJS，其他也可以配置的，但是需要安装对应的包，比如jade

EJS的3种模板标记：

* <%= someValue %>
* <%- someRawHTML %> 这种不会转义，比如 ' 等 
* <% /* some javascript code with access to the data as local variables */ %>



* 数据从哪里来？

在sails以及其他的一些MVC的框架里面，views的动态数据都是从controll里面传递过去的。在sails的controllers，用 res.view()这个方法可以用来传递数据。

controllers/FooController.js的index的action里面对应的view：views/foo/index.ejs。


> 这个称为Server-Side Views，规则就是：/views/:controller/:action.ejs

res.view(data)，这个data参数必须是纯js对象！

比如：

```
res.view({
  name: 'Mike',
  favoriteColor: 'green',
  friends: [{
    name: 'Margaret Thatcher',
    favoriteColor: 'purple'
  },
  {
    name: 'Big Bird',
    favoriteColor: 'yellow'
  }]
});
```
