# GetCookies

Chrome下获取Cookies插件,突破HTTP ONLY限制  

# 获取插件

### 谷歌商店
[Chrome商店下载](https://chrome.google.com/webstore/detail/cookies-get-assistant/flidilldhehoieobcejmjmnhfaabghfc)

### 直接下载（安装需信任ID: flidilldhehoieobcejmjmnhfaabghfc）
[crx直接下载（Github）](https://raw.githubusercontent.com/elfive1992/GetCookies/master/GetCookies.crx)  

# 使用文档

## 绑定按钮点击事件
插件会寻找DOM树中属性为`[data-toggle='get-cookie']`的元素标签并绑定click事件,
所以如果想获取Cookies就首先必须让页面上有一个带此属性的标签.  
例如button标签,所有信息都是通过button标签的属性进行获取的.

		<button class="icon-btn-device" data-cookie=" " data-name="BDUSS" data-site="http://pan.baidu.com/" data-toggle="get-cookie" >点击获取</button>

## 检测插件是否正常加载
如果插件加载了,会在body标签增加一个`get-cookie`属性,调用前JS检测一下即可

		<body get-cookie="true">

## 设置获取Cookie的site(可选)
在button标签上添加属性data-site
例如:

		data-site=http://pan.baidu.com/

这样设置的是获取百度网盘页面下的Cookie,当然也包括*.baidu.com域的Cookies

## 设置获取Cookie的name(可选)
在button标签上添加属性data-name
例如:

		data-name=BDUSS

说明获取的Cookies的name为BDUSS.

## 设置获取Cookie的domain(可选)
在button标签上添加属性data-domain
例如:

		data-domain=.baidu.com

设置获取的Cookies的domain属性为.baidu.com.

## 设置Cookie的value
在button标签上添加属性data-cookie
可以默认设置为空值.
获取到的Cookie会添加到这个属性上

## 获取Cookie之后回调

	    window.addEventListener("message", receiveMessage, false);

			function receiveMessage(event)
			{
				if (event.origin == window.location.origin){
					console.log(event.data);
				}
			}


## 触发获取Cookie事件
JS模拟Click事件即可触发,之后读取data-cookie即可.
例如:

data-cookie={"BDUSS":"ABC","BAIDUID":"ASCED"}

返回一个对象.

## 备注

现阶段为了安全起见,只在以下网站加载本插件.

* https://qiandao.elfive.vip/
* https://qiandao.elfive.cn/

如果想要使用到你个人的网站中，请联系我：elfive@elfive.cn  

当你满足一下条件就可以联系我为你更新插件：  

1、我只为签到项目提供改服务；  

2、你的签到项目必须是 fork 我的项目或者 acgotaku 本人的项目，而且必须是开源项目；
- 我的项目 [Github](https://github.com/elfive1992/qiandao)
- acgotaku（[Github](https://github.com/binux/qiandao)）  

3、联系我的时候，请务必在邮件中附上你个人的开源项目地址，目前仅限于 Github；  

4、因为我只是为了方便没有谷歌开发者的朋友，所以不会收取任何费用，但是如果用于非法用途，将保留追究责任的权利（包括但不限于民事、刑事责任）。
