assets
==========


[参考](https://github.com/balderdashy/sails-docs/blob/master/concepts/Assets/Assets.md)

和你服务里面的静态文件(js,css,images等)，这些文件都放在assets目录下，当你执行sails lift的适合，这些文件都会被处理到一个隐藏的临时目录(.tmp/public/)。

这个类似express的public文件夹，或者其他web serves[比如Apache]的www目录。
在sails里面可以用一些预编译的比如：LESS、CoffeeScript、SASS、spritesheets还有Jade等。

* 静态中间件

sails用的是Express的[static middleware](http://www.senchalabs.org/connect/static.html)来管理assets.

这个也可以配置：/config/http.js

举例：

你创建了assets/foo.html，可以这样访问：http://localhost:1337/foo.html
