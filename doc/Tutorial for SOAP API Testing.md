# SOAP 请求

在 Katalon Studio 中发送 SOAP 请求时，您可以收到来自 API 服务器的响应以进行检查和故障排除。本节包括如何创建 SOAP 请求对象的教程，以及在打开的编辑器中对请求服务的每个字段的介绍。

## 创建基于 SOAP 的请求

1. 从主菜单中，选择 **File > New > Web Service Request**。

2. 在**New Web Service Request** 对话框中，在**Request Type**列表中选择**SOAP ，然后单击****OK**创建一个新的 SOAP 对象。

   ![](Tutorial for SOAP API Testing.assets/img-008-01.png)

3.  在Katalon Studio的**对象存储库**下创建了一个**新的**请求对象。

   

## 添加 SOAP 请求详细信息

成功创建请求后，双击请求以打开其编辑器以添加详细信息。在**新请求**对象的打开编辑器中，您可以看到请求对象的所有必需信息。

![](Tutorial for SOAP API Testing.assets/img-008-02.png)

### 请求方法

request 方法指示要在指定资源上执行的预期操作。Katalon Studio 支持以下 SOAP 方法：SOAP、SOAP 1.2、POST、GET。默认情况下，Katalon 选择 SOAP 作为新 SOAP 请求的方法。

![](Tutorial for SOAP API Testing.assets/img-008-03.png)

### WSDL 网址

此字段用于 WSDL 路径，Katalon Studio 从该路径将内容导入此 SOAP 请求。

![](Tutorial for SOAP API Testing.assets/img-008-04.png)

### 服务功能

您要在此 SOAP 请求中使用的函数。单击**Load Service Function**时，您可以从 WSDL 文件中检索可用的服务功能列表。

![](Tutorial for SOAP API Testing.assets/img-008-05.png)

每个 Service Function 都携带自己的内容，包括 Service Endpoint、SOAPAction Header 和 Request 消息。

在**Service Endpoint**中，您可以指定另一个 URL，指示此请求的所需服务端点。

![](Tutorial for SOAP API Testing.assets/img-008-06.png)

### 请求认证

这部分用于对请求进行认证和授权，即验证是否允许客户端发送请求并执行端点操作。

有关使用每种身份验证的更多详细信息，请参阅：

- [基本的](https://docs.katalon.com/katalon-studio/docs/authorization-basic.html)
- [OAuth 1.0](https://docs.katalon.com/katalon-studio/docs/authorization-oauth1.html)
- [OAuth 2.0](https://docs.katalon.com/katalon-studio/docs/authorization-oauth2.html)

![](Tutorial for SOAP API Testing.assets/img-008-07.png)

### 请求标头

标头信息需要与此 SOAP 请求一起发送。您可以从建议选项列表中选择标题（通过双击**名称**单元格）或输入您感兴趣的另一个标题。有关详细信息，请参阅[支持的 HTTP 标头](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers)。

![](Tutorial for SOAP API Testing.assets/img-008-08.png)

### 请求消息

您要在此 SOAP 请求中传输的信息。点击所选服务功能的**加载新内容**后即可获取。

![](Tutorial for SOAP API Testing.assets/img-008-09.png)

## 回复

发送服务请求后，Katalon Studio 从服务器检索消息并将其显示在请求的**响应**视图中。服务响应包括状态、经过时间和大小字段；正文部分、标题和验证日志。

- **Status** : 响应的状态码
- **Elapsed**：从请求开始发送到 Katalon Studio 收到响应的最后一个字节的总时间
- **Size** : 响应包的大小

### 响应体

有 2 种查看格式：**pretty**和**raw**。例如，SOAP 的响应`http://www.dneonline.com/calculator.asmx?WSDL`如下所示。

- 漂亮的格式
  ![](Tutorial for SOAP API Testing.assets/img-008-10.png)

- 原始格式

  ![](Tutorial for SOAP API Testing.assets/img-008-11.png)

### 响应头

响应的标头显示在 **标头** 选项卡中。

### 验证日志

此选项卡显示请求经过测试和验证后的验证结果。[有关如何在 Katalon Studio 中验证 API 响应的](https://docs.katalon.com/katalon-studio/docs/verify-api-responses.html#verifying-rest-response-in-json-format)信息，请参阅此文档。

**也可以看看：**

- [参数化 Web 服务对象](https://docs.katalon.com/display/KD/Parameterize+a+Web+Service+Object)
- [验证片段](https://docs.katalon.com/display/KD/Verification+Snippets)
- [在测试用例中使用 Web 服务](https://docs.katalon.com/display/KD/Using+Web+Services+in+a+Test+Case)

