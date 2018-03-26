# 微信JSSDK类

### 没有实现的接口
* ibeacon设备相关接口
* 微信卡券添加卡券以外的接口
* 微信支付接口
* 分享到腾讯微博


### 存在问题的接口实现
* 语音识别接口如果没有接收到语音似乎会出现错误


### 功能
* 将所有的接口写成InvokeWechatAPI类的方法进行方便的调用
* 所有抛出错误同时都会alert相同错误信息，以便在手机上看到



### 使用方法：
1. 将 `jssdk_set` 文件夹放到主页面（这里是`index.php`）同级的位置
2. 在主页面填写`APPID`和`APPSECRET`
3. 在wx.ready回调时就要调用的接口直接放进其回调函数中，之后再调用的接口可以放到外部
4. 所有的接口调用都通过 `InvokeWechatAPI` 类的相应原型方法。见 `APIInvoking.js` 文
   件。
5. 公众平台——开发——基本配置——IP白名单，填写代码所在的IP地址，否则无法获取
   `access token`，从而出现 `config:invalid signature` 的错误
6. 公众平台——设置——公众号设置——功能设置——JS接口安全域名，填写代码所在的域名并上传提
   供的txt文件。否则会出现 `invalid url domain` 的错误。



### 注意事项：
* 传入`wx.ready()`方法的的函数并不是配置成功之后的回调函数。在配置成功之前调用`ready`
  方法传入函数，该函数会等待配置成功后执行；在配置成功之后调用ready方法传入函数，该
  函数会立刻执行。
* **分享给朋友和分享到朋友圈时设置的分享链接的域名或路径必须与当前页面对应的公众
号JS安全域名一致，否则会静默失败。**



### 对官方文件的合并和修改
* 在JSSDK类构造函数中动态创建 jsapi_ticket.php 和 access_token.php
* 在JSSDK类中添加了计算卡券签名的方法 getCardSignature


## 注意
这里会直接调用微信接口刷新 `access token`，在实际使用时如果还有其他应用也需要
`access token`，则需要统一获取。否则其中一个刷新后其他的就会提前过期。
