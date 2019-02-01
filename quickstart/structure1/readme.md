# [快速搭建](../)/机器人 - Minecraft 模式

## 特点
- 最简单的运行模式，搭建简单。
- 本运作结构针对一游戏服务器与一群互通，适合大多数的用户使用。

## 运行模式
- 我们再次看一下运行结构图，分析一下我们需要做些什么。
<img src="image/structure.svg" width="480"/>
- 我们只需要关注红色部分即可。因为黑色部分已经是被别人做好的了~

## 开始搭设
- 我们以 [Bukkit](../../install/bukkit) 与 [CoolQ](../../install/coolq) 为例。
- 在这个运行结构中。 酷Q机器人端设为JustChat服务端，Minecraft服务器端设为JustChat客户端。
1. 先下载好 [Bukkit](https://bukkit.org) 与 [CoolQ Air](https://cq.im/air) 备用。 
(```CoolQ Air``` 为 CoolQ 的免费版，使用付费的 [CoolQ Pro](https://cq.im/pro) 依然可以正常使用本插件)
1. 搭设 酷Q机器人端
	1. 将cpk插件文件复制到酷Q插件目录: ```app/``` 。
	![image/cq_0.jpg"]()
	1. 启动酷Q并启用本插件，生成初始配置文件。
	![image/cq_1.jpg"]()
	1. 在 ```data/app/com.superexercisebook.justchat/``` 或 ```app/com.superexercisebook.justchat/``` 中找到配置文件并按照您的喜好修改。
	[配置文件格式介绍](../../install/coolq/#配置文件)
	注意： ```[server]mode``` 必须为 ```server``` 
	```
# 这是一个配置文件样例
[server]
ip=0.0.0.0
port=54321
mode=server

[config]
groupid=您的MC服务器交流QQ群群号
	```
	1. 重启 酷Q ，使得修改后的配置文件生效。
1. 搭设 Minecraft Bukkit 服务端
	1. 将jar插件文件复制到酷Q插件目录: ```plugins/``` 。
	![image/bukkit_0.jpg"]()
	1. 启动 Bukkit 服务端，生成初始配置文件。
	1. 在 ```plugins/MultiRobot/```  中找到配置文件并按照您的喜好修改。
	[配置文件格式介绍](../../install/bukkit/#配置文件)
```
# 这是一个配置文件样例
############### 服务器设置 ###############
#服务器IP，必须是x.x.x.x形式，使用域名会连接不上服务器
#本地请使用127.0.0.1
serverIP: "127.0.0.1"

#服务器端口，默认8282
serverPort: 8282

#服务器名称
serverName: "Bukkit"

#-----------开发设置----------#
#！！！非必要请勿改动！！！
#服务器心跳速度（秒）
#需要与PHP服务器的心跳同时修改
serverPulse: 20

############### 扩展插件 ##################
#是否使用VexView插件来显示图片
#需要付费版的VexView才能使用
useVexView: false

#收到图片时显示在屏幕的位置x
#需要VexView插件支持
#这个值需要在0和1之间，它是你屏幕从左到右的百分比宽度
imageX: 0.68

#收到图片时显示在屏幕的位置y
#需要VexView插件支持
#这个值需要在0和1之间，它是你屏幕从上到下的百分比高度
imageY: 0.65

############### 聊天设置 ##################
# %world% 表示来自哪个世界或哪个群
# %player% 表示说话的玩家

#收到的信息在MC中的聊天前缀
messageFormQQ: "[%world%]<%player%> "
```
	1. 重启 Bukkit ，使得修改后的配置文件生效。