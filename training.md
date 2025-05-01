# 模型训练

在CantorAI Design Studio 集可视化建模、分布式调度、训练管理于一体。本手册将指导你如何在 Design Studio 中**配置、启动并监控一次完整的 AI 模型训练流程**。

------

## 第一步：新建或打开项目

1. 打开 CantorAI Design Studio。
2. 点击左上角【新建项目】或选择已有项目进入主界面。
3. 命名项目、设置项目目录并确认保存。



------

## 第二步：准备训练数据

1. 添加数据集。在dataset 文件夹里，添加图像数据；可添加多个文件夹或文件；
2. 设置标签信息（如分类标签、人脸、车辆等）；
3. 可使用【自动标注】功能由预置模型进行初步标注，再通过【手动标注】模块进行修正；



## 第三步：开始训练

在CantorAI Design Studia的训练界面：

- 新建或打开训练计划文件


![image-20250501075025854](/images/training-model-plan.png)

- 选择训练模型。选择不同的机器学习模型。下图显示，选择Detectron2模型进行训练。

![image-20250501075054394](/images/training-model.png)

- 配置超参数，根据选择的不同模型，配置与该模型相应的超参数。下图显示的是Detectron2模型的超参数配置界面。


![image-20250501075115097](/images/training-hyper-parameter.png)

- 数据集配置：给出放置标注图像数据文件的文件夹


![image-20250501075221190](/Users/zonghuanwu/Library/Application Support/typora-user-images/image-20250501075221190.png)

​	点击菜单有上街蓝色的运行按钮，开始训练

- 状态跟踪：训练开始，显示训练状态。


![image-20250501075246106](/images/training-status.png)

- 结果审视（35:50左右）

- 模型位置（37:57左右）

- 模型重用（38:11左右）