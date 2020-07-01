# [安装与架设](../)/Minecraft Sponge 服务端

## 概述
- JustChat 的 Sponge 端插件。

## 安装
1. [下载插件](https://github.com/ParaParty/JustChat/releases/)
1. 复制 jar 文件到 [Sponge](https://www.spongepowered.org/)插件目录
1. 重启一次 Sponge ，使得插件生成插件配置文件
1. 使用 [notepad++](https://notepad-plus-plus.org/) 或 [Sublime Text](http://www.sublimetext.com/) 或 记事本 或 gedit 或 vim 等文本编辑器修改**并保存**配置文件
1. 重启 Sponge ， 使得修改后的配置文件生效。

## 配置文件
- 基础配置文件 `config.conf`
```conf
# 服务器设置
server {
	# 本终端编号
	ID="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
	
	# 本终端名称
	name="Sponge服务器"

	# 欲连接的服务器的地址
	ip="mcserver.example.com"
	
	# 欲连接的服务器的端口
	port=38440
}

# 功能设置
functionControl {

    # 将游戏角色死亡信息的游戏中原始消息转发到QQ群
    # 当本设置开启时，QQ群设置中的 Info_PlayerDead 会被 Info_General 覆盖
    forwardPlayersDeadOriginalMessages=true

    # 将玩家上下线信息的游戏中原始消息转发到QQ群
    # 当本设置开启时，QQ群设置中的 Info_PlayerJoin、Info_PlayerDisconnect 会被 Info_General 覆盖
    forwardPlayersLoggingAndDisconnectionMessages=false
}

```
- 消息输出格式 `locale.conf`

## 指令
### `/justchat`
- 介绍 : 主设置指令
- 用法 : `/justchat`
- 基础权限 : `justchat.admin`

### `/justchat reload`
- 介绍 : 重载插件配置
- 用法 : `/justchat reload`
- 基础权限 : `justchat.admin.reload`

## 权限
| 权限 | 说明 |
|:----|:-----|
|`justchat.admin`|管理员设置指令|
|`justchat.admin.reload`|重载插件配置指令|
|`justchat.forward.chat`|允许将聊天信息发送到QQ群|
|`justchat.forward.network.*`|允许将上下线信息发送到QQ群|
|`justchat.forward.network.join`|允许将上线信息发送到QQ群|
|`justchat.forward.network.disconnect`|允许将下线信息发送到QQ群|
|`justchat.forward.death`|允许将游戏角色死亡信息发送到QQ群|
