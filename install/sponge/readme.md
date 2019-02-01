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
#The server config
server {
	# 本J客户端的编号（随机生成）
	ID="f4b26361-0e49-4940-ba2a-05990cd2c6f1"
	# 欲连接的服务器的IPv4地址。
	ip="115.159.36.210"
	# 欲连接的服务器的端口。
	port=38440
	# 客户端心跳包的时间间隔。0为关闭。(单位:秒)
	pulseInterval=20
}
	```
- 消息输出格式 ```locale.conf```
	```
# 超链接文本输出格式
"MSGFormat_URL" {arguments {CONTENT {optional=false}}closeArg="}"content {extra=[{color=bluetext="{CONTENT}"underlined=true}]text=""}openArg="{"options {closeArg="}"openArg="{"}}
# AT(@)输出格式
"MSGFormat_at"  {arguments {TARGET {optional=false}}closeArg="}"content {extra=[{color=bluetext="{TARGET}"}]text=""}openArg="{"options {closeArg="}"openArg="{"}}
# 图片输出格式
"MSGFormat_image" {arguments {CONTENT {optional=false}}closeArg="}"content {extra=[{color=bluetext="{CONTENT}"underlined=true}]text=""}openArg="{"options {closeArg="}"openArg="{"}}
# 整体输出格式
"MSGFormat_overview" {arguments {BODY {optional=false}SENDER {optional=false}}closeArg="}"content {color=resetextra=[{text="[*]"},{color="dark_green"text="{SENDER}"},{text=": "},{text="{BODY}"}]text=""}openArg="{"options {closeArg="}"openArg="{"}}
# 普通文本输出格式
"MSGFormat_text" {arguments {CONTENT {optional=false}}closeArg="}"content {extra=[{text="{CONTENT}"}]text=""}openArg="{"options {closeArg="}"openArg="{"}}
	```