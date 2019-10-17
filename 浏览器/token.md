##### token工作原理图

![img](https://lc-gold-cdn.xitu.io/16894865298b0f8fc60c.png?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

* 登录时候，客户端通过用户名与密码请求登录
* 服务器收到请求区验证用户名与密码
* 验证通过，服务端会签发一个token，再把这个token发给客户端
* 客户端收到token，储存到本地，如：Cookie，SessionStorage，LocalStorage，我们是存在SessionStorage
* 客户端每次向服务器请求API接口时候，都得带上Token
* 服务端收到请求，验证Token，如果通过就返回数据，否则提示报错信息