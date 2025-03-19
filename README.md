<h2 id="uV6xv">关于Hawkeye</h2>
本工具为安全分析、应急响应、事件响应、DFIR、安全服务等岗位从业人员设计的一个图形化Windows安全分析工具，涵盖常见Windows安全分析场景，能够有效的发现Windows主机存在的安全威胁。工具整体实现由go语言编写，通过调用Windows系统API获取主机相关信息，并将常见需要分析的事件ID展示在图形化界面，无需去记忆繁杂的Windows事件id，小白也能很快的上手进行分析，大幅度降低使用门槛。

工具集成了yara扫描的功能，用户可以根据自身需要编写yara规则，对进程进行威胁检索，程序自身使用elastic security相关规则，涵盖大部分已知的安全威胁。并且程序提供了友好的数据复制功能，在编写安全报告时，直接复制数据即可使用。

<h2 id="JvNIk">支持平台</h2>
Windows7-Windows11

<h2 id="TaXg1">核心特点</h2>

+ **进程信息**：能够查看当前主机相关进程，并且支持查看相关进程加载的DLL模块，支持文件跳转，进程终止等功能

+ **外连分析** ：通过外连IP快速定位异常进程，并输出常见的自启动维持项。

+ **beacon扫描** ：集成BeaconEye模块，检索当前系统的CobaltStrike异常进程

+ **主机信息**：涵盖常见分析场景，主机用户、计划任务、服务、自启动等信息，并对可执行文件路径采用yara进行扫描，并进行提示。

+ **日志分析**：涵盖Windows常见Windows事件id分析场景，如登录成功、登录失败、RDP登录、SqlServer、服务、Powershell等。

+ **进程扫描**：引入yara扫描引擎，对当前系统进程进行扫描，用户可以在输入框内输入yara规则路径，并且可以通过修改hawkeye目录下的rules文件下规则，进行定制化修改。

+ **活动痕迹**：工具对常见活动痕迹进行了采集，如Prefetch文件解析、UserAssit活动记录以及Recent文件夹信息，查看主机历史的操作记录。

+ **内存检索**：能够通过指定字符串对进程进行检索，可用于僵尸网络、恶意外连、挖矿病毒等相关场景。

**PS：重点是程序大小仅****10.4****MB，upx压缩后程序仅****4.21****MB大小，无需安装即开即用，方便快速上机进行使用。并且在网络传输过程中也能够节省大量时间。**

<h2 id="yUldm">功能</h2>
<h3 id="L1O2d">进程信息</h3>
该功能能够查看当前主机所有的进程信息包含进程名称、父进程pid、父进程名称、进程创建时间、可执行文件路径、MD5等关键信息，点击相关进程后能够查看当前进程加载的DLL模块信息，并且右键支持进程信息复制以及文件跳转等功能

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742307243865-9a08456e-f566-4f17-821c-8050e371fd9a.png)

<h3 id="VZRWz">外连助手</h3>
旨在发现异常外连后，通过外连ip及时发现相关程序进程以及常见维持项信息，方便进行快速的分析处置的工作。

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742307435639-ae49b7ad-51aa-4292-9f24-5a35c9f460e3.png)

<h3 id="Y8cMM">beacon扫描</h3>
该功能会遍历当前系统进程信息，并且找出CobaltStrike加载的进程，并解析相关信息。

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742307523741-6db20972-baa5-4729-9f59-29fcb7b16703.png)

<h3 id="pEGCw">主机信息</h3>
主机信息模块包含了用户信息、计划任务、服务信息、启动项信息以及镜像劫持

用户信息会标识当前系统存在的隐藏账户，并进行提示

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742307596423-de2a3515-8304-4e1b-8ad0-95d62f5c8b60.png)

计划任务模块，会检索当前系统存在的计划任务信息，并且调用yara扫描模块，检索是否存在恶意程序。

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742307616707-de87e603-53d7-4e4a-b1cd-f17af2ecfe14.png)

同理计划服务、启动项以及镜像劫持等功能也会展示相关信息，并调用yara扫描模块，对这些常见维持项进行扫描。

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742307667942-8eaaa36c-5018-49e8-bae9-d873ed3dd7f4.png)

<h3 id="KawnZ">日志分析</h3>
日志分析模块，涵盖常见Windows应急分析过程中，常见的Windows事件，如登录成功、登录失败、RDP登录、RDP连接、服务创建、用户创建、sqlserver日志以及powershell日志等信息。

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742307738505-21d589ea-2947-4e3f-9143-90f946eb6ede.png)

并且在服务创建模块中会对异常服务信息进行标记，发现可能被横向攻击的服务日志。

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742307884492-6a04de66-1233-4d7e-bb0f-b4b3bd655b02.png)

在sqlserver日志中也会对异常的组件激活行为进行标识。

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742307900712-4b4f271d-ded4-453e-a8d0-31a001d8d873.png)

同理在powershell日志分析模块中也会对异常的powershell命令进行标记，发现安全风险。

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742307954002-d215c29e-c562-4141-9676-b258c891fb3b.png)

