# [安装与架设](../)/Minecraft Bukkit 服务端
- [MCBBS发布帖](http://www.mcbbs.net/thread-788137-1-1.html)

## 概述
- ```JustChat Minecraft Bukkit客户端```用于接受与发送Minecraft聊天消息以供玩家与```JustChat QQ机器人端```或```JustChat 消息转发控制中心```等使用。

### 配置文件
```
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
useVexView: true

#收到图片时显示在屏幕的位置x
#需要VexView插件支持
#这个值需要在0和1之间，它是你屏幕从左到右的百分比宽度
imageX: 0.68

#收到图片时显示在屏幕的位置y
#需要VexView插件支持
#这个值需要在0和1之间，它是你屏幕从上到下的百分比高度
imageY: 0.65
```