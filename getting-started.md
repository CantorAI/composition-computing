# Getting Started

#### **4. Galaxy Studio**

Galaxy Studio 是一个综合性的 GUI 工具，用于设计、管理和部署分布式流水线。

- **流水线设计**：
  - 提供拖放式界面，用于创建和配置由过滤器组成的流水线。
  - 支持直观管理连接类型（任务、强连接、弱连接）和数据流。

- **项目管理**：
  - 集中式仪表盘，用于管理流水线配置和部署。
  - 简化分布式工作流的协作和版本控制。

- **边缘中心（Edge Hub）**：
  - 专用 GUI，用于管理边缘设备注册和集群配置。
  - 支持设备与边缘节点的关联，并提供实时设备状态监控。

- **设备中心（Device Hub）**：
  - 与 Edge Hub 集成，管理单个设备的状态和配置。

---

With this example, you will be able to login to CantorAI Design Studio for the first time and enter the gate of the world of CantorAI's composition computing platform. 

##### Concepts:

- **CantorAI Design Studio**: It is a front-end tool designed to 

  - ease most of your configurations of your composition computing network with simple mouse clicks and a few keystrokes,

  - visualize your network assets and their organization, 

  - help to construct your apps with a visualized pipeline building mechanism,

  - customize dashboard and monitor systemetic, applicational  matrics

  - customize the 

  However, CantorAI Design studio should not be regarded as a all-in-one venue to conduct all the development. We do assume its user has reasonable knowledge how CantorAI technology works. 

  

  Example：启动CantorAI Design Studio

  - 在装有Cantor计算框架的任意节点，执行Cantor命令，即可启动Cantor系统。在这个时候，在本机打开互联网浏览器（如chrome，Firefox等），在地址栏输入：https://localhost:9719，则可以运行本机的CantorAI Design Studio。

    - 第一次启动Cantor系统时，出于安全和许可证验证的要求，系统会要求您在CantorAI将该计算节点注册。您会看到以下界面。计算节点注册需要在CantorAI门户网站完成，详情请参考下一个Node Authorization案例。

    ![image-20250410163804589](images/need-authorization.png)

  - 当Node Authorization完成以后，再次打开https://localhost:9719 网址，会出现用户登录界面。

    ![image-20250410143752245](images/login-screenshot.png)

- 也可以在浏览器上输入任何一台其它联网节点的IP地址https://ip-address:9719，则可以访问它节点的CantorAI Design Studio。
