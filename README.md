CantorAI 系统详细介绍，也即组合计算“白皮书” 

# 组合计算 （composition-computing）

## 组合计算：一种新型的计算架构
### [组合计算](composition-computing.md) 

### [计算发展的历史和趋势](computing-history-trend.md)

### 当前的计算的架构和技术方案​

#### [计算架构](3-computing-architectures.md)

#### [技术方案](computing-solutions.md)

### 组合计算的计算架构和CantorAI技术方案

#### [计算架构](composition-computing-architecture.md)

#### [技术方案](cantorai-solution.md)

#### [编程模式](programming-pattern.md)

## 开始使用CantorAI

### [安装CantorAI](cantorai-installations.md)

`组合计算`是跨边端云、跨操作系统的方案，可以在多型系统上快速安装CantorAI。

### [开始使用](getting-started.md)

通过`CantorAI Design Studio`，在CantorAI网络的计算节点上首次上手体验组合计算。

### [注册和认证](cantorai-authorizations.md)

通过CantorAI门户网站（CantorAI Portal），完成租户、用户和节点设备注册，体验零信任安全机制。

[租户注册](tenant-registration.md) 

[用户注册](user-registration.md)​ ​

[节点注册](node-registration.md)​

[节点检测](node-inspect.md)

## 主要功能

### [项目管理](project-management.md)

CantorAI Design Studio提供简单的项目管理功能，用户可以组织管理包括集群组网，流水线构建、部署和运行，数据标注和训练等各种开发大规模计算项目所需的项目和各子任务。

### [组网](join-the-network.md)​

将多个计算节点连接，组成你的CantorAI网络。

### [节点间的通信](messaging.md)

“Hello World!” 恭喜，随着信息在各节点之间传播，你联通CantorAI Network上的节点和计算资源。

### 流水线

[构建流水线](build-pipeline.md)

用户主要通过构建流水线来开发应用。

[过滤器](filters.md)​​

流水线由过滤器和连接器构成，本节介绍过滤器。

[流水线连接](connectors.md)

流水线由过滤器和连接器构成，本节介绍连接。

[流水线运行](run-pipeline.md)

通过一键，完成分布式流水线在全集群的部署和运行。

#### [任务调度](task-scheduling.md)

资源分配的组合计算任务调度。



### [指标监控和日志](monitoring.md)

本案例展示如何通过仪表板监控系统、应用和资源的各种指标。

### [标注](annotation.md)

本案例展示标注功能

### [机器学习训练](training.md)

本案例展示如何训练机器学习模型。

## 进阶主题

### CantorAI编程

通过简单的流水线配置和程序，CantorAI流水线能力对外开放，通过API服务将功能嵌入其他的系统。

[案例一：展示XLang编程范式的简单案例](programming-case-1.md)

[案例二：实时目标检测流水线](programming-case-2.md) 

[案例三：LLM 闭环交互流水线](programming-case-3.md)

[案例四：综合应用示例](programming-case-4.md)

### 7.4 案例对比分析

通过以上案例，可总结CantorAI在应用层面的主要特点是：

* **设计范式**：CantorAI 倾向于**配置驱动**和**流程编排**，开发者更多在配置/模块中声明做什么，更接近无代码/低代码理念（特别有Galaxy Studio辅助）。
* **实时处理**：CantorAI 针对实时、多媒体等应用有专门优化（如Galaxy Fermat处理视频帧，强连接降低延迟）。
* **复杂控制流**：CantorAI 通过Switch等组件能表示一定的条件和循环，但对于非常复杂的逻辑（比如跨多个不同流水线的条件），可能通过直接代码更为清晰。
* **服务集成**：CantorAI 自身可以胜任构建一体化服务应用，这意味着CantorAI方案适合从零打造新的分布式应用平台。
* **应用场景**：从案例看，CantorAI 非常适合**边缘AI**（摄像头检测）、**连续智能应用**（LLM agent循环）以及**统一AI平台**（类似main.x集成训练、推理、多节点服务于一体）。

一个有趣的观察是：CantorAI 案例常涉及**硬件资源**（摄像头、GPU）和**混合场景**（IoT + AI + Web），这是因为CantorAI试图提供一个贴近业务场景的全栈分布式方案。对于企业来说，如果需求侧重于构建具体AI应用（尤其跨边缘和云），CantorAI的案例表明它能更省力地完成。

### 模型集成 

通过在设计器中增加新的机器学习模型，将新的过滤器引入系统。

## API库

CantorAI为开发者提供APIs

### [Cantor APIs](cantor-apis.md)

### [Galaxy APIs](galaxy-apis.md)

### [CantorAI平台的项目开发模式](development-pattern.md)



### [概念列表](concept-list.md)
