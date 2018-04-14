###小程序兼容处理
####基础库
#####基础库与客户端之间的关系
小程序的能力需要微信客户端来支撑，每一个基础库都只能在对应的客户端版本上运行，高版本的基础库无法兼容低版本的微信客户端。
关于基础库的兼容方法，可以查看[兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)章节。

Page.prototype.route
基础库 1.2.0 开始支持，低版本需做兼容处理

route 字段可以获取到当前页面的路径。

低版本获取当前页面路径：
```markdown
getCurrentPageUrl: function(){
    var pages = getCurrentPages()    //获取加载的页面
    var currentPage = pages[pages.length - 1]    //获取当前页面的对象
    var url = currentPage.route    //当前页面url
    return url
  },

/*获取当前页带参数的url*/
  getCurrentPageUrlWithArgs:function () {
    var pages = getCurrentPages()    //获取加载的页面
    var currentPage = pages[pages.length - 1]    //获取当前页面的对象
    var url = currentPage.route    //当前页面url
    var options = currentPage.options    //如果要获取url中所带的参数可以查看options

    //拼接url的参数
    var urlWithArgs = url + '?'
    for (var key in options) {
      var value = options[key]
      urlWithArgs += key + '=' + value + '&'
    }
    urlWithArgs = urlWithArgs.substring(0, urlWithArgs.length - 1)

    return urlWithArgs
  }
  ```
####路由
#####页面栈 Tab切换


