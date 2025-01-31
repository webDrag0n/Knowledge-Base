- #Windows
- 本文转自https://blog.mozui.cn/article/kms，https://blog.kuretru.com/kms/， https://blog.kuretru.com/posts/888cb050/，如有侵权，请联系删除。
- ### 激活Office
  Office的激活略为复杂，推荐使用[Office Tool Plus](https://otp.landian.vip/zh-cn/)软件。
- **安装Office：**
- 产品：`Microsoft 365企业应用版`(O365ProPlusRetail)
- Visio选择：`Visio 专业版 2019 - 批量版本`(VisioPro2019Volume)
- 应用程序：你需要的，一般御三家(Word、Excel、PowerPoint)
  **激活Office：**
- 许可证管理：`Office Mondo 2016 - 批量版`(MonodoVolume)
- Visio选择：`Visio 专业版 2019 - 批量版本`(VisioPro2019Volume)
- KMS管理：`kms.kuretru.com`
  [KMS服务器](https://blog.mozui.cn/article/kms#10bceacdb8b480a7983ce4158ba2b211)
  [[Windows KMS激活]]
- 手动激活方法
  找到Office的安装目录，使用管理员打开cmd或Windows Power Shell，并切换到该目录，输入以下命令：
  ```powershell
  cscript ospp.vbs /inpkey:{对应Office的密钥}    #设置新密钥
  cscript ospp.vbs /sethst:kms.kuretru.com     #设置KMS服务器地址
  cscript ospp.vbs /act                        #立即尝试激活
  cscript ospp.vbs /dstatus                    #查看激活状态
  ```
  下表为一些常见的Office密钥，若表中没有出现你需要的Office版本，可以在这里查找完整的列表：[Office 2019 & Office 2016](https://docs.microsoft.com/zh-cn/DeployOffice/vlactivation/gvlks)，[Office 2013](https://docs.microsoft.com/zh-cn/previous-versions/office/dn385360(v=office.15)?redirectedfrom=MSDN)，[Office 2010](https://docs.microsoft.com/zh-cn/previous-versions/office/office-2010/ee624355(v=office.14)?redirectedfrom=MSDN)。
- |Office版本|密钥|
  |Office LTSC Professional Plus 2021|FXYTK-NJJ8C-GB6DW-3DYQT-6F7TH|
  |Visio LTSC Professional 2021|KNH8D-FGHT4-T8RK3-CTDYJ-K2HT4|
  |Office Professional Plus 2019|NMMKJ-6RK4F-KMJVX-8D9MJ-6MWKP|
  |Visio Professional 2019|9BGNQ-K37YR-RQHF2-38RQ3-7VCBB|
  |Office Professional Plus 2016|XQNVK-8JYDB-WJ9W3-YJ8YR-WFG99|
  |Visio Professional 2016|PD3PC-RHNGV-FXJ29-8JK7D-RJRJK|
  |Office 2013 Professional Plus|YC7DK-G2NP3-2QQC3-J6H88-GVGXT|
  |Visio 2013 Professional|C2FG9-N6J68-H8BTJ-BW3QX-RM3B3|
  |Office Professional Plus 2010|VYBBJ-TRJPB-QFQRF-QFT4D-H3GVB|
  |Visio Premium 2010|D9DWC-HPYVV-JGF4P-BTWQB-WX8BJ|