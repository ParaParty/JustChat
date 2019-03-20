# [安装与架设](../)/Minecraft Sponge 服务端

## 概述
- ```JustChat Minecraft Sponge 客户端```用于接受与发送Minecraft聊天消息以供玩家与```JustChat QQ机器人端```或```JustChat 消息转发控制中心```等使用。

## 安装
1. [下载插件](https://github.com/ExerciseBook/JustChat/releases/)
1. 复制jar文件到 [Sponge](https://www.spongepowered.org/)插件目录
1. 重启一次 Sponge ，使得插件生成插件配置文件
1. 使用 [notepad++](https://notepad-plus-plus.org/) 或 [Sublime Text](http://www.sublimetext.com/) 或 记事本 或 gedit 或 vim 等文本编辑器修改**并保存**配置文件
1. 重启 Sponge ， 使得修改后的配置文件生效。

## 配置文件
- 基础配置文件 ```config.conf```
	```
#服务器设置
server {
	# 本客户端的编号（随机生成）
	ID="f4b26361-0e49-4940-ba2a-05990cd2c6f1"
	
	# 欲连接的服务器的IPv4地址。
	ip="93.184.216.34"
	
	# 本客户端的名字
	name="Sponge服务器"
	
	# 欲连接的服务器的端口。
	port=38440
	
	# 客户端心跳包的时间间隔。0为关闭。(单位:秒)
	pulseInterval=20
}
	```
- 消息输出格式 ```locale.conf```
	```
# 消息显示格式
messageFormat {
    # 网页超链接显示格式 [未被使用]
    URL {arguments {CONTENT {optional=false}}closeArg="}"content {extra=[{color=bluetext="{CONTENT}"underlined=true}]text=""}openArg="{"options {closeArg="}"openArg="{"}}
    # QQ群消息AT(@)显示格式
    at {arguments {TARGET {optional=false}}closeArg="}"content {extra=[{color=bluetext="{TARGET}"}]text=""}openArg="{"options {closeArg="}"openArg="{"}}
    # QQ表情显示格式
    face {arguments {CONTENT {optional=false}}closeArg="}"content {extra=[{text="{CONTENT}"}]text=""}openArg="{"options {closeArg="}"openArg="{"}}
    # QQ表情地址
    faceURL="https://exercisebook.github.io/JustChat/resource/CQ/face/{ID}.{EXTENSION}"
    # 图片显示格式
    image {arguments {CONTENT {optional=false}}closeArg="}"content {extra=[{color=bluetext="{CONTENT}"underlined=true}]text=""}openArg="{"options {closeArg="}"openArg="{"}}
    # 整体消息显示格式
    overview {arguments {BODY {optional=false}SENDER {optional=false}}closeArg="}"content {color=resetextra=[{color="dark_green"text="{SENDER}"},{text=": "},{text="{BODY}"}]text="[*]"}openArg="{"options {closeArg="}"openArg="{"}}
    # 红包显示格式
    redEnvelope {arguments {TITLE {optional=false}}closeArg="}"content {extra=[{color=redtext="{TITLE}"underlined=true}]text=""}openArg="{"options {closeArg="}"openArg="{"}}
    # 一般富文本消息显示格式
    rich {arguments {TEXT {optional=false}}closeArg="}"content {extra=[{color=bluetext="{TEXT}"underlined=true}]text=""}openArg="{"options {closeArg="}"openArg="{"}}
    # 分享链接显示格式
    share {arguments {TITLE {optional=false}}closeArg="}"content {extra=[{color=bluetext="{TITLE}"underlined=true}]text=""}openArg="{"options {closeArg="}"openArg="{"}}
    # 普通文本消息显示格式
    text {arguments {CONTENT {optional=false}}closeArg="}"content {extra=[{text="{CONTENT}"}]text=""}openArg="{"options {closeArg="}"openArg="{"}}
}
	```