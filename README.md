# MIUI Task
一个适用于 小米社区 4.0 自动完成成长值任务的脚本

[![996.icu](https://img.shields.io/badge/link-996.icu-red.svg)](https://996.icu) ![GitHub](https://img.shields.io/github/license/0-8-4/miui-auto-tasks) 
![Python](https://img.shields.io/badge/python-3.7+-blue) ![DockerHub](https://github.com/0-8-4/miui-auto-tasks/actions/workflows/docker-image.yml/badge.svg)


## **关于项目**:

  受`東雲研究所` 的某位大佬启发  
  最初的源码由大佬授权 `0-8-4` 使用 `MIT` 开源   
  项目初期由`0-8-4` 和 `TardisLX` 进行维护，现已逐渐转为社区驱动
  我们认为小米社区无权在无任何回报的情况下强制要求内测用户完成 KPI 任务，因此诞生了这个脚本


## **重要声明**:
- 虽然理论上本脚本不会影响小米社区账户安全，但您需要自行承担使用本脚本的后果

- **我们不鼓励，不支持一切商业使用**
  - 鉴于项目的特殊性，我们可能在任何时间 **停止更新** 或 **删除项目**


### **使用说明**：
关于项目的详细使用方法请阅览 **[WiKi](https://github.com/0-8-4/miui-auto-tasks/wiki)**


### **项目依赖**：
  1. 需要前往 Python 官网自行下载自己系统对应的 Python 版本，或使用自己系统对应的包管理安装，推荐至少 Python 3.6 以上

  ```
  https://www.python.org/downloads/
  ```

  2. Python 3 安装完成之后，请在 **项目目录** 执行以下命令安装所需模块
  ```bash
  pip install -r requirements.txt
  ```
  注意：你可能需要使用管理员权限运行命令行


### **项目介绍**：  
- [x] 支持 多账号 配置
- [x] 支持 Docker 部署
- [x] 支持 腾讯云函数 部署
- [x] 自动登录小米账号刷新社区 Cookie 实现自动化   
- [x] 选择性启用参与小米社区拔萝卜
- [x] 选择性启用小米社区每日签到
- [x] 选择性启用小米社区限时专题任务
- [x] 自动完成以下小米社区成长值任务且不留下可见痕迹  
  - “每日登录小米社区App” 成长值任务
  - “浏览帖子超过10秒” 成长值任务  
  - “点赞他人帖子” 成长值任务  
  - “浏览个人主页超过10秒” 成长值任务
  - “加入小米社区圈子” 成长值任务

&#x26A0; 请注意，修改配置文件开启完成限时专题任务后 MIUI Task 不会检测当前是否可完成限时专题任务而会直接发送请求，根据社区相关规则，启用完成限时专题任务、拔萝卜及签到等可能存在风险。您需要自行承担使用本脚本的后果


### **配置推送**：
推送基于[onepush](https://github.com/y1ndan/onepush)
- 推送名称 / notifier: bark

  参数大全 / params:
  {'required': ['key'], 'optional': ['title', 'sound', 'isarchive', 'icon', 'group', 'url', 'copy', 'autocopy']}

- 推送名称 / notifier: custom

  参数大全 / params:
  {'required': ['url'], 'optional': ['method', 'datatype', 'data']}

- 推送名称 / notifier: dingtalk

  参数大全 / params:
  {'required': ['token'], 'optional': ['title', 'secret', 'markdown']}

- 推送名称 / notifier: discord

  参数大全 / params:
  {'required': ['webhook'], 'optional': ['title', 'username', 'avatar_url', 'color']}

- 推送名称 / notifier: pushplus

  参数大全 / params:
  {'required': ['token'], 'optional': ['title', 'topic', 'markdown']}

- 推送名称 / notifier: qmsg

  参数大全 / params:
  {'required': ['key'], 'optional': ['title', 'mode', 'qq']}

- 推送名称 / notifier: serverchan

  参数大全 / params:
  {'required': ['sckey', 'title'], 'optional': []}

- 推送名称 / notifier: serverchanturbo

  参数大全 / params:
  {'required': ['sctkey', 'title'], 'optional': ['channel', 'openid']}

- 推送名称 / notifier: telegram

  参数大全 / params:
  {'required': ['token', 'userid'], 'optional': ['title', 'api_url']}

- 推送名称 / notifier: wechatworkapp

  参数大全 / params:
  {'required': ['corpid', 'corpsecret', 'agentid'], 'optional': ['title', 'touser', 'markdown']}

- 推送名称 / notifier: wechatworkbot

  参数大全 / params:
  {'required': ['key'], 'optional': ['title', 'markdown']}
* **required为必填参数，optional为选填参数**

配置参考：
```yaml
ONEPUSH:
  notifier: telegram
  params:
    title: 
    markdown: false
    token: 123456789:XXXXXXXXXXXXXXXXXXXXXXXX
    userid: 114514
```
```yaml
ONEPUSH:
  notifier: pushplus
  params:
    title: 
    token: XXXXXXXXXXXXXXXXXXXXXXXX
    markdown: false
```
#### **其他**：  
* 在使用本脚本时请临时关闭网络代理工具及广告拦截程序  
* 在服务器上使用前建议先使用服务器IP登录 `https://account.xiaomi.com`  
* 建议配合 Python3 及 Crontab 使用  
* **欢迎提供有关的思路，提交BUG以及更多完成社区其他任务方式，我们会认真对待~**


#### **贡献**：

如果你在使用过程中发现任何问题，可以 [提交 issue](https://github.com/0-8-4/miui-auto-tasks/issues/new) 或自行 Fork 修改后提交 Pull request

如果你要提交 Pull request，请确保你的代码风格和项目已有的代码保持一致，遵循 [PEP 8](https://www.python.org/dev/peps/pep-0008) ，变量命名清晰，有适当的注释


# **License**
```
MIT License

Copyright (c) 2021 東雲研究所

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
