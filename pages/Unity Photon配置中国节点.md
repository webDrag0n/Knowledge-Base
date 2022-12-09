- ## photon 网址
  
  >  https://dashboard.photonengine.com/zh-CN
  
  先创建一个app，这里的appid等等会用到
- ## 中国区
- > https://vibrantlink.com/
- ## 步骤
- 访问中国区官网
  ![image.png](../assets/image_1670552818742_0.png)
- 填写信息，填写之前复制的appid，一般两个工作日
- 按正常流程安装配置Unity photon插件
- 搜索LoadBalancingClient.cs
  ![image.png](../assets/image_1670552837317_0.png){:height 241, :width 620}
- 修改 NameServerHost， 由 ns.exitgames.io 改为 ns.photonengine.cn
  ![image.png](../assets/image_1670552855961_0.png)
- PhotonServerSettings 的 Fixed Region 设置为 cn
-