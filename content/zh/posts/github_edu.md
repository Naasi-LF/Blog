---
title: "Github_edu"
date: 2025-03-22T20:24:28+08:00
draft: false
description: "github copilot教程"
tags: ["copilot"]
categories: ["教程"]
---
# Github Copilot学生认证申请与使用指北（以常工院学生为例）

## UserName与Name的区别

| **Aspect** | **Name**                                    | **Username**                        |
| :--------- | :------------------------------------------ | :---------------------------------- |
| **定义**   | 显示名称（可以是真实姓名,例如XiCheng Yang） | GitHub 账户的唯一标识符（Naasi-LF） |
| **用途**   | 展示在个人资料或提交记录中                  | 登录 GitHub、个人页面 URL           |
| **唯一性** | 不需要唯一                                  | 必须唯一                            |
| **修改**   | 可随时修改                                  | 也可以修改，**但需谨慎**            |

在实际使用中，**Name** 是你的展示信息，更偏向于个人风格；而 **Username** 是账户的技术标识，影响你的 GitHub URL 和账户关联。

在修改名称时候，注意修改的是**Name**！！！

## 公开资料

在设置(Settings)中，修改成如下内容：

![image-20250322194820049](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322194820049.png)

确保首页中的信息替换成如下形式：

![image-20250322194226134](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322194226134.png)

## 电子邮箱

电子邮箱中，添加学校邮箱的账号：

![image-20250322194506420](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322194506420.png)

注意，使用**czust.edu.cn**后缀而非czu.cn。

## 支付信息

**无需绑卡**，只需填写相关支付信息即可

![image-20250322195308635](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322195308635.png)

## 双重认证

需要开启双重认证（部分人之前已有）

![image-20250322195613116](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322195613116.png)

## 学籍认证

