#### **11. 动态部分代码分发**

Cantor 支持动态部署代码，消除了手动分发的需求。

- **零部署**:

  - 在任务执行期间，代码和依赖项会自动传输到目标节点。

- **示例**:

  ```python
  @cantor.Task(NPU=1 and OS == 'Windows')
  def test_func(x, y):
      p_id = pid()
      sleep(200)
      y = x + y
      print("pid:", p_id, ",x=", x, ",y=", y)
      z = x + y
      print("z=", z)
      return [p_id, x + y]
  ```

  - 任务通过装饰器（如 `@cantor.Task`）定义，可使用 `test_func.run(parameters)` 跨集群执行。
  - Cantor 自动管理依赖项、全局变量和执行上下文。