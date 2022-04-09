# 设置 WinAppDriver

本文档向您展示如何在执行 Windows 桌面应用程序测试之前在 Windows 10 计算机上安装和运行 Windows 应用程序驱动程序 (WinAppDriver)。

> 什么是测试机（test machine）？
>
> 测试机是您安装和测试被测应用程序的地方。

> 什么是测试运行器（test runner machine）？
>
> - 测试运行器是您安装 Katalon Studio 和存储测试脚本的地方。
> - 测试运行器和测试机可以是同一台机器，也可以是不同的机器（远程连接）。

## 在 Windows 10 机器上安装并运行 WinAppDriver

### 安装 WinAppDriver

> 笔记：
>
> 在测试机上安装并运行 WinAppDriver。

在 Windows 10 机器上安装 WinAppDriver 有两种方法：

1. 从 Katalon Studio 工具栏中，选择**Tools > Windows > Install WinAppDrivers**。**Windows 应用程序驱动程序设置**窗口打开。按照说明安装 Windows 应用程序的驱动程序。
2. 您也可以参考这里的 WinAppDriver Github 项目文档：[安装并运行Windows 应用程序驱动](https://github.com/microsoft/WinAppDriver#installing-and-running-windows-application-driver)进行安装。

### 运行 WinAppDriver

1. 在测试机上启用**开发者模式。**您可以在此处参考 Microsoft 文档：[启用您的设备进行开发](https://docs.microsoft.com/en-us/windows/uwp/get-started/enable-your-device-for-development)以获取说明。
![](../img/zs/img-025-01.png) 
2. 默认情况下，WinAppDriver 安装在`C:\Program Files (x86)\Windows Application Driver`. 要运行 WinAppDriver，请双击`WinAppDriver.exe`安装目录中的文件。

## 为远程连接设置 WinAppDriver

### 在 Windows 10 测试机上

> 笔记：
>
> - 运行测试时，请确保已打开 WinAppDriver 并为 Windows 10 测试机上的远程连接进行配置。

安装 WinAppDriver 并启用**开发者模式**后，要配置 WinAppDriver 以进行远程连接，请按照下列步骤操作：

1. 打开**任务管理器**> 选择**文件**> 创建新任务。

2. 选择**使用管理权限创建此任务**`cmd`并在**打开**文本框中输入，然后单击**确定**按钮。
![](../img/zs/img-025-02.png)
3. 运行`cd`命令，到您的 WinAppDriver 安装文件夹。默认情况下，它位于`C:\Program Files (x86)\Windows Application Driver`.

4. 运行`WinAppDriver.exe <IP_Adress> <Port>`。

   - `IP_Adress`: 是测试机的公网IP地址。运行`ipconfig.exe`以确定 IP 地址。
   - `Port`: 是远程机器的公共端口。默认情况下，它应该是 4723。
![](../img/zs/img-025-03.png)
   > 笔记：
   >
   > 如果测试机处于带有防火墙的高度安全环境中，您可能需要为测试机创建入站端口规则，用以接收入站请求。要设置入站规则，您可以按照 WinAppDriver 项目文档中的步骤：[创建入站端口规则](https://github.com/microsoft/WinAppDriver/blob/master/Docs/RunningOnRemoteMachine.md)。

### 在测试运行器上

> 笔记：
>
> - 测试运行器可以是 Windows、macOS 或 Linux。

在构建测试脚本时，请确保`WinAppDriver URL`指向远程测试机的公共 IP 地址。在上面的例子中，它应该是：`http://192.168.37.95:4723/`.

应用程序文件路径是`Windows Executable File (*.exe)`远程测试机文件的绝对路径。

![](../img/zs/img-025-04.png)
**下一步：**

设置 WinAppDriver 后，您可以开始创建您的第一个 Windows 桌面应用程序测试。您可以参考以下文档了解更多详情：

- [使用 Windows 记录实用程序创建测试用例](https://docs.katalon.com/katalon-studio/docs/windows-recorder-tutorials.html#coordinate-based-recording)
- [使用 Windows Spy Utility 创建测试用例](https://docs.katalon.com/katalon-studio/docs/windows-spy-tutorials.html)