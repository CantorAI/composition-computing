# 5.1 Cantor APIs

Cantor是组合计算的计算框架。提供了以网络操作、数据操作、节点操作以及各类指标管理为对象的一系列XLang语言编程APIs。

5.1.1 [Cantor Host APIs](apis/cantor/cantor_host_apis.md)

Cantor 主机类提供了多个应用程序编程接口（APIs），这些接口可以通过 XLang 来访问，用于与数据视图、数据帧以及运行时操作进行交互。这些 API 被设计为既可以在 Cantor 进程内部使用（直接导入），也能从一个独立进程使用（通过共享内存进行远程访问）。也就是说，开发人员可以利用 XLang 通过这些 API 在不同场景下对 Cantor 系统中的数据视图、数据帧等进行操作，无论是在 Cantor 自身运行环境内，还是在与之独立的其他进程中，只是在独立进程中采用共享内存方式来实现远程访问。例如，在一个数据分析项目中，若使用 Cantor 系统进行数据处理，主程序在 Cantor 进程内可直接调用 API 处理数据，而辅助的监控程序作为独立进程，就可通过共享内存远程调用 API 获取数据视图状态。

5.1.2 [Dataframe APIs](apis/cantor/dataframe_apis.md)

Cantor DataFrame 类提供了一套全面的 API，用于与数据帧进行交互和操作。它包括用于元数据、格式和数据管理的属性，以及用于访问和修改数据帧内容的函数。

5.1.3 [Metrics APIs](apis/cantor/metrics_apis.md)

Metrics 类为 Cantor 框架中的指标管理和查询提供了一个全面的接口。它支持为各种对象和实例注册、查询和删除指标。

 5.1.4 [Network APIs](apis/cantor/network_apis)

Cantor网络类提供了一个简化的接口，用于管理网络操作，如启动/停止服务器、连接到服务器以及处理网络事件。