# 本机 Windows 记录器

从 7.0.0 版本开始，Katalon 支持用于桌面应用程序测试的录制实用程序。从版本**7.5.0 开始**，本机 Windows 记录器可用于 Windows 机器。这款新一代 Windows Recorder 为您提供类似于 Web Recorder 的无缝录制体验。

**要求**

- 您的 Katalon Studio 版本必须是**7.5.0+**
- 您需要有效的**Katalon Studio Enterprise**许可证
- 此功能**仅在 Windows上受支持**

**前提条件**

- [设置 WinAppDriver](https://docs.katalon.com/katalon-studio/docs/setup-winappdriver.html)。如果您的机器尚未安装，请打开 Katalon Studio 并转到**工具 > Windows > 安装 WinAppDrivers**并按照设置向导进行操作。
- 安装[Microsoft .NET Framework 4.5.2 或更高版本](https://dotnet.microsoft.com/download/dotnet-framework/net452)

## 基于坐标的记录

> 从**版本 7.8**开始，您可以通过其相对坐标记录和定位 Windows 元素。

在**本机 Windows 记录器**中，启用**基于坐标的录制**，`click`动作和`rightClick`动作被分别记录为`clickElementOffset`和`rightClickElementOffset`。支持以下关键字：

- [[Windows\] 单击元素偏移](https://docs.katalon.com/katalon-studio/docs/windows-kw-click-element-offset.html)
- [[Windows\] 右键单击元素偏移](https://docs.katalon.com/katalon-studio/docs/windows-kw-rightclick-element-offset.html)

使用基于坐标的记录，Katalon Studio 除了记录元素的选择器之外，还记录元素的相对坐标。例如，您想单击红色 X 部分以关闭记事本中的选项卡。Katalon Recorder 将按钮的偏移量（其相对于其左上角的坐标）记录为一组表示 X 和 Y 偏移量的参数，并将它们保存在 clickElementOffset 中。它使用它们来识别在运行时执行单击操作的确切位置。

如果没有该元素的偏移量，测试引擎只能单击按钮的中心，从而导致测试失败。

## 记录

1. 右键单击 Windows 记录器图标并选择**本机Windows 记录器**以打开 本机Windows 记录器 窗口。
![](../img/zs/img-027-01.png)
2. 将显示本**机 Windows 记录器**对话框。在 CONFIGURATIONS 部分指定信息。

   **应用程序文件**：测试机器上 Windows 可执行文件 (*.exe) 的绝对路径。单击**“浏览...”**按钮以找到应用程序文件。
![](../img/zs/img-027-02.png)
   要启动 UWP 应用程序，应用程序的执行文件应为：

   - *ApplicationID*（如果您的应用已在 Microsoft 商店中发布）
   - *PackageFamilyName!Application ID*（如果您的应用仍在开发中）。

3. 单击**开始**部署并打开指定的 Windows 应用程序。
![](../img/zs/img-027-03.png)
4. 当您将鼠标悬停在 AUT 的某个元素上时，Katalon Studio 会用红色矩形突出显示已识别的对象。
![](../img/zs/img-027-04.png)
5. 当您在 AUT 上执行操作时，该操作会记录在**Recorded Actions**部分中。可用操作列表与 Katalon Studio 的内置关键字相同。您可以添加任何操作、调用另一个测试用例以及使用自定义关键字。
![](../img/zs/img-027-05.png)
6. 上面所有指定的操作都记录在**记录的操作**部分。

   在**Captured Objects**中，您可以查看在录制会话期间捕获的所有元素。**在这里，您可以通过在Object Properties**的**Locator**选项卡中对其进行修改来自定义捕获对象的定位器。捕获的对象的定位器是它们的绝对 XPath路径。
![](../img/zs/img-027-06.png)
7. 完成录制后，单击“**确定**”将录制的动作保存在 Katalon Studio 中。

8. 系统将提示您将捕获的对象保存在 Katalon Studio 的对象存储库中。选择现有文件夹或创建一个新文件夹，然后单击“**确定**”继续。
![](../img/zs/img-027-07.png)
9. 完成录制会话后，将录制的步骤导出到新的测试用例。
![](../img/zs/img-027-08.png)
10. 记录的对象和动作保存在测试用例中
![](../img/zs/img-027-09.png)
## 执行测试用例

请记住在执行测试用例之前打开 WinAppDriver。

选择主工具栏上**运行按钮中**的**Windows**图标来执行脚本。

![用windows运行](https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/record-windows-actions/run-with-windows.png)

相应地使用这些记录的步骤执行 Windows 测试。

