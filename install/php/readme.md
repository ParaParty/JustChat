# [安装与架设](../)/PHP消息转发控制中心
## 概述
- `JustChat PHP消息转发控制中心` 用于接受来自其他 `JustChat 客户端` 的消息并处理转发到其他的 `JustChat 客户端`。

## 安装
1. [下载插件](https://github.com/ExerciseBook/JustChat/releases/)
1. 解压得到`JustChat PHP消息转发控制中心` 的代码
1. 确保系统变量 `Path` 中存在 PHP 的路径
1. 使用 [notepad++](https://notepad-plus-plus.org/) 或 [Sublime Text](http://www.sublimetext.com/) 或 记事本 或 gedit 或 vim 等文本编辑器修改**并保存**配置
1. 运行本程序
	1. Windows下执行 `start_for_win.bat`
	1. Linux下执行 `php start.php start -d`
		
## 配置
- 配置文件 `Applications\JustChat\start_gateway.php`  
	```
	// gateway 进程，这里使用Text协议，可以用telnet测试
	// 既 JustChat PHP消息转发控制中心 所侦听的ip地址与端口
	$gateway = new Gateway("JustChat://0.0.0.0:8282");

	// gateway名称，status方便查看
	$gateway->name = 'JustChat';

	// gateway进程数
	$gateway->count = 4;

	// 本机ip，分布式部署时使用内网ip
	$gateway->lanIp = '127.0.0.1';

	// 内部通讯起始端口，假如$gateway->count=4，起始端口为4000
	// 则一般会使用4000 4001 4002 4003 4个端口作为内部通讯端口 
	$gateway->startPort = 2900;
	```