# 设置概览

> 在[此处](https://www.katalon.com/download/)下载最新版本的 Katalon Studio 。

在使用 Katalon Studio 进行设置时，我们将指导您完成安装、GUI 和首选项。我们还提供从 Selenium、TestNG 和 JUnit 等其他测试工具迁移到 Katalon Studio 的说明。

## 安装

要了解有关安装的更多信息，请参阅[安装概述](https://docs.katalon.com/katalon-studio/docs/getting-started.html)。

## GUI 和首选项

成功下载 Katalon Studio 并激活您的许可证后，就可以开始使用 Katalon Studio。

> 在[激活 Katalon 许可证中](https://docs.katalon.com/katalon-studio/docs/activate-license.html)了解如何激活您的许可证。

本部分将指导您完成 Katalon Studio 的入职之旅。以下是您在开始第一个测试项目之前需要了解的一些基本工具和配置：

- [工具栏和视图](https://docs.katalon.com/katalon-studio/docs/toolbars-and-views.html)
- [Katalon 偏好](https://docs.katalon.com/katalon-studio/docs/katalon-preferences.html)
- [如何在 Katalon Studio 中更改主题](https://docs.katalon.com/katalon-studio/docs/theme.html)
- [Katalon 帮助](https://docs.katalon.com/katalon-studio/docs/katalon-help.html)
- [更新 Katalon Studio](https://docs.katalon.com/katalon-studio/docs/auto-updater.html)

## 从其他工具迁移

从 Katalon Studio 7.4.0 版开始，您可以将测试用例从 Selenium、TestNG 或 JUnit 项目迁移到 Katalon Studio。看：

- [Selenium/TestNG/JUnit 迁移到 Katalon Studio](https://docs.katalon.com/katalon-studio/docs/selenium-testng-junit-migration.html)。
- [导入 Selenium IDE 版本 3 项目](https://docs.katalon.com/katalon-studio/docs/import-selenium-ide.html)。



# 工具栏和视图

## 工具栏

> 从 8.1.0 版开始。

![](Tutorial.assets/img-002-01.png)

主 **工具栏** 包含您通常执行的最常见操作，例如：创建测试资源或执行自动化测试。

### 系统特点

| 图标                                | 描述                                                         |
| :---------------------------------- | :----------------------------------------------------------- |
| ![](Tutorial.assets/img-002-02.png) | 保存当前打开的测试工件。                                     |
| ![](Tutorial.assets/img-002-03.png) | 保存所有打开的测试工件。                                     |
| ![](Tutorial.assets/img-002-04.png) | 打开**Spy Web**以捕获网站上的元素。                          |
| ![](Tutorial.assets/img-002-05.png) | 打开**Spy Mobile**以捕获移动应用程序上的元素。               |
| ![](Tutorial.assets/img-002-06.png) | 打开**Spy Windows Object**以捕获 Windows 中的元素。          |
| ![](Tutorial.assets/img-002-07.png) | 打开**Record Web**记录 WebUI 测试用例。                      |
| ![](Tutorial.assets/img-002-08.png) | 打开**Record Mobile**以记录移动测试用例。                    |
| ![](Tutorial.assets/img-002-09.png) | 打开**Record Windows Actions**以记录 Windows 测试用例。      |
| ![](Tutorial.assets/img-002-10.png) | 运行当前打开的测试用例。您可以从下拉列表中选择一个应用程序来运行测试：<br />Chrome<br/>Firefox<br/>IE<br/>Safari<br/>Edge<br/>Remote<br/>Headless<br/>Android<br/>iOS (on macOS)<br/>Custom |
| ![](Tutorial.assets/img-002-11.png) | 运行和调试当前打开的测试用例。您可以从下拉列表中选择一个应用程序来运行测试：<br />Chrome<br/>Firefox<br/>IE<br/>Safari<br/>Edge<br/>Remote<br/>Headless<br/>Android<br/>iOS (on macOS)<br/>Custom |
| ![](Tutorial.assets/img-002-12.png) | 调试当前打开的测试用例。请参阅[调试测试用例](https://docs.katalon.com/katalon-studio/docs/execute-a-test-case-or-a-test-suite.html#debug-a-test-case)。 |
| ![](Tutorial.assets/img-002-13.png) | 停止当前的测试执行会话。                                     |
| ![](Tutorial.assets/img-002-14.png) | 打开**命令生成器**以生成用于控制台执行的命令。               |
| ![](Tutorial.assets/img-002-15.png) | 运行测试时要应用的执行配置文件（测试环境）。                 |
| ![](Tutorial.assets/img-002-16.png) | 访问我们的[帮助中心](https://www.katalon.com/help-center/)和我们的[论坛](https://forum.katalon.com/)。 |
| ![](Tutorial.assets/img-002-17.png) | 您也可以向我们的频道提交任何反馈或进一步的问题。Katalon 专家和用户将尽快为您提供帮助。 |

### 插件功能

| 图标                                | 描述                                                         |
| :---------------------------------- | :----------------------------------------------------------- |
| ![](Tutorial.assets/img-002-18.png) | Git 活动的命令。您可以通过选择下拉列表中显示的这些选项来选择这些选项（[启用 Git 之后](https://docs.katalon.com/display/KD/Git+Integration)）：<br />克隆项目<br />分享项目<br />显示历史<br />管理分支机构<br />遵守协议<br />Push<br />Pull<br />Fetch |
| ![](Tutorial.assets/img-002-19.png) | [Katalon TestOps](https://docs.katalon.com/katalon-analytics/docs/overview.html)是我们用于 QA 编排、测试分析和高级报告的专用平台。 |
| ![](Tutorial.assets/img-002-20.png) | [Applitools](https://docs.katalon.com/katalon-studio/docs/applitools-integration.html#configure-applitools-integration)是用于录制和脚本模式的内置可视化测试工具。 |
| ![](Tutorial.assets/img-002-21.png) | 当默认定位器失败时，[自我修复会](https://docs.katalon.com/katalon-recorder/docs/self-healing.html#enabling-and-disabling-self-healing)自动尝试其他定位器。 |
| ![](Tutorial.assets/img-002-22.png) | 从[JIRA 集成](https://store.katalon.com/product/3/Jira-Integration)账户导入测试用例。 |

## 测试资源管理器视图

该 **测试资源管理器** 视图允许您浏览您的项目，并访问所有测试工件的结构。使用视图上的上下文菜单，您可以创建新的工件、组织视图的项目，或者在需要时将它们拖放到特定的编辑器视图中。

![](Tutorial.assets/img-002-23.png)

| 团体       | 描述                                                         |
| :--------- | :----------------------------------------------------------- |
| 简介       | 列出当前项目的所有[执行配置文件](https://docs.katalon.com/x/xAHR) |
| 测试用例   | 列出当前项目中的所有[测试用例](https://docs.katalon.com/display/KD/Manual+View) |
| 对象存储库 | 列出当前项目的所有[测试对象](https://docs.katalon.com/display/KD/Manage+Test+Object) |
| 测试套件   | 列出当前项目的所有[测试套件](https://docs.katalon.com/display/KD/Execute+a+test+suite)和[测试套件集合](https://docs.katalon.com/display/KD/Execute+a+test+suite+collection) |
| 数据文件   | 列出当前项目的所有[测试数据](https://docs.katalon.com/display/KD/Manage+Test+Data) |
| 检查站     | 列出当前项目的所有[检查点](https://docs.katalon.com/katalon-studio/docs/manage-checkpoints.html) |
| 关键词     | 列出当前项目的所有[自定义关键字](https://docs.katalon.com/display/KD/Introduction+to+Custom+Keywords) |
| 测试监听器 | 列出当前项目的所有[测试监听器](https://docs.katalon.com/katalon-studio/docs/fixtures-listeners.html#test-listeners-test-hooks) |
| 报告       | 列出当前项目的所有生成[报告](https://docs.katalon.com/display/KD/Test+Report) |
| 测试运维   | 包含来自[TestOps 服务器的](https://testops.katalon.io/)所有测试运行 |
| 包括       | 包含[Cucumber](https://docs.katalon.com/x/wRDR)特征文件和步骤定义 |
| 插件       | 包含当前项目的所有[插件](https://docs.katalon.com/katalon-studio/docs/kse-use-plugins.html#introduction-to-plugins)文件 |

> 笔记：
>
> 默认情况下，测试资源管理器显示所有测试工件。从版本 7.0.0 开始，您可以通过选择**Project > Settings > Explorer**来自定义测试资源**管理器**。取消选中要隐藏的测试工件，然后单击**Apply and Close**。
>
> ![](Tutorial.assets/img-002-24.png)

## 关键字浏览器视图

该 **关键词浏览器** 视图显示所有可用的关键字，通过Katalon工作室的支持，包括内置，自定义和公用事业关键字。创建测试用例脚本时，可以将**关键字浏览器**中的**关键字**拖放到测试用例编辑器中。

![](Tutorial.assets/img-002-25.png)

## 编辑

编辑器用于修改对象的详细信息。每个测试工件都有自己的编辑器。

### 测试用例编辑器

当您打开测试用例时，测试用例编辑器会在以下选项卡中包含该测试用例的详细信息：

- 手动选项卡
- 脚本选项卡
- 变量选项卡
- 变量（脚本模式）选项卡
- 集成选项卡
- 属性选项卡

**手动选项卡**

手动选项卡显示手动视图，其中基本的关键字驱动配置允许您创建自动化测试而无需编码。 有关详细信息，请参阅 [手动查看](https://docs.katalon.com/display/KD/Manual+View)。

![](Tutorial.assets/img-002-26.png)

**脚本选项卡**

脚本选项卡显示脚本视图，具有编程背景的高级用户可以使用 Groovy 或 Java 语言修改测试脚本。 有关详细信息，请参阅 [脚本视图](https://docs.katalon.com/display/KD/Script+View)。

![](Tutorial.assets/img-002-27.png)

**变量选项卡**

变量选项卡显示该测试用例的所有已定义变量。 有关详细信息，请参阅 [公共变量](https://docs.katalon.com/display/KD/Variable+Types#VariableTypes-Publicvariables)。

![](Tutorial.assets/img-002-28.png)

**变量选项卡（脚本模式）**

变量选项卡（脚本模式）以脚本模式显示该测试用例的所有定义变量。

![](Tutorial.assets/img-002-29.png)

**集成选项卡**

集成选项卡显示您在项目中配置的集成，例如：qTest、Jira、Azure DevOps 等 。有关详细信息，请参阅 [集成测试用例](https://docs.katalon.com/display/KD/Integrate+test+case)。

![](Tutorial.assets/img-002-30.png)

**属性选项卡**

属性选项卡显示有关测试用例的一般信息，包括描述和注释。

![](Tutorial.assets/img-002-31.png)

- **描述**：您可以添加或编辑此字段以提供有关测试用例的详细信息
- **注释**：此字段是只读的。内容是从测试用例中的注释关键字提取和填充的。您可以通过在 Comment 中提供需求来利用 Comment 字段参与公司的开发过程。有关 Comment 关键字的更多信息，请参阅[Comment](https://docs.katalon.com/display/KD/[Common]+Comment)。

### 测试对象编辑器

要打开测试对象，请转到**测试资源管理器 > 对象存储库**并选择要打开的对象。测试对象编辑器显示测试对象的所有详细信息，包括属性和对象识别机制。 有关详细信息，请参阅 [间谍对象](https://docs.katalon.com/display/KD/Record+and+Spy+Utilities)。

![](Tutorial.assets/img-002-32.png)

### 网络服务编辑器

要打开 Web 服务，请转到**测试资源管理器 > 对象存储库**并选择要打开的 Web 服务。当您打开 RESTful 或 SOAP 请求对象时，Web 服务编辑器会显示当前项目的详细信息，包括资源 URL、请求方法和参数。有关更多详细信息，请参阅 [RESTful](https://docs.katalon.com/pages/viewpage.action?pageId=5125144) 和[SOAP](https://docs.katalon.com/display/KD/SOAP)。

**RESTful 请求对象编辑器**

![](Tutorial.assets/img-002-33.png)

**SOAP 请求对象编辑器**

![](Tutorial.assets/img-002-34.png)

### 测试套件编辑器

当您打开一个测试套件时，测试套件编辑器会显示该测试套件的详细信息，包括：

- 主选项卡
- 脚本选项卡
- 集成选项卡
- 结果选项卡

**主选项卡**

Main 选项卡显示有关测试套件的基本信息，例如要执行的测试用例、执行机制和数据绑定。 有关更多详细信息，请参阅 [执行测试套件](https://docs.katalon.com/display/KD/Execute+a+Test+Case+or+a+Test+Suite)。

![](Tutorial.assets/img-002-35.png)

**脚本选项卡**

Script 选项卡显示 Script 视图，您可以在其中设置环境、setUp、tearDown 或测试套件级别的任何配置。要了解有关测试套件配置的更多信息，请参阅[测试套件](https://docs.katalon.com/katalon-studio/docs/create-test-suite.html)。

![](Tutorial.assets/img-002-36.png)

**集成选项卡**

集成选项卡显示有关您的测试套件集成的信息，例如与 qTest 的集成。 有关更多详细信息，请参阅 [集成测试套件](https://docs.katalon.com/display/KD/Integrate+test+suite)。

![](Tutorial.assets/img-002-37.png)

**结果选项卡**

执行测试后，Result 选项卡会显示最近执行的结果，包括每个测试用例的 Passed/Failed 状态、摘要报告、所有执行设置和执行环境。

![](Tutorial.assets/img-002-38.png)

### 测试套件集合编辑器

测试套件集合包含一组测试套件，允许您以并行模式或顺序模式一起执行多个测试套件。Test Suite Collection 编辑器有两个选项卡：Main 选项卡和 Result 选项卡。 有关更多详细信息，请参阅 [测试套件集合](https://docs.katalon.com/display/KD/Test+Suite+Collection)。

**Main 选项卡** Main 选项卡显示要执行的测试套件、每个测试套件的配置文件以及测试套件集合的执行模式。

![](Tutorial.assets/img-002-39.png)

**结果选项卡**

执行测试后，Result 选项卡会显示最近一次执行的结果，包括执行状态和每个测试套件的 Failed/Total rate。您可以通过单击**Show details 查看**每个测试套件的详细结果。

![](Tutorial.assets/img-002-40.png)

### 数据文件编辑器

打开数据文件时，数据文件编辑器会显示数据文件的详细信息，包括数据源和数据集预览。您可以从 Excel 文件、CSV 文件、数据库查询上传数据或在 Katalon Studio 中创建自己的数据文件。 有关详细信息，请参阅 [管理测试数据](https://docs.katalon.com/display/KD/Manage+Test+Data)。

- 使用 Excel 文件导入数据文件：

  ![](Tutorial.assets/img-002-41.png)

- 使用 CSV 文件导入数据文件：

  ![](Tutorial.assets/img-002-42.png)

- 使用 Katalon Studio 手动创建数据文件：

  ![](Tutorial.assets/img-002-43.png)

- 使用数据库查询导入数据文件：

  ![](Tutorial.assets/img-002-44.png)

### 检查点编辑器

当您打开检查点时，检查点编辑器会显示测试数据的详细信息，包括数据源及其拍摄的快照。 有关详细信息，请参阅 [管理检查点](https://docs.katalon.com/display/KD/Manage+Checkpoints)。

![](Tutorial.assets/img-002-45.png)

### 关键字编辑器

当您打开自定义关键字时，关键字编辑器会在脚本视图中显示关键字内容。此脚本编辑器类似于测试用例的脚本视图，您可以在其中使用 Groovy 或 Java 定义新的自定义关键字。 有关详细信息，请参阅 [自定义关键字简介](https://docs.katalon.com/display/KD/Introduction+to+Custom+Keywords)。

![](Tutorial.assets/img-002-46.png)

## 全局变量视图

全局变量视图允许您浏览项目中定义的全局变量列表。您可以在手动视图或脚本视图中查看全局变量。 有关详细信息，请参阅 [全局变量](https://docs.katalon.com/display/KD/Variable+Types#VariableTypes-Globalvariables)。

**手动查看**

![](Tutorial.assets/img-002-47.png)

**脚本视图**

![](Tutorial.assets/img-002-48.png)

## 作业进度视图

Job Progress 视图允许您查看执行测试用例和测试套件的进度。

![](Tutorial.assets/img-002-49.png)

## 问题视图

问题视图显示设置项目或设计测试用例、测试套件、测试对象或测试数据时出现的错误和警告消息。

![](Tutorial.assets/img-002-50.png)

## 事件日志

事件日志显示为您的测试运行启用的所有插件和集成的所有运行时活动。有关详细信息，请参阅[插件](https://docs.katalon.com/katalon-studio/docs/kse-use-plugins.html)。

![](Tutorial.assets/img-002-51.png)

## 控制台视图

控制台视图显示了 Katalon Studio 执行自动化测试时执行的所有运行时活动的系统日志。从测试脚本生成的控制台输出也显示在此处。

![](Tutorial.assets/img-002-52.png)

## 日志查看器视图

日志查看器显示测试执行的实时报告/日志。 有关详细信息，请参阅 [查看执行日志](https://docs.katalon.com/display/KD/View+Execution+Log)。

![](Tutorial.assets/img-002-53.png)

单击展开按钮可在日志查看器中查看更多信息。

![](Tutorial.assets/img-002-54.png)

## 报告视图

报告视图允许您查看特定测试套件的已完成测试执行的详细信息。

![](Tutorial.assets/img-002-55.png)

您可以使用搜索栏在您的报告中找到所需的信息。

![](Tutorial.assets/img-002-56.png)

## 测试套件收集报告视图

测试套件集合报告视图允许您查看特定测试套件集合的已完成测试执行的详细信息。 有关详细信息，请参阅 [测试套件收集报告](https://docs.katalon.com/display/KD/Test+Suite+Collection+Report)。

![](Tutorial.assets/img-002-57.png)

