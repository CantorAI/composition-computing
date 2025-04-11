# 图像标注

**目标**

对一个包含不同动物（猫、狗）的图像数据集，，进行人工标注，并用于训练图像分类模型或目标检测模型。**图像标注目标**则是对每一张图像中出现的狗进行**边界框标注**（框出动物所在的位置和种类）

**CantorAI 标注工具**

![image-20250409183641246](images\cats-dogs-original.png)

CantorAI提供多种标注工具，最常用的就是：

- 关键点标注（Keypoint Annotation）：标记物体或人体上的关键点，用于人脸五官点、人手指关节点、动物骨骼点，常用于：姿态估计、人脸识别、动作识别等

- 线段标注（Polyline/Line Annotation）：用线条标注目标（如车道线、道路边界），常用于自动驾驶中的道路结构识别等。

- 矩形边界框（Bounding Box）标注：用最小矩形框框住目标物体，适用于目标检测（如 YOLO、Faster R-CNN、Detectron）等模型。

![image-20250409184445725](images\cats-dogs-annotated.png)

- 多边形（Polygon）边界框标注：用任意多边形精确描绘目标轮廓，更适用于形状不规则的物体（如人、建筑），用于精细语义分割任务（如 Mask R-CNN）等。
- 骨架结构标注（Skeleton Annotation）：CantorAI Designer Studio还提供了特有的能够快速对人、动物或其他结构物体进行以关键点为基础的骨架结构进行标注的工具。

![image-20250410161927861](images\skeleton-annotation.png)