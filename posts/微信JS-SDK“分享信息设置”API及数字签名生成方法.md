---
title: 微信JS-SDK“分享信息设置”API及数字签名生成方法
date: 2016-11-05 13:45:55
tags: [js,微信]
---



jssdk

<!-- more -->

> 前提：一个通过认证了的微信公众号或者开发者帐号，没有通过认证的公众帐号。数字签名认证也能成功，但是分享信息是无法设置成功的 

#### Step1  添加安全域名
	左侧公众号设置--功能设置--JS接口安全域名
	添加安全域名

#### Step2  生成数字签名(服务端)
![http://images.cnitblog.com/blog/405426/201501/280924499562893.png](http://images.cnitblog.com/blog/405426/201501/280924499562893.png) 

获取access_token  

	请求接口:
	https://api.weixin.qq.com/cgi-bin/token?grant_type=client_credential&appid=你的appid&secret=你的secret
	请求方法: get
	返回结果: access_token (有效期7200秒，必须在服务端缓存)
	
获取签名所需ticket

	请求接口:https://api.weixin.qq.com/cgi-bin/ticket/getticket?access_token=上一步中获取的access_token&type=jsapi
	请求方法: get,
	type: JSON,
	返回结果: jsapi_ticket (有效期7200秒，必须在服务端缓存)
	
生成随机字符串

	// 随机字符串产生函数
	var nonceStr = function() {
		return Math.random().toString(36).substr(2, 15);
	};
生成时间戳

	// 时间戳产生函数
	var timeStamp = function () {
		return parseInt(new Date().getTime() / 1000) + '';
	};
	
签名算法 (可以参考官方给出的demo:[https://github.com/arronf2e/jssdk_simple](https://github.com/arronf2e/jssdk_simple))
	
	var calcSignature =function(ticket,nonceStr,timeStamp,url) {
		var result = {
			jsapi_ticket: ticket,
			nonceStr: nonceStr,
			timestamp: timeStamp,
			url: url,
		}
		var str = 'jsapi_ticket=' + ticket + '&noncestr=' + nonceStr + '&timestamp=' + timeStamp + '&url=' + url;
		// 对str使用sha1签名，得到signature，这里使用jsSHA模块，需install
		shaObj = new jsSHA(str, 'TEXT');
		result.signature = shaObj.getHash('SHA-1', 'HEX');
		return result; // 返回到前端，提供接口由前端请求
	}

#### Step3  在web中使用数字签名
@1 需要调用JS接口的页面引入如下JS文件，（支持https）：http://res.wx.qq.com/open/js/jweixin-1.0.0.js

@2 通过config接口注入权限验证配置  

	wx.config({
		debug: true,
		appId: '',
		timestamp: ,
		nonceStr: '',
		signature: '',
		jsApiList: ['onMenuShareTimeline']  //需要使用的JS接口列表
	})
	
@3 通过ready接口处理成功验证
	
	//config信息验证后会执行ready方法
	wx.ready(function() {
		wx.onMenuShareTimeline({
			title: '',
			desc: '',
			link: '',
			imgUrl: '',
			success: function() {
				
			},
			cancel: funcntion() {
				
			}
		})
	})
	
@4 通过error接口处理失败验证

	//config信息验证失败会执行error函数
	wx.error(function(res) {
		如签名过期导致验证失败，具体错误信息可以打开config的debug模式查看，也可以在返回的res参数中查看，对于SPA可以在这里更新签名。
	})

####  Done!
