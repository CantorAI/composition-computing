# Build a pipeline 

#### **1. 流水线框架**

Galaxy 采用模块化流水线架构，帮助高效地管理分布式工作流。

- **Filters（过滤器）**：

  - 过滤器是 Galaxy 流水线的核心组件，每个过滤器表示一个处理单元。
  - 过滤器支持多个 **输入引脚（input pins）** 和 **输出引脚（output pins）** 来管理数据流。
  - DataFrame 通过引脚在过滤器之间流动，封装了需要处理的数据。

- **用户自定义过滤器**：

  - Galaxy 允许用户使用 **XLang** 作为胶水语言定义自定义过滤器。

  - 过滤器可以仅使用 XLang 实现，或者与 **Python**、**C++** 等编程语言结合实现。

  - 用户可以通过继承 `galaxy.BaseFilter` 定义一个自定义过滤器：

    ```xlang
    class Detectron_Filter(galaxy.BaseFilter):
        inputPin:Pin = None
        outputPin:Pin = None
    
        def Detectron_Filter():
            # 构造器逻辑
            this.inputPin = this.NewInputPin()
            this.inputPin.setputcallback(this.Process)
            this.outputPin = this.NewOutputPin()
    
        def Process(input_frame):
            # 处理 DataFrame 的自定义逻辑
            return output_frame
    ```

---

#### **2. 连接管理**

连接决定了 DataFrame 在过滤器之间的传递方式，为流水线设计提供了灵活性。

- **任务连接（Task Connections）**：
  - 使用 **Cantor 的任务调度器** 将下游过滤器作为独立任务执行。
  - DataFrame 被传递为任务输入。

- **强连接（Strong Connections）**：
  - 确保 DataFrame 在同一节点上的过滤器中处理，保持本地化操作。

- **弱连接（Weak Connections）**：
  - 允许 DataFrame 跨节点传递，支持分布式处理。

---

体验AI App的构建

Concepts:

**pipeline**

**filters**

### 