Services
==========

#### 简介

Services可以被认为会在你的应用的很多地方的都会用到的库 - 包含一些方法。

举例：在你的应用里面，你会用到很多次的一个EmailService

在Sails最大的好处就是，services可以全局访问，而不需要手动require()来访问。

#### 如何创建一个service?

一般都是在api/services文件夹里面创建

比如： 在api/services里面有一个EmailService.js文件。

```
// EmailService.js - in api/services
module.exports = {

    sendInviteEmail: function(options) {

        var opts = {"type":"messages","call":"send","message":
            {
                "subject": "YourIn!",
                "from_email": "info@balderdash.co",
                "from_name": "AmazingStartupApp",
                "to":[
                    {"email": options.email, "name": options.name}
                ],
                "text": "Dear "+options.name+",\nYou're in the Beta! Click <insert link> to verify your account"
            }
        };

        myEmailSendingLibrary.send(opts);

    }
};
```


然后你就可以在你的应用的任何地方使用EmailService

比如在某一controller里面

```
// Somewhere in a controller
EmailService.sendInviteEmail({email: 'test@test.com', name: 'test'});
```