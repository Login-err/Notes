### Vue在未使用history模式时，静态文件加载出现错误

#### 解决方法：在build里面的index.js将build里面的``  assetsPublicPath:'/'  `` 改为 ``  assetsPublicPath:'./' ``

### Vue路由在使用history模式之后，出现``loading chunk n fail ``的问题

#### 解决方法：在build里面的index.js将build里面的``  assetsPublicPath:'./'  `` 改为 ``  assetsPublicPath:'/' ``

