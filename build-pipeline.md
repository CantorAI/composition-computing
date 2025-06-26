# 3.4.1 构建流水线

`流水线`（Pipeline）是CantorAI计算平台的核心概念之一。

### **What**

**CantorAI Pipeline 是基于组合计算理念构建的一种分布式流水线系统，结合 XLang、Cantor 和 Galaxy 三大组件，实现从数据采集、标注、训练、应用开发到部署与运维的全流程闭环自动化执行。**

1. **本质（What it is）**
   CantorAI Pipeline 是在 Galaxy 框架上运行的一个分布式任务执行机制，支持组件化、模块化的 AI 应用工作流管理。其底层由 Cantor 提供动态任务调度与资源管理，XLang 提供脚本和模型封装能力，Galaxy 组织这些单元为可视化、可复用的任务链。
2. **核心特性（Key Features）**
   - **基于 DataFrame 的数据流图（Data Bus）**：以 DataFrame 为基本传输单位，构建数据流网络；
   - **Filter 编程模型**：每个 AI 模型或算法组件都封装为一个 Filter，可重用、可部署；
   - **自动任务调度与资源绑定**：通过`资源表达式`进行调度（如 `GPU >= 1`），并自动路由到合适节点；
   - **支持异构环境部署**：从边缘节点、IoT 设备，到云端集群均可运行同一套流水线；
   - **低代码/零代码开发**：通过可视化拖拽与 XLang 脚本结合设计流程。
3. **组成阶段（Workflow Phases）**
   - **数据采集与标注**：支持多源实时采集与分布式标注工具；
   - **模型训练**：支持分布式训练与在线监控；
   - **应用开发**：支持视觉类、LLM类、大数据类 AI 应用开发；
   - **部署执行**：零部署开销，支持一键发布至所有节点；
   - **实时监控与安全**：集成日志、时序指标系统与零信任计算模型。
4. **技术优势（Why it’s unique）**
   - **组合计算框架下的流水线架构**，任务与资源解耦，弹性调度；
   - **完全去中心化（P2P）集群编排机制**，无单点故障；
   - **适配 AI 和 IoT 混合场景**，可在边端云统一部署 AI 任务。

### **How**

构建一条 CantorAI 流水线（Pipeline），主要包括以下六个阶段：

#### **1. 新建或打开项目**

在[项目管理](project-management.md)一节中讲到，使用 **CantorAI Design Studio** 的project 页面打开/创建一个项目空间。用户的项目可以是视频识别、物体检测、IoT 监控等用户准备进行开发的任意 AI 应用场景。在项目的pipeline子目录中，可以新建/打开Pipeline文件。从下图可以看到，Pipeline文件是以YAML格式存储。

![image-20250501184738735](/images/pipeline-files.png)

------

#### **2. 设计数据流图：拖拽式构建 Filter 节点**

- 在 CantorAI Design Studio 中用拖拽方式放置 **Filter** ，每个Filter都一个都计算模块（如模型推理、图像解码、数据分流等）；

  ![image-20250501184930706](/images/pipeline1.png)

  上图展示了一个通过将5个过滤器相连构建的一个视频目标识别的Pipeline。这个pipeline由 initiator, fermat, tee, Detectron2和player等五个过滤器构成。从左边的面板中，可以将过滤器鼠标拖拽到中间区域进行编辑（排列，连接等）；在右边的面板中，可以对当前流水线中选中的滤波器或连接进行必要的配置。

  在上图中，

  - `Initiator`过滤器是 Galaxy 分布式流水线系统中的一种特殊类型的滤波器（Filter），其主要作用是**在分布式数据处理流水线中充当数据流的起点，用于主动发起数据流并触发后续的处理逻辑。**
  - `Fermat`  分布式滤波器，名字取自数学家费马（Fermat），作为一个**高性能图像帧处理模块**，处理视频流数据。它与 `GStreamer` 等外部系统集成，接收视频帧并推入数据管道中进行处理或分析。
  - `Tee` 过滤器在 CantorAI 的 Galaxy 分布式流水线系统中，**扮演“数据复制器”的角色**。它的作用是：**将同一个输入 DataFrame 同步分发到多个输出端口（Output Pins）**，使得下游的多个模块可以**并行处理相同的数据副本**。在上图的流水线中，Tee过滤器将同样的数据帧分发给下游的`Detectron2`过滤器和`Player`过滤器。
  - `Detectron2`过滤器封装了 Facebook Research 出品的 Detectron2 目标检测模型（例如 Faster R-CNN、Mask R-CNN 等），用于从上游传递过来的数据帧中的视频帧中识别出物体类别、位置等信息。
  - 在 **播放器 过滤器（`Player` Filter）** 主要用于**播放数据帧**，例如图像序列、视频帧或其他视觉数据，是数据展示和验证的重要环节。在上图的流水线中，作为最后一个过滤器，`Player`播放了从`tee`滤波器传来的原始视频数据帧，同时也叠加播放了从`Detectron2`传过来识别物体的类型标签和位置（方框）信息。

- 在[过滤器](filters.md)一节中，我们详细介绍过滤器。

- 通过连接箭头定义数据流的输入输出逻辑。

- 在[流水线连接](connectors.md)一节中，我们详细介绍流水线里的连接。

------

#### **3. 编写 XLang 脚本（可选，增强逻辑）**

- 每个 Filter 可绑定一个 XLang 脚本，定义处理逻辑，如：

```
def run(input: DataFrame) -> DataFrame:
    img = decode_image(input["image"])
    result = model_infer(img)
    return {"boxes": result}
```

- 支持调用 Python、C++、外部库等。

------

#### **4. 设置资源条件与部署策略**

- 在每个 Filter 上配置资源条件（CPU/GPU/摄像头等）：

```
resource: "GPU >= 1 AND Camera == True"
```

- 系统自动根据 Cantor 的资源图谱调度任务到满足条件的节点。
- 关于Filter的详情，请见[过滤器](filters.md)一节。

------

#### **5. 一键部署到边/云/终端**

- 使用 CantorAI Design Studio 的“一键部署”功能：
  - 流水线结构、XLang 脚本、依赖项将自动下发到对应节点；
  - 自动进行网络拓扑连接与 DataFrame 路由设置；
  - 支持边云协同部署、按需激活节点。

------

#### **6. 实时监控与调试**

- 在 CantorAI Design Studio 可视化面板中查看：
  - 每个 Filter 的执行频率、数据吞吐量；
  - GPU/CPU 占用；
  - 日志输出；
  - 支持热更新脚本与热迁移节点。