<h3 id="PxfGd">进程扫描</h3>
进程扫描采用了yara扫描的功能，能够对当前系统进程进行扫描，发现异常风险。若发现异常进程，会将相关信息打印在告警日志面板。

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742308051917-796809dc-464e-4383-b5f8-c12746c487e6.png)

该功能采用了elastic security的yara规则，在HawkEye同级目录下的rules文件夹中，用户可以将自己编写的yara规则放在该目录下，文件后缀为.yara，如果在其他目录下放有yara规则，程序提供了输入框，可以根据相关规则路径，进行引入。

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742308292264-9cd9fc7c-df97-4aec-9a5b-03a43eee2e60.png)

<h3 id="l9RIF">活动痕迹</h3>
主机会采集当前系统Prefetch文件、UserAssit以及Recent文件夹相关信息进行展示，方便用户分析主机实现时攻击者通过RDP进行操作的相关记录。

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742308360250-80fdbd99-cfda-4252-a6af-53b63745d661.png)

<h3 id="pgipi">威胁检索</h3>
该功能会对当前主机内存进行字符串检索，常用于异常域名外连的使用场景，方便快速定位可疑进程。

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742308536604-6d85ab07-9dae-44dc-bd89-a75a8df5762e.png)

<h2 id="TpccW">各平台运行效果</h2>
Windows11

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742310038052-bd8da13b-4329-47c4-bbb4-1ee41cce7f6a.png)

Windows Server 2019

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742310073966-d97d0d95-7e4c-47f6-a998-f6cb2ff25cb5.png)

Windows7

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742310142774-dae577b5-33d1-4aaa-81e9-a246dde92d80.png)

<h2 id="On2n9">其他问题</h2>
1、程序需要在管理员权限下进行使用，如果在非管理员权限运行，程序提示权限不够。

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742310281410-a81732fa-bc0a-45c9-b871-96d3e6d08cd9.png)

2、程序退出时会有直接退出或者托盘运行的提示，根据用户需要选择退出方式，点击yes程序会直接退出。

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742310349565-459fe148-588c-4021-b5c0-870d9d28c8e6.png)

如果是托盘运行，退出程序后，需要在托盘处选择退出，程序即可退出。

![](https://cdn.nlark.com/yuque/0/2025/png/26746188/1742310389574-9d0353be-d0ba-4d7a-b107-6e4c99eed0f5.png)

<h2 id="A9Xnf">其他</h2>
1、本程序默认使用elastic security的yara检测规则

[https://github.com/elastic/protections-artifacts](https://github.com/elastic/protections-artifacts)

2、图形化框架开发使用govcl

[https://github.com/ying32/govcl/](https://github.com/ying32/govcl/)

3、Beacon扫描模块采用了EvilEye该项目并对相关程序进行修改

[https://github.com/akkuman/EvilEye](https://github.com/akkuman/EvilEye)

<h2 id="dl1R9">杂谈</h2>
程序迭代好几个版本了，最初Windows日志只支持常见的登录日志，后面又对日志进行了扩充，再也不用记那些繁杂的Windows事件id了，想想当初自己记那些id就头疼，有时还得翻阅笔记。再后面又引入yara规则对文件进程等信息进行扫描，大幅减轻常见分析常见的分析场景，还支持数据复制的功能，减轻写分析报告的压力。至于文件检索的功能，就不写了，Everything更好用，哈哈哈哈哈，写的话也是调用Everything的SDK，没必要，用它就好。



至于Issue提到的进程排序，目前看了下，程序是自动根据pid从小到大进行排列，然后govcl这个框架也没琢磨出来怎么再listview表单中去实现，也不想写了，主要是懒，当然写这个程序的初衷也是因为懒，哈哈哈哈，懒得记那些繁杂的id还得用logparse去敲命令如果是看Windows事件管理器，看的脑壳痛还有的不是要关注的类型、懒得手工使用certutil去计算进程相关文件的md5，也懒得每次分析事件托一大堆工具上去，总之就是因为懒，哈哈哈哈哈。



个人觉得这个工具有点像个大杂烩，哈哈哈，所以就勉强叫他是综合性的Windows应急分析工具吧。为啥不加响应，也没写自动处置的功能，而且处置这一块的东西，还是需要人去分析后再去处置，如果加了处置，万一出问题了呢，哈哈哈哈，再一个，一下子就处置了，咋写报告，还得截图啥的，哈哈哈哈。



然后就是会被杀软查杀的问题了，go不知为啥，我写个helloworld都能给我杀，后面捉摸着是内嵌入yara规则的问题，就索性不嵌入了，直接丢到当前目录下得了，也方便大家自己diy rules文件夹下的规则。之前内嵌，看到有小伙伴丢到微步上去了，看了下报告，说这个程序又是勒索、又是蠕虫、还又是红队工具(黑人问号.jpg)。自己看到都觉得好笑，哈哈哈哈。现在直接舍弃内嵌。



最后希望大家使用愉快。

<h2 id="mtF4n">免责声明</h2>
<font style="color:rgb(31, 35, 40);">免责声明：此工具仅限于安全研究，用户承担因使用此工具而导致的所有法律和相关责任！作者不承担任何法律责任</font>
