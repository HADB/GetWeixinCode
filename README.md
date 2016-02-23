# GetWeixinCode

解决微信OAuth2.0网页授权回调域名只能设置一个的问题

## 使用方法

1. 部署get-weixin-code.html至你的微信授权回调域名的目录下，例如http://wx.abc.com/get-weixin-code.html
2. 在其他页面的使用方式如下，类似于直接通过微信回调的方式，只是将回调地址改成了get-weixin-code.html的地址，另外省去了response_type参数（因为它只能为code）以及#wechat_redirect的hash，它们会在get-weixin-code.html里面去加上
    ```javascript

    location.href = 'http://wx.abc.com/get-weixin-code.html?appid=XXX&scope=XXX&state=XXX&redirect_uri=' + encodeURIComponent(location.href);

    ```
3. get-weixin-code.html页面从微信那里拿到code之后会重新跳转回调用的页面，并且在url后面带上code

## 其他说明

- 通过多一次的跳转，解决了微信限制回调域名只能设置一个的问题
- 牺牲了一点用户体验，换来了项目部署的美感，不需要将各种项目都部署到一个域名下
- 如果你有这样的需求，可以使用本项目
- 欢迎提交pull request