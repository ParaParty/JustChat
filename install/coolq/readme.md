# [安装与架设](../)/QQ机器人 酷Q机器人

## 概述
- ```JustChat酷Q机器人端```用于接受与发送QQ群消息以供群员与```JustChat Minecraft服务器端```或```JustChat 消息转发控制中心```等使用。

## 配置文件
- 本插件使用的配置文档均以***UTF-8无BOM***形式储存。
- 基础配置文件 ```config.ini``` 或 ```config.json```
	1. ini格式
	```
	#通用设置
	[server]
	# 插件运作模式
	# 服务端模式(server) : 本插件开放端口以供其他JustChat客户端连接。
	# 客户端模式(client) : 连接到其他的JustChat服务端。
	mode=server
	# 当插件为服务端模式时为绑定侦听的本地IPv4地址，若为0.0.0.0既是侦听所有ip。
	# 当插件为客户端模式时为欲连接的服务器的IPv4地址。
	# IPv6:咕咕
	ip=0.0.0.0
	# 当插件为服务端模式时为绑定侦听的本地端口号。
	# 当插件为客户端模式时为欲连接的服务器的端口号。
	port=54321
	# 当插件为客户端模式时本设置有效，为本客户端的编号。（随机生成）
	ID=909431a3-d430-4cdb-b3c1-5cf3dc8f556e
	# 当插件为客户端模式时本设置有效，为本客户端的名称。
	name=My QQ Group
	# 当插件为客户端模式时本设置有效，为客户端心跳包的时间间隔。0为关闭。(单位:秒)
	pulseInterval=20
	[config]
	# 欲将本插件于何群使用
	groupid=123456789
	```
	1. json格式
	```
	{
	  "server" : {
		"mode" : "server",
		"ip" : "0.0.0.0",
		"port" : 54321,
		"ID" : "909431a3-d430-4cdb-b3c1-5cf3dc8f556e",
		"name" : "My QQ Group",
		"pulseInterval" : 20
	  },
	  "config" : {
		"groupid" : 123456789
	  }
	}
	```
- 消息输出格式 ```config.ini``` 或 ```config.json```
	1. ini格式
	```
	[message]
	# 当玩家加入游戏时，并未有接收到现成输出内容，机器人发往群中的消息的格式。
	Msg_INFO_Join=%SENDER% joined the game.
	# 当玩家退出游戏时，并未有接收到现成输出内容，机器人发往群中的消息的格式。
	Msg_INFO_Disconnect=%SENDER% left the game.
	# 当玩家死亡时，并未有接收到现成输出内容，机器人发往群中的消息的格式。
	Msg_INFO_PlayerDead=%SENDER% dead.
	# 当玩家发言时，机器人往群众发送的消息的格式。
	Msg_Text_Overview=[*][%WORLD_DISPLAY%]%SENDER%: %CONTENT%
	```
	1. json格式
	```
	{
		"Msg_INFO_Join": "%SENDER% joined the game.",
		"Msg_INFO_Disconnect": "%SENDER% left the game.",
		"Msg_INFO_PlayerDead": "%SENDER% dead.",
		"Msg_Text_Overview": "[*][%WORLD_DISPLAY%]%SENDER%: %CONTENT%"
	}
	```