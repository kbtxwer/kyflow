# 课程下载助手

所有的课程已在 [资源参照表](资源参照表.html) 中列出，可以根据名称查询对应的id

<hr>

## 常见命令
- 列出目录：
http://librarywap.koolearn.com/tree?productId=58761
	- 其中一部分json内容如下：
	- {"id":1586554,"pId":1586553,"name":"考研经验分享","klId":1039734,"ctype":3,"type":2,"wyType":1,"display_order":0,"_order":0}

- 获取播放地址：
http://librarywap.koolearn.com/getVideoUrl?courseUnitId=1586554
注意到我们将json中的id当成了courseUnitId
	- 如果这个id是存在的，返回内容如下：
		- {"data":"http://pl.koolearn.com/hls/m3u8_free?sKey=AF8E69CEC258F0D4FF1&url=/b2b/kyyy/xxk_ky_wx_xjp_01.mp4&timesTamp=1591833262647&consumerTypes=1003001","message":"ok","status":0}
	- 否则，返回内容如下：
		- {"data":null,"message":"fail","status":-1}

## 如何处理下载的m3u8文件？
- 由于密钥得下发地址会失效，我们要对其进行替换，改为永久链接
- 具体操作为用正则表达式模式(目前下载助手已经能自动替换，无需手动操作)
	- （notepad++下）将 URI[=]["].*["] 替换为 URI="http://kbtxwer.gitee.io/koolean_key.bin"
	- （Java下） 将 URI=\".*\" 替换为 URI="http://kbtxwer.gitee.io/koolean_key.bin"