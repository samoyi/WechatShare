# 微信分享设置

### 功能：
* 只需要拷贝一个不需要修改文件夹和引入两段代码
* 可以根据事件来决定何时设置分享信息。（例如在用户玩完游戏之后再将成绩作为分享描述）

### 使用方法：
1. 将 WechatShare 文件夹放到主页面（这里是index.php）同级的位置
2. 在主页面中添加 index.php 中的一段JS代码和PHP代码，保证JS代码在PHP代码之前，并填写设置

### 注意事项：
1. 官方示例文件默认所有文件都是同级而不像这里又有一层，所以这里的代码中有几处在官方文件中改写了路径。搜索“WechatShare”可找到。
2. 如果出现 *invalid url domain* 的错误提示，可能可以通过设置公众号JS接口安全域名来解决：进入公众平台——点击公众平台logo——功能设置——JS接口安全域名 


