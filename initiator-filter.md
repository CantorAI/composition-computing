# 启动器过滤器

**Initiator Filter（启动器过滤器）** 是CantorAI分布式流水线系统中的一种特殊类型的滤波器，其主要作用是：

> **在分布式数据处理流水线中充当数据流的起点，用于主动发起数据流并触发后续的处理逻辑。**

1. **触发机制**：它负责激活整条数据处理管道。
2. **与任务调度解耦**：通过 Initiator Filter 的定义，数据驱动与后续执行解耦，使得系统更具灵活性与可组合性。

### 举例

![image-20250501062706502](/Users/zonghuanwu/github/composition-computing/initiator-filter.png)

由上图可见，在这个流水线中，第一个滤波器是`initiator`滤波器，被用户命名为“Start”。它没有输入脚`Input Pins`。有一个输出脚`Output Pins`，连到下游的`Fermat`滤波器。在它的描述里，表明`initiator`滤波器作为Pipeline的启动器。