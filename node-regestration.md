# 节点注册

当安装用户在计算节点安装了Cantor，首次启动Design Studio，在浏览器里访问`https://localhost:9719`时，会得到一个类似下图的页面。页面显示当前节点尚未被认证，尚未加入到用户的CantorAI集群里。

![image-20250420100754355](/images/node-registration-interface.png)

用户需要：

- 首先点击页面上的co py按钮，将注册节点所需要的认证信息拷贝到剪贴板；
- 访问`https://portal.cantorai.com`，用自己的CantorAI用户账号登陆CantorAI Portal。
- 在`admin`页签，选择租户（也是用户的CantorAI集群），将认证信息粘贴到`Authorize Node`域内。如下图：

![image-20250420102307667](/images/portal-node-admin-page.png)

​	注：进行节点注册前，假设用户已完成`租户注册`和`用户注册`。

- 点击`Authorize`按钮，即完成节点注册，将该节点加入了租户集群。这时，回到Design Studio界面, 用户可以看到，等待节点认证界面已经被用户登录界面所取代。

  ![Screenshot 2025-04-20 at 10.43.24 AM](/images/user-login-page.png)