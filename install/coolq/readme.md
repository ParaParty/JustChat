# [安装与架设](../)/QQ机器人 酷Q机器人

## 概述
- JustChat 的核心协议和路由模块均写在酷Q机器人插件中。

## 特性
- 服务组 : 允许将多个 QQ 群和多个 Minecraft 服务器的聊天信息转发到一起。
- 设置隔离 : 允许不同群和不同服务组使用不同的 JustChat 设置。
- 内容隔离 : 允许一个机器人同时为多个不同的服务组提供服务。

## 升级
- 如果您是从 `1.x` 版本升级而来，因插件配置文件改动较大，无法自动升级。请先备份原有设置文件，清理设置目录后再升级插件。

## 安装
1. [下载插件](https://github.com/ExerciseBook/JustChat/releases/)
1. 复制cpk文件到 [酷Q](https://cqp.cc)插件目录
1. 重启一次 酷Q ，使得插件生成插件配置文件
1. 使用 [notepad++](https://notepad-plus-plus.org/) 或 [Sublime Text](http://www.sublimetext.com/) 或 记事本 或 gedit 或 vim 等文本编辑器修改**并保存**配置文件
1. 重启 酷Q ， 使得修改后的配置文件生效。

## 配置文件
- 本插件使用的配置文档均以**UTF-8无BOM**形式储存。
- 基础配置文件 `config.json`
<details>
  <summary>json 格式</summary>

```jsonc
{
	/// 配置文件版本
	"version": {
		"config": 2 
	},

	/// JustChat 连接服务设置
	"connection": {

		/// 服务器模式设置
		"server": {
			"enable": true,
			"port": 38440
		},

		/// 客户端模式设置 (暂未支持)
		"client": {
			"enable": false,
			"address": "",
			"port": 38440
		},

		"name": "", // 本终端名称
		"ID": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" // 本终端编号 ( UUID 格式 )
	},

	/// 服务组设置
	"services": [
		
		/// 一个服务组
		{
			/// 这个服务组的绑定设置
			"bind": {
				/// 和哪些QQ群绑定
				"qqgroups": [
					123456, xxxxxx
				],
				/// 和哪些 Minecraft 服务器绑定，依然是 UUID 格式
				"minecraft": [
					"xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
				]
			},
			/// 这个服务组的特殊设置，具体介绍见后文
			"events": {
				"PlayerList_All": false // 这里覆盖了全局设置里的一个开关
			}
			"message_format": {
				"Info_PlayerJoin": "[%SERVER%] %SENDER% 来搬砖辣！",
				"Info_PlayerDisconnect": "[%SERVER%] %SENDER% 退出搬砖。"
			}
		},

		/// 另一个服务组
		{
			"bind": {
				"qqgroups": [
					xxxxxx
				],
				"minecraft": [
					"xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
				]
			},
			"message_format": {
				"Message_Overview": "[*][%WORLD_DISPLAY%]%SENDER%: %CONTENT%"
			}
		}
	],

	/// 对于QQ群的特殊设置
	"qqgroups": [
		/// 一个QQ群的特殊设置
		{
			"groupid": 123456,
			"config": {
				"events": {
					"PlayerList_All": true // 这里覆盖了一个服务组设置里的一个开关
				},
				"message_format": {
					"Message_Overview": "[*][%WORLD_DISPLAY%]%SENDER%: %CONTENT%"
				}
			}
		}
	],

	/// 全局设置
	"global_configuration": {
		/// 设置开关
		"events": {
			"Registration_All": true,
			"Info_All": true,
			"Info_PlayerNetwork": true,
			"Info_PlayerDeath": true,
			"Info_Other": true,
			"Message_All": true,
			"PlayerList_All": true
		},
		/// 消息输出格式
		"message_format": {
			"Info_General": "[%SERVER%] %CONTENT%",
			"Info_PlayerJoin": "[%SERVER%] %SENDER% joined the game.",
			"Info_PlayerDisconnect": "[%SERVER%] %SENDER% left the game.",
			"Info_PlayerDead": "[%SERVER%] %SENDER% dead.",
			"Message_Overview": "[*][%SERVER%][%WORLD_DISPLAY%]%SENDER%: %CONTENT%",
			"Message_ImageAlternative": "[IMAGE]",
			"PlayerList_Layout": "[%SERVER%] There are %NOW%/%MAX% players online.%PLAYERS_LIST%",
			"Registration_online": "Server %NAME% is now online.",
			"Registration_offline": "Server %NAME% is now offline."
		}
	}
}
```
</details>

### 设置

#### 设置开关
- 不区分大小写

|        Key         |        Type        |            描述            |                相关输出格式                     |
|:------------------ |:------------------:|:------------------------- |:--------------------------------------------- |
| Registration_All   | `boolean`          | 服务器上下线提示             | `Registration_online`, `Registration_offline` |
| Info_All           | `boolean`          | [提示] 提示开关              | 所有以 `info` 开头的输出格式*                    |
| Info_PlayerNetwork | `boolean`          | [提示] 玩家上下线提示         | `Info_PlayerJoin`, `Info_PlayerDisconnect`    |
| Info_PlayerDeath   | `boolean`          | [提示] 玩家死亡提示           | `Info_PlayerDead`                            |
| Info_Other         | `boolean`          | [提示] 其他提示              | `Info_General`                                |
| Message_All        | `boolean`          | 聊天信息显示                | `Message_Overview`                            |
| PlayerList_All     | `boolean`          | 查询在线玩家列表开关         | `PlayerList_Layout`                           |

```
* 由于数据包中可能存在预设文本，因而 Info 开头的输出格式可能会被数据包中的预设文本覆盖。
```


#### 消息输出格式
- `key` 不区分大小写
- 默认值参考上文中的配置文件样例。

|        Key            |            描述            |
|:--------------------- |:--------------------------|
| Info_General          | [提示] 通用提示输出格式      |
| Info_PlayerJoin       | [提示] 玩家加入游戏提示      |
| Info_PlayerDisconnect | [提示] 玩家退出游戏提示      |
| Info_PlayerDead       | [提示] 玩家死亡提示         |
| Message_Overview      | 聊天信息显示               |
| Message_ImageAlternative      | 游戏内 [图片] 替换文本 |
| PlayerList_Layout     | 在线玩家列表输出格式         |
| Registration_online   | 服务器上线提示               |
| Registration_offline  | 服务器下线提示               |



## 命令

### 查询在线玩家列表
1. 支持版本: `1.2.0` 到 `未定`
1. 命令: `/list`, `/ls`, `!list`, `!ls`
1. 权限: 全体群成员