使用学信网[学历查询_中国高等教育学生信息网（学信网）](https://www.chsi.com.cn/xlcx/index.jsp)进行学籍认证，获得如下pdf文档

![image-20250322200131384](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322200131384.png)

英文文档最好，亲测中文也可以。

然后**打印**下来（方便手机拍照）

## 开始申请

申请请用手机打开网址！！！！

申请请用手机打开网址！！！！

申请请用手机打开网址！！！！

进入后最好不要打开代理（打不开用流量）。

打开[Get your GitHub benefits - GitHub Education](https://education.github.com/discount_requests/application)网址，注意登录github账号。

![image-20250322200723915](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322200723915.png)

Proof type选择other(学信网属于other)

输入一行文字：在文本框输入：
```
Ministry of Education online verification report
```

## 申请完成

一旦您的学术福利准备就绪，您将收到一封电子邮件通知（[GitHub benefits](https://link.zhihu.com/?target=https%3A//education.github.com/discount_requests/application)中右侧显示**绿色的Approved**表示审核通过但学生福利未到账，**紫色的Approved**表示学生福利已到账，这个到账的过程通常需要三天以上，到账后会有邮件通知）

![image-20250322200949658](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322200949658.png)

![image-20250322201118193](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322201118193.png)

## 订阅

本工作容易被忽略!

在github pro权益到来之后，**coplit是不会自动到账的**，还需要手动订阅，否则使用的就还是free版本，方法是访问[订阅网址](https://link.zhihu.com/?target=https%3A//github.com/github-copilot/signup),点击订阅。

![img](https://picx.zhimg.com/v2-3b1ff92b76530e4559bd24115cbd0823_1440w.jpg)

## 使用

### 方法1

使用[GitHub Copilot官网](https://github.com/copilot/)

### 方法2

下载Vscode上的Coplit插件即可（注意是pro会员）

| 操作                | 快捷键（Windows） | 快捷键（Mac）   | 说明                                    |
| ------------------- | ----------------- | --------------- | --------------------------------------- |
| 激活 Copilot        | Ctrl + Shift + P  | Cmd + Shift + P | 打开命令面板，搜索并启动 Copilot 功能。 |
| 提示补全            | Alt + \           | Option + \      | 激活 Copilot 自动补全。                 |
| 显示代码建议        | Ctrl + Space      | Cmd + Space     | 提供代码建议或自动补全。                |
| 插入建议            | Tab               | Tab             | 插入 Copilot 提供的建议。               |
| 打开或关闭 Copilot  | Ctrl + Shift + I  | Cmd + Shift + I | 启用或禁用 Copilot。                    |
| 显示 Copilot 对话框 | Ctrl + Enter      | Cmd + Enter     | 显示 Copilot 对话框，方便与其交互。     |
| 查看完整建议        | Ctrl + .          | Cmd + .         | 查看 Copilot 提供的完整代码建议。       |
| 查看 Copilot 设置   | Ctrl + Shift + S  | Cmd + Shift + S | 打开 Copilot 设置，进行个性化调整。     |
| 重载 Copilot        | Ctrl + Shift + R  | Cmd + Shift + R | 重载 Copilot 插件，重新加载其配置。     |

tab大法好（

### 检验是否是会员的方法

有这些preview模型选择即是会员

![image-20250322201748314](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322201748314.png)

## 进阶操作

场景：文字转图

文字如下：

```bash
设备缺陷追踪模块构建了覆盖检测全流程的智能化追溯体系，通过数据流监控、过程回溯与预警干预的深度融合，实现了缺陷识别过程的可视化跟踪与闭环管理。该模块采用层次化架构设计，在任务全生命周期管理、实时状态感知、版本控制等方面形成技术闭环，确保从缺陷发现到处置验证的全链条可追溯性。
在任务全生命周期管理层面，系统建立了多维度数据采集与存储机制，完整记录从任务创建至处理反馈的完整链路。每个检测任务在初始化阶段即生成全局唯一追溯标识，动态采集设备参数、资源分配状态、推理中间结果等关键信息。任务执行过程中，系统持续跟踪GPU/CPU资源占用、内存波动等硬件指标，同步记录特征图演化、置信度变化曲线等模型内部状态，形成包含时空维度信息的立体化数据档案。通过非关系型数据库集群与图数据库的协同工作，既实现了海量过程数据的高效存储，又构建了跨环节的数据血缘图谱，为后续溯源分析提供结构化支持。
实时监控子系统基于事件驱动架构构建，通过观察者模式实现系统状态的动态感知。系统定义了涵盖数据输入、模型推理、结果输出等环节的核心事件体系，每个事件节点注册对应的监听处理逻辑。当检测到低置信度预警、硬件超温等异常信号时，触发机制将自动启动多级响应流程，根据预设策略执行通知发送、工单创建或服务降级等操作。监控指标覆盖计算、传输、存储各层级，采用百分位统计方法分析推理时延分布特征，实时监测消息队列堆积深度，并通过集群健康度评估预判潜在风险，形成预防性维护能力。
数据版本控制体系贯穿整个追踪流程，采用双重保障机制确保追溯数据的完整性与可复现性。模型版本管理引入大文件存储技术，每次推理任务关联模型哈希值与训练参数快照，实现算法迭代过程的精准追溯。输入数据采用差异存储策略，在保证存储效率的同时完整保留原始数据特征。针对关键推理环节，系统通过容器快照技术固化运行时环境，配合可视化对比工具实现不同版本特征图的热力学分析，为模型优化提供直观依据。
智能预警机制采用动态阈值调整策略，构建了分层递进的应急响应体系。系统根据历史数据建立缺陷模式知识库，当检测到同类缺陷重复出现、硬件负载超限等异常模式时，自动激活对应的处置预案。预警信息处理流程引入优先级排序算法，结合响应时效要求智能选择通知渠道，在预设时间内未获响应时自动提升处理级别。该机制与运维系统深度集成，支持从预警生成到工单关闭的全流程状态跟踪，确保问题处置形成有效闭环。
异常追踪技术依托日志分析体系构建了立体化诊断能力。通过日志采集组件实时捕获容器运行时信息，运用模式识别算法自动提取异常特征。系统提供时间反查调试功能，可基于时间戳回放特定时刻的推理过程，结合保存的中间张量数据进行问题复现。针对复杂异常场景，支持通过数据血缘图谱追溯关联环节，快速定位异常根源。该技术体系大幅提升了系统故障的诊断效率，为持续优化检测模型提供数据支撑。
该模块通过上述技术体系的有机整合，形成了具备自我诊断与进化能力的智能追踪系统。各子系统间采用标准化接口进行数据交互，既保持功能模块的独立性，又通过统一的消息格式确保系统整体协同。在设计上预留扩展接口，可兼容数字孪生、知识图谱等新型技术的后续接入，为构建更完善的设备健康管理体系奠定技术基础。
```

vscode创建.tex文件

可 拖进去相关的上下文

![image-20250322201941736](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322201941736.png)

加上一些prompt即可（分为聊天和编辑功能，聊天会将信息在聊天框打出，而编辑功能可支持修改，创建文件，适合软件项目开发，但是速度比聊天模式慢一些）

建议使用**Claude3.7**进行代码生成。若需要识图，可使用gpt4o模型先将图转文字，再用Claude3.7(因为这里只有4o支持识图)

将tex进行编译(可使用texlive+vscode 或 overleaf进行编译)

![image-20250322202801038](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322202801038.png)

似乎生成的很丑？

![image-20250322202926552](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322202926552.png)

因为生成的是矢量图，使用Adobe Acrobat DC或Adobe Illustrator或Inkscape等编译软件进行简单编辑即可

![image-20250322203807661](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250322203807661.png)

经过微调可这样快速生图。




