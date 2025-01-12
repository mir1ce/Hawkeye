## Hawkeye 一款Windows综合应急响应工具
### 简介
Hawkeye(鹰眼)一款基于goalang开发的安全工具，旨在帮助安全工程师上机排查时能够快速的定位问题，提供排查思路。

### 程序运行报错的问题
运行反馈服务器返回一个参照，如下图所示，鼠标右键->属性->兼容性->勾选以管理员身份运行此程序，点击应用就好了
![微信截图_20250110095450](https://github.com/user-attachments/assets/666c18f1-f5f8-4898-b590-cf943d900036)


### 功能
#### 外连分析
当发现主机存在恶意外连时，并且知道外连地址，能够快速的定位外连的进程，以及进程的连接信息。同时根据进程定位到对应的文件以及常见维持项。该功能适用于常见的外连场景，如挖矿，木马，后门等。
如下图所示，以todesk为例，通过外连分析功能，能够快速的定位到todesk.exe进程，以及进程的连接信息。

![image](https://github.com/user-attachments/assets/8473373c-3fc3-4738-a27b-7d886ed3e11f)


#### Beacon扫描
适用于主机存在C2外连场景，该功能能够快速的扫描主机上的beacon信息，包括beacon的进程信息，beacon的连接信息等。
![image-1](https://github.com/user-attachments/assets/e4ffdd85-625f-464f-b5e4-21a96662c682)


#### 主机信息
该功能能够查看常见的主机信息，具体如下：

- 用户信息
能够查看当前主机用户，以及主机是否存在隐藏账号
![image-2](https://github.com/user-attachments/assets/18c9318e-cd3b-435e-99c2-aa9179c0d88e)


- 计划任务
查看当前主机的计划任务以及触发时间
![image-3](https://github.com/user-attachments/assets/c2a58c87-5706-4813-ab2d-efceefcc489a)


- 服务信息
![image-4](https://github.com/user-attachments/assets/8aeb05af-c5c1-4544-a547-e906a57fe44b)


- 启动项信息
![image-5](https://github.com/user-attachments/assets/96247878-5e84-462d-a048-cb5d49519f49)


#### 日志分析
- 登录成功日志
该功能会获取当前主机所有登录成功的日志，包括用户名，登录时间，登录IP等信息。
![image-6](https://github.com/user-attachments/assets/3eb5ff28-0f24-4dd5-a470-42de8e3289ef)


- 登录失败日志
该功能会获取当前主机所有登录失败的日志，包括用户名，登录时间，登录IP等信息。
![image-7](https://github.com/user-attachments/assets/49fd82c4-d501-405e-954a-7b1c294ca9ec)


- 服务创建日志
该功能会获取当前主机所有服务创建的日志，包括服务名，服务路径等信息。
![image-8](https://github.com/user-attachments/assets/7ec6bf90-7766-4828-8fa8-bda9dcc6a25c)


- 用户创建日志
该功能会获取当前主机所有用户创建的日志，包括用户名，用户路径等信息。方便安全工程师查看是否存在可以账号的创建。
![image-9](https://github.com/user-attachments/assets/97f7beb6-8a72-4416-a381-eb6de600acf4)


### Todo
1、yara进程、文件扫描
2、新增其他日志项，如计划任务、powershell、RDP等

### 微信公众号
更多安全问题，请关注微信公众号，获取更多信息。或者微信公众号后台联系作者，加入交流群，获取更多信息。
![qrcode_for_gh_121aa154068a_430](https://github.com/user-attachments/assets/ada22b22-a230-4a91-a784-332a7fb7ac57)

## Stargazers over time
[![Stargazers over time](https://starchart.cc/mir1ce/Hawkeye.svg?variant=adaptive)](https://starchart.cc/mir1ce/Hawkeye)
