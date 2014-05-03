---
layout: post
title: "使用GoAgent进行翻墙代理"
category: proxy
tagline: 
tags: [proxy, GoAgent]
description: "使用GoAgent进行翻墙代理"
---

# 使用GoAgent进行翻墙代理
> GoAgent是一个基于Google Appengine的，全面兼容IE，FireFox，chrome的代理工具，使用Python和Google App EngineSDK编写，程序可以在Microsoft Windows，Mac，Linux，Android，iPod Touch，iPhone，iPad，webOS，OpenWrt，Maemo上使用。GoAgent出口地址使用的是美国加利福尼亚州山景城Google数据中心IP段。  

## GoAgent的使用方法

### 1. 申请Gmail帐号
因为使用的是Google App Engine，是需要用Gmail帐号登录的，所以没有话要先[注册](https://accounts.google.com/SignUp)一个，如果已经有Gmail帐号的话，直接看下一步。

### 2. 注册appid
1. 打开http://appengine.google.com/ ,输入gmail用户密码登入。
2. 然后点击Create Application进入下一步
3. 输入自己的手机号
4. 手机收到验证码后输入，验证成功后 申请完成。
5. 创建一个appid，比如：abc555，**注意记下这个appid**，后面还会再用到。最后点击Create Application完成整个注册过程。

### 3. 下载GoAgent主程序
1. 进入https://code.google.com/p/goagent/下载GoAgent
2. 解压并修改`local\proxy.ini`中的[gae]下的appid=你的appid(多appid请用`|`隔开)
3. 双击server\uploader.bat 开始上传, 成功后即可使用了(地址127.0.0.1:8087)  
   MacOS/Linux 请在 Terminal 执行 cd server && python uploader.zip  
   (其间需要输入你的appid和gmail的帐号和密码)

### 4. 使用 GoAgent
* chrome请安装 [SwitchySharp](https://chrome.google.com/webstore/detail/dpplabbmogkhghncfbfdeeokoefdjegm) 插件（拖放SwitchySharp.crx到扩展设置），然后导入 SwitchyOptions.bak
* firefox请安装 [FoxyProxy](https://addons.mozilla.org/zh-cn/firefox/addon/foxyproxy-standard/) ，Firefox需要导入证书
* IE/Opera 用户请右击 goagent.exe 托盘图标设置 IE 代理。

### 5. 启动GoAgent
* window下直接动行goagent.exe就可以了
* mac下cd到local目录下，然后执行`python proxy.py`

**chrome在使用goagent上很多网站例如登陆twitter，总提示：说“该网站的安全证书不受信任！”**
如果出现这个问题，可进行如下设置
1. 通过 chrome设置-》高级设置-》https/ssl（管理证书）-》导入-》受信任的根证书颁发机构-》然后选择`goagent\local\CA.crt`这个文件
2. 实用工具 > 钥匙串访问 > 系统 中找到GoAgent CA 并双击，选择 信任->加密套接字协议层(SSL)->总是信任

现在基本就可以翻墙了。  
**（使用贴士：以后每次用的时候，只需启动GoAgent（记住终端不能关！），然后开启插件，选择goagent，就可以使用了，也就是：开终端-->开插件-->上网！)**

## 参考文章
* [GoAgent](https://code.google.com/p/goagent/)
* [Mac OS利用GAE翻墙](http://www.appifan.com/jc/201209/35546.html)
* [怎样在mac下用goagent翻墙](http://www.guokr.com/blog/436937/)