# Detectron2 滤波器

Detectron2 滤波器**是集成于 CantorAI 平台流水线框架**中的高级计算机视觉模块。它封装了 Facebook 开源的 Detectron2 模型，支持目标检测、实例分割和关键点检测，将这些功能打包成可复用、可编排的**滤波器**，可部署在边缘、云端或终端设备上，实现真正的多场景智能视觉能力。

**基于 DataFrame 的数据流处理**：接收并输出 GalaxyDataFrame 格式的数据，支持图像和视频数据处理，支持二进制或 ndarray 格式转换。

### 实例

![image-20250501062912806](/images/detectron2-filter.png)

在上图中，上游`fermat`滤波器将视频流转换成JPEG数据帧，经`tee`分发，数据帧经过`Detectron2`进行物体目标物体识别，识别信息（物体类别名和位置）输出给下游`player`滤波器。

Detectron2 滤波器帮助用户构建可扩展的视觉智能系统，将先进的 AI 模型与 CantorAI 的组合计算能力无缝结合。