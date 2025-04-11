# 组合计算 （composition-computing）

## 组合计算：一种新型的计算架构
### [组合计算](composition-computing.md)

### [云计算、边缘计算和端计算](3-computing-architectures.md)

### [基于云计算、边缘计算和端计算的技术方案](computing-solutions.md)
### [计算发展的历史和趋势](computing-history-trend.md)



## Examples

### Installations

CantorAI组合计算框架支持多种机型、多种操作系统。安装了CantorAI计算框架的计算机可以跨操作系统、跨网络地相互连接，方便地组合形成一个算力和计算资源P2P网络。在任何一个节点发起的计算任务，都将由CantorAI计算框架的分布式任务分配根据对任务对计算资源的需要，优化分配给Cantor网络里的符合要求的节点。

在Linux系统下的安装

在Windows系统下的安装

在树莓派的Raspberry Pi OS系统下的安装

在MacOS系统下的安装

### Getting Started

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
  
    ![image-20250410163804589](C:\GitHub\composition-computing\images\need-authorization.png)
  
  - 当Node Authorization完成以后，再次打开https://localhost:9719 网址，会出现用户登录界面。
  
  - ![image-20250410143752245](C:\GitHub\composition-computing\images\login-screenshot.png)
  
  - 也可以在浏览器上输入任何一台其它联网节点的IP地址https://ip-address:9719，则可以访问它节点的CantorAI Design Studio。
  
    

### Authorization

- 租户注册
- 用户注册
- 节点注册

**CantorAI Portal**:CantorAI

![image-20250410162426942](C:\GitHub\composition-computing\images\authorization.png)

**CantorAI Tenants**

![image-20250410162216490](C:\GitHub\composition-computing\images\tenant-center.png)

**CantorAI Node**

![image-20250410162710355](C:\GitHub\composition-computing\images\nodes.png)

### Join the network

In this ue case, we will walk you through a use case how to setup a network of heterogeneous computers

**CantorAI Cluster**

**CantorAI Resource**

### Messaging in the network

### Task Scheduling

### Building a Webserver

### Preparing a simple pipeline

Concepts:

**pipeline**

**filters**

### Building a pipeline for  detecting objects in video

现有的Examples

**connectors**

### Add a filter

- filter的写法
  - femma: description的写法（gstreamer）。

### Monitoring System with Dashboard

### Model Integration 

### Annotations

Annotation refers to **labeling data** to train algorithms. For example

- Labeling photos of objects, such as, cats and dogs.
- Tagging parts of speech in a sentence.
- Highlighting spam in emails.
- Marking bounding boxes around objects in videos.

Annotations are needed in large-scale machine learning tasks, especially: 

**Supervised Learning** – Most ML models learn from labeled (annotated) data.

**Accuracy & Performance** – Better annotations → better training → better model results.

**Bias Reduction** – Well-annotated, diverse data helps models make fairer predictions.

**Interpretability** – Annotated examples help humans understand what models are learning.

In CantorAI Design Studio, we provide a few key annotation functions: 

Image Annotations

[An Example of Image Annotation in CantorAI Design Studio](image-annotation.md)

Automatic Annotations

Also, there are several tools for annotations.

Format Converter

### Training
