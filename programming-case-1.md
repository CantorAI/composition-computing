# 示例1：XLang 调用范式

通过一个简单示例，介绍CantorAI (XLang)  的调用范式，直观地了解CantorAI API。假设我们要编写一个分布式程序，完成以下任务流程：

**场景**：有一组传感器数据文件，我们想并行读取文件 -> 进行阈值过滤 -> 汇总结果计数。

**CantorAI 实现**（使用 XLang 和 Galaxy Pipeline）：可以将其构造成三步流水线，每步一个Filter：

1. 读取文件 Filter（读取文件数据，输出数据帧）
2. 阈值过滤 Filter（判断数据是否超标，输出标记结果）
3. 汇总 Filter（收集结果，可以把每次结果写入全局计数）

XLang 代码示例：

```python
# 假设已 import cantor 并获取 galaxy 对象
class FileReader(galaxy.BaseFilter):
    output: Pin = None
    def FileReader():
        this.output = this.NewOutputPin()
    def Process(dummy_frame):
        # 读取文件逻辑，假设文件名列表预存在全局 list_files
        if list_files:
            fname = list_files.pop()  # 取一个文件
            data = fs.File(fname).read() 
            frame = galaxy.NewDataFrame()
            frame.data = data
            this.output.put(frame)

class ThresholdFilter(galaxy.BaseFilter):
    input: Pin = None
    output: Pin = None
    def ThresholdFilter():
        this.input = this.NewInputPin()
        this.input.setputcallback(this.Process)
        this.output = this.NewOutputPin()
    def Process(frame):
        data = frame.data
        result = (data > threshold)  # 简单判断
        out_frame = galaxy.NewDataFrame()
        out_frame.data = result
        this.output.put(out_frame)

class Aggregator(galaxy.BaseFilter):
    input: Pin = None
    def Aggregator():
        this.input = this.NewInputPin()
        this.input.setputcallback(this.Process)
        global count_exceed
        count_exceed = 0
    def Process(frame):
        global count_exceed
        if frame.data == True:
            count_exceed += 1
        print("Current exceed count:", count_exceed)

# 构建并运行流水线
pipeline = galaxy.Pipeline()  # 伪代码，实际用LoadYamlPipeline或API创建
f1 = pipeline.AddFilter(FileReader)
f2 = pipeline.AddFilter(ThresholdFilter)
f3 = pipeline.AddFilter(Aggregator)
pipeline.Connect(f1.output, f2.input)
pipeline.Connect(f2.output, f3.input)
pipeline.Run()
```

在上面的 CantorAI 代码中，我们定义了三个 Filter 类，每个封装相应步骤逻辑，然后连接成 pipeline 并运行。FileReader 每触发一次会读取一个文件并输出数据帧，ThresholdFilter 对每帧判断阈值并传递布尔结果，Aggregator 收集统计。由于 FileReader 没有输入，我们可以在流水线启动时人为触发它（或者配置为Initiator定时触发）。整个流程一旦Run，调度器就会自动安排这些Filter在节点上执行，直到文件列表空为止。开发者无需关注这些处理在哪个节点执行、如何并行——CantorAI 自动调度FileReader可能分布到各存储节点，ThresholdFilter任务并行执行，Aggregator作为汇总运行。只需关注业务逻辑本身。