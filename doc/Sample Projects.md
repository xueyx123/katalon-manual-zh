# 示例项目

> 先决条件
>
> - Katalon Studio 已安装并激活。要了解有关安装和激活 Katalon Studio 的更多信息，您可以参考此文档：[安装](https://docs.katalon.com/katalon-studio/docs/getting-started.html)。

为了帮助您熟悉 Katalon Studio 的功能，Katalon 为每种支持的测试类型创建了示例项目。您可以在 Katalon Studio 中打开这些示例项目。转到**文件/新建示例项目**并选择一个示例项目：

- Web UI 测试（医疗保健示例）。您可以在此处了解有关医疗保健示例项目的更多信息：[医疗保健示例](https://docs.katalon.com/katalon-studio/docs/health-care-prj.html)。

- 使用数据驱动测试（购物车示例）进行 Web UI 测试。您可以在此处了解有关购物车示例项目的更多信息：[购物车示例](https://docs.katalon.com/katalon-studio/docs/shopping-cart-prj.html)。

- API 测试。您可以在此处了解有关 API 测试示例项目的更多信息：[Web 服务测试示例](https://docs.katalon.com/katalon-studio/docs/web-service-samples.html)。

- 移动测试，包括 Android 和 iOS 示例项目。您可以在以下文档中了解有关每种类型的移动测试示例项目的更多信息：

  - [安卓示例项目](https://docs.katalon.com/katalon-studio/docs/android-sample-prj.html)
  - [iOS 示例项目](https://docs.katalon.com/katalon-studio/docs/ios-sample-prj.html)

- BDD（黄瓜）测试。您可以在此处了解有关 BDD（Cucumber）测试示例项目的更多信息：[BDD 测试示例](https://docs.katalon.com/katalon-studio/docs/bdd-samples.html)。

  

我们还为不同的测试目的提供各种示例项目。要查找和下载我们的示例项目，您可以在此处访问我们的 Github 存储库：[Katalon Studio 示例项目](https://github.com/katalon-studio-samples)。



# 示例 WebUI 测试项目（医疗保健示例）

此示例演示了 Katalon Studio 中的 WebUI 测试基础。被测应用程序 (AUT) 是 CURA 医疗保健服务网站：`https://katalon-demo-cura.herokuapp.com/`. 您可以在本文档中了解有关 WebUI 测试的更多信息：WebUI 测试[简介](https://docs.katalon.com/katalon-studio/docs/introduction-to-web-testing.html#before-you-begin)。

## 打开 Healthcare 示例项目

要打开 Healthcare 示例项目，请在 Katalon Studio 中转到**File > New Sample Project > Sample Web UI Tests Project (Healthcare)**。

![](Sample Projects.assets/img-003-01.png)

或者，您可以从我们的 Github 存储库下载医疗保健示例项目：[医疗保健示例](https://github.com/katalon-studio-samples/healthcare-tests)。

## 医疗保健示例项目组件

### 简介

要打开执行配置文件，请转到**Profiles > default**。

![](Sample Projects.assets/img-003-02.png)

您可以在执行配置文件中创建和保存所有全局变量。它们可以在项目中的测试用例中使用。要了解有关执行配置文件和全局变量的更多信息，您可以参考此文档：[执行配置文件和全局变量](https://docs.katalon.com/katalon-studio/docs/execution-profile-v54.html)。

Katalon 在此示例项目中创建三个全局变量，如下所示：

| 名称           | 价值                       |
| :------------- | :------------------------- |
| G_超时         | 10                         |
| G_SiteURL      | http://demoaut.katalon.com |
| G_ShortTimeOut | 5                          |

### 自定义关键字

您可以在测试用例中使用自定义关键字。要了解更多关于自定义关键字的信息，您可以参考本文档：[自定义关键字简介](https://docs.katalon.com/katalon-studio/docs/introduction-to-custom-keywords.html)。

Katalon 在此示例项目中创建了三个自定义关键字。要查看自定义关键字，请在“**测试资源管理器**”面板中，转到“**关键字”>“com.example”>“WebUICustomKeywords.groovy”**。

![](Sample Projects.assets/img-003-03.png)

**▼com.example.WebUICustomKeywords.isElementPresent**

### 描述

此关键字用于检查元素是否在预定义的时间限制内显示。

### 参数

| 范围 | 类型     | 强制的 | 描述                                   |
| :--- | :------- | :----- | :------------------------------------- |
| 到   | 测试对象 | 必需的 | Katalon 测试对象                       |
| 暂停 | 整数     | 必需的 | 等待元素出现的超时时间（以秒为单位）。 |

### 退货

| 参数类型 | 类型                                                       |
| :------- | :--------------------------------------------------------- |
| 布尔值   | - **true** : 如果元素存在。 - **false** : 如果元素不存在。 |

### 例子

在此示例中，我们要检查**Make Appointment**按钮是否在 10 秒内显示。

```
import static com.kms.katalon.core.checkpoint.CheckpointFactory.findCheckpoint
import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase
import static com.kms.katalon.core.testdata.TestDataFactory.findTestData
import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
import com.kms.katalon.core.checkpoint.Checkpoint as Checkpoint
import com.kms.katalon.core.checkpoint.CheckpointFactory as CheckpointFactory
import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as MobileBuiltInKeywords
import com.kms.katalon.core.model.FailureHandling as FailureHandling
import com.kms.katalon.core.testcase.TestCase as TestCase
import com.kms.katalon.core.testcase.TestCaseFactory as TestCaseFactory
import com.kms.katalon.core.testdata.TestData as TestData
import com.kms.katalon.core.testdata.TestDataFactory as TestDataFactory
import com.kms.katalon.core.testobject.ObjectRepository as ObjectRepository
import com.kms.katalon.core.testobject.TestObject as TestObject
import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WSBuiltInKeywords
import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUiBuiltInKeywords
import internal.GlobalVariable as GlobalVariable
import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI
import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS

/*Open browser and navigate to the AUT website.*/
WebUI.openBrowser(GlobalVariable.G_SiteURL)

/*Check to see whether the Make Appointment button presents within 10 seconds*/
CustomKeywords.'com.example.WebUICustomKeywords.isElementPresent'(findTestObject('Page_CuraHomepage/btn_MakeAppointment'), 10)

WebUI.closeBrowser()
```

**▼com.example.WebUICustomKeywords.getHtmlTableRows**

### 描述

此关键字从 HTML 表的所有行中检索 Web 元素。要了解有关表格的 HTML 元素的更多信息，您可以参考这份 Mozilla 开发人员文档：[HTML 表格基础知识](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics)。

### 参数

| 范围         | 类型     | 强制的 | 描述                                 |
| :----------- | :------- | :----- | :----------------------------------- |
| 桌子         | 测试对象 | 必需的 | Katalon 测试对象代表一个 HTML 表格。 |
| 外部标签名称 | 细绳     | 必需的 | 标记的外部标记名`tr`，通常`tbody`    |

### 退货

HTML 表格中所有行的 Web 元素。

### 例子

在此示例中，我们要检索 HTML 表格正文中所有行的 Web 元素。

创建代表 HTML 表的测试对象后，应用`com.example.WebUICustomKeywords.getHtmlTableRows`custom 关键字，如下所示：

```
import static com.kms.katalon.core.checkpoint.CheckpointFactory.findCheckpoint
import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase
import static com.kms.katalon.core.testdata.TestDataFactory.findTestData
import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
import static com.kms.katalon.core.testobject.ObjectRepository.findWindowsObject
import com.kms.katalon.core.checkpoint.Checkpoint as Checkpoint
import com.kms.katalon.core.cucumber.keyword.CucumberBuiltinKeywords as CucumberKW
import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
import com.kms.katalon.core.model.FailureHandling as FailureHandling
import com.kms.katalon.core.testcase.TestCase as TestCase
import com.kms.katalon.core.testdata.TestData as TestData
import com.kms.katalon.core.testng.keyword.TestNGBuiltinKeywords as TestNGKW
import com.kms.katalon.core.testobject.TestObject as TestObject
import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS
import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI
import com.kms.katalon.core.windows.keyword.WindowsBuiltinKeywords as Windows
import internal.GlobalVariable as GlobalVariable
import org.openqa.selenium.Keys as Keys

/*Open the website contains the table*/
WebUI.openBrowser('https://docs.katalon.com/katalon-studio/docs/webui-click.html')

/*Get web elements of all rows of the table body*/
CustomKeywords.'com.example.WebUICustomKeywords.getHtmlTableRows'(findTestObject('Object Repository/Table/New Test Object'), 'tbody')

WebUI.closeBrowser()
```

**▼com.example.WebUICustomKeywords.getHtmlTableColumns**

### 描述

此关键字检索 HTML 表格中一行的所有单元格的 Web 元素。要了解有关表格的 HTML 元素的更多信息，您可以参考这份 Mozilla 开发人员文档：[HTML 表格基础知识](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics)。

### 参数

| 范围     | 类型 | 强制的 | 描述                                 |
| :------- | :--- | :----- | :----------------------------------- |
| 桌子     | 网元 | 必需的 | 一个 WebElement 代表 HTML 表格的一行 |
| 标签名称 | 细绳 | 必需的 | HTML 列标记名，通常 `td/th`          |

### 退货

HTML 表格中一行的所有单元格的 Web 元素。

### 例子

在此示例中，我们要检索以下 HTML 表格正文中第一行的所有单元格的 Web 元素。

![](Sample Projects.assets/img-003-04.png)

如上图所示，行索引从 开始`0`。在这里，要获取表体的第一行，我们将参数设置为`row[0]`并使用`com.example.WebUICustomKeywords.getHtmlTableRows`自定义关键字，如下所示：

```
import static com.kms.katalon.core.checkpoint.CheckpointFactory.findCheckpoint
import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase
import static com.kms.katalon.core.testdata.TestDataFactory.findTestData
import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
import static com.kms.katalon.core.testobject.ObjectRepository.findWindowsObject
import com.kms.katalon.core.checkpoint.Checkpoint as Checkpoint
import com.kms.katalon.core.cucumber.keyword.CucumberBuiltinKeywords as CucumberKW
import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
import com.kms.katalon.core.model.FailureHandling as FailureHandling
import com.kms.katalon.core.testcase.TestCase as TestCase
import com.kms.katalon.core.testdata.TestData as TestData
import com.kms.katalon.core.testng.keyword.TestNGBuiltinKeywords as TestNGKW
import com.kms.katalon.core.testobject.TestObject as TestObject
import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS
import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI
import com.kms.katalon.core.windows.keyword.WindowsBuiltinKeywords as Windows
import internal.GlobalVariable as GlobalVariable
import org.openqa.selenium.Keys as Keys

/*Open the website contains the table*/
WebUI.openBrowser('https://docs.katalon.com/katalon-studio/docs/webui-click.html')

/*Get web elements of all rows of the table body*/
Rows = CustomKeywords.'com.example.WebUICustomKeywords.getHtmlTableRows'(findTestObject('Object Repository/Table/New Test Object'), 'tbody')

/*Get web elements of all cells of the first row of the table body*/
TableColumns = CustomKeywords.'com.example.WebUICustomKeywords.getHtmlTableColumns'(Rows[0], 'td')

WebUI.closeBrowser()
```

### 测试用例

要访问此项目中的主要测试用例，请在“**测试资源管理器**”面板中，转到“**测试用例”>“主要测试用例**” 。

![](Sample Projects.assets/img-003-05.png)

三个测试用例用于不同的目的：

1. 测试用例**TC1_Verify Successful Login**用于验证一个人是否可以使用有效帐户成功登录。这个测试用例的流程如下：

   - 访问 CURA 医疗保健服务网站：`https://katalon-demo-cura.herokuapp.com/`。在这里，我们使用`G_SiteURL`全局变量。

   - 单击**预约**按钮。

   - 填写**用户名**和**密码**。**在这里，我们将Username**和**Password**的值类型设置为**Variable**。**您可以在变量**选项卡中更改**用户名**和**密码**值。要了解有关测试用例变量的更多信息，您可以参考此文档：[测试用例变量](https://docs.katalon.com/katalon-studio/docs/test-case-variables.html)。

     ![](Sample Projects.assets/img-003-06.png)

   - 单击**登录**按钮。

   - 验证账号是否登录成功。在这里，我们使用`G_Timeout`变量。如果10秒内出现**预约**页面，则登录成功。

   - 关闭浏览器。

     ![](Sample Projects.assets/img-003-07.gif)

     *单击 gif 将其放大。*

     ▼**点击查看测试脚本**

     ```
     import static com.kms.katalon.core.checkpoint.CheckpointFactory.findCheckpoint
     import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase
     import static com.kms.katalon.core.testdata.TestDataFactory.findTestData
     import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
     import com.kms.katalon.core.checkpoint.Checkpoint as Checkpoint
     import com.kms.katalon.core.checkpoint.CheckpointFactory as CheckpointFactory
     import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as MobileBuiltInKeywords
     import com.kms.katalon.core.model.FailureHandling as FailureHandling
     import com.kms.katalon.core.testcase.TestCase as TestCase
     import com.kms.katalon.core.testcase.TestCaseFactory as TestCaseFactory
     import com.kms.katalon.core.testdata.TestData as TestData
     import com.kms.katalon.core.testdata.TestDataFactory as TestDataFactory
     import com.kms.katalon.core.testobject.ObjectRepository as ObjectRepository
     import com.kms.katalon.core.testobject.TestObject as TestObject
     import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WSBuiltInKeywords
     import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUiBuiltInKeywords
     import internal.GlobalVariable as GlobalVariable
     import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI
     import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
     import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS
     
     WebUI.comment('Story: Login to CURA system')
     
     WebUI.comment('Given that the user has the valid login information')
     
     WebUI.openBrowser(GlobalVariable.G_SiteURL)
     
     WebUI.click(findTestObject('Page_CuraHomepage/btn_MakeAppointment'))
     
     WebUI.setText(findTestObject('Page_Login/txt_UserName'), Username)
     
     WebUI.setText(findTestObject('Page_Login/txt_Password'), Password)
     
     WebUI.comment('When he logins to CURA system')
     
     WebUI.click(findTestObject('Page_Login/btn_Login'))
     
     WebUI.comment('Then he should be able to login successfully')
     
     landingPage = WebUI.verifyElementPresent(findTestObject('Page_CuraAppointment/div_Appointment'), GlobalVariable.G_Timeout)
     
     WebUI.closeBrowser()
     ```

2. 测试用例**TC2_Verify Successful Appointment**是验证该人登录后是否可以成功预约。本测试用例的流程如下：

   - 转到 CURA Healthcare Service 网站：`https://katalon-demo-cura.herokuapp.com/`并登录。我们不重新记录登录步骤，而是调用**Common Test Cases/Login**测试用例。想了解更多关于调用测试用例的知识，可以参考这篇文档：[调用测试用例](https://docs.katalon.com/katalon-studio/docs/call-test-case.html#call-test-case-in-manual-view)。
   - **要进行预约，请填写Facility**、**Healthcare Program**和**Visit Date**的有效值。单击**预约**按钮。
   - 验证约会是否成功确认。**在这里，当出现约会确认**文本时，我们认为约会已成功确认。
   - 验证预订信息是否与确认信息匹配。
   - 截屏。

   > 笔记：
   >
   > - 您只能在执行测试套件后看到屏幕截图。见下文：[测试套件和测试套件集合](https://docs.katalon.com/katalon-studio/docs/health-care-prj.html#test-suite-and-test-suite-collection)。

   ![](Sample Projects.assets/img-003-08.gif)

   *单击 gif 将其放大。*

   ▼**点击查看测试脚本**

   ```
   import static com.kms.katalon.core.checkpoint.CheckpointFactory.findCheckpoint
   import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase
   import static com.kms.katalon.core.testdata.TestDataFactory.findTestData
   import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
   import com.kms.katalon.core.checkpoint.Checkpoint as Checkpoint
   import com.kms.katalon.core.checkpoint.CheckpointFactory as CheckpointFactory
   import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as MobileBuiltInKeywords
   import com.kms.katalon.core.model.FailureHandling as FailureHandling
   import com.kms.katalon.core.testcase.TestCase as TestCase
   import com.kms.katalon.core.testcase.TestCaseFactory as TestCaseFactory
   import com.kms.katalon.core.testdata.TestData as TestData
   import com.kms.katalon.core.testdata.TestDataFactory as TestDataFactory
   import com.kms.katalon.core.testobject.ObjectRepository as ObjectRepository
   import com.kms.katalon.core.testobject.TestObject as TestObject
   import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WSBuiltInKeywords
   import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUiBuiltInKeywords
   import internal.GlobalVariable as GlobalVariable
   import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI
   import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
   import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS
   
   WebUI.comment('Story: Book an appointment')
   
   WebUI.comment('Given that the user has logged into their account')
   
   WebUI.openBrowser(GlobalVariable.G_SiteURL)
   
   WebUI.callTestCase(findTestCase('Common Test Cases/Login'), [('Username') : 'John Doe', ('Password') : 'ThisIsNotAPassword'], 
       FailureHandling.STOP_ON_FAILURE)
   
   WebUI.comment('And Appointment page is displayed')
   
   if (true) {
       WebUI.selectOptionByLabel(findTestObject('Page_CuraAppointment/lst_Facility'), 'Hongkong CURA Healthcare Center', false)
   
       WebUI.check(findTestObject('Page_CuraAppointment/chk_Medicaid'))
   
       WebUI.check(findTestObject('Page_CuraAppointment/chk_Readmission'))
   
       WebUI.setText(findTestObject('Page_CuraAppointment/txt_VisitDate'), '27/12/2016')
   
       WebUI.setText(findTestObject('Page_CuraAppointment/txt_Comment'), 'Please make appointment as soon as possible.')
   }
   
   WebUI.comment('When he fills in valid information in Appointment page')
   
   WebUI.click(findTestObject('Page_CuraAppointment/btn_BookAppointment'))
   
   WebUI.verifyTextPresent('Appointment Confirmation', false)
   
   WebUI.comment('Then he should be able to book a new appointment')
   
   if (true) {
       WebUI.verifyMatch('Hongkong CURA Healthcare Center', WebUI.getText(findTestObject('Page_AppointmentConfirmation/lbl_Facility')), 
           false)
   
       WebUI.verifyMatch('Yes', WebUI.getText(findTestObject('Page_AppointmentConfirmation/lbl_HospitalReadmission')), false)
   
       WebUI.verifyMatch('Medicaid', WebUI.getText(findTestObject('Page_AppointmentConfirmation/lbl_Program')), false)
   
       WebUI.verifyMatch('27/12/2016', WebUI.getText(findTestObject('Page_AppointmentConfirmation/lbl_VisitDate')), false)
   
       WebUI.verifyMatch('Please make appointment as soon as possible.', WebUI.getText(findTestObject('Page_AppointmentConfirmation/lbl_Comment')), 
           false)
   }
   
   WebUI.takeScreenshot()
   ```

3. 测试用例**TC3_Visual 测试示例**利用 Katalon TestOps 中的**可视化测试**功能来比较测试执行期间捕获的图像。您可以在此处查看此功能的说明：[Katalon TestOps 中的可视化测试](https://docs.katalon.com/katalon-analytics/docs/ks-visual-testing.html#set-up-visual-testing)。

### 测试套件和测试套件集合

这个项目中有两个测试套件。要访问它们，在**Test Explorer**面板中，转到**Test Suites**。

![](Sample Projects.assets/img-003-09.png)

1. 测试套件**Healthcare-tests - TS_RegressionTest**结合了上面显示的三个测试用例。

   ![](Sample Projects.assets/img-003-10.png)

2. 测试套件集合**Healthcare-tests - TS_RegressionTestCollection**结合了两个**Healthcare-tests - TS_RegressionTest**测试套件与不同的测试环境。在这个项目中，我们使用 Firefox 和 Chrome 运行测试套件。

   ![](Sample Projects.assets/img-003-11.png)

   *点击图片放大。*

## 执行选定的测试用例或测试套件/测试套件集合

要在示例项目中执行测试用例或测试套件/测试套件集合：

1. 选择您要执行的测试用例/测试套件/测试套件集合。

2. 单击**运行**或按 Ctrl + Shift + A（macOS：Cmd+Shift+A）。

   您可以在**Run**旁边的下拉列表中选择不同的浏览器来执行您的测试。

   ![](Sample Projects.assets/img-003-12.png)

3. 在**Log Viewer**选项卡中观察测试结果。想要了解更多关于分析测试执行日志的内容，可以参考这篇文档：[【WebUI】分析测试执行日志和调试测试用例](https://docs.katalon.com/katalon-studio/tutorials/webui-analyze-test-case-execution-logs-and-resolve-errors.html#analyze-test-execution-logs-in-log-viewer)。

   ![](Sample Projects.assets/img-003-13.png)

   > 笔记：
   >
   > - 您可以在测试套件或测试套件集合级别的**结果**选项卡中查看测试结果。测试结果可以是通过、失败、错误或不完整。要了解有关测试状态的更多信息，您可以参考本文档：[查看和自定义执行日志](https://docs.katalon.com/katalon-studio/docs/working-with-execution-log.html#view-execution-log)。
   > - 执行测试套件或测试套件集合后，您可以在`<your-project-folder>/Reports`. Katalon Studio 还支持将测试报告导出为不同的格式，例如 HTML、CSV、PDF 和 JUnit。
   > - 要获得实时监控和更好的报告功能，请考虑将您的项目与 Katalon TestOps 集成。在此处了解有关测试结果报告的更多信息：[从 Katalon Studio 将测试结果上传到 Katalon TestOps](https://docs.katalon.com/katalon-studio/docs/katalon-analytics-beta-integration.html)。





# 带有数据驱动测试的示例 WebUI 测试项目（购物车示例）

此示例演示了在 Katalon Studio 中使用数据驱动测试进行的 WebUI 测试。此示例还向您展示了测试用例中自定义关键字的广泛使用。

被测应用程序 (AUT) 是 Katalon 商店网站：`http://cms.demo.katalon.com`. 您可以在本文档中了解有关 WebUI 测试的更多信息：WebUI 测试[简介](https://docs.katalon.com/katalon-studio/docs/introduction-to-web-testing.html#before-you-begin)。

## 打开购物车示例项目

要打开 Shopping Cart 示例项目，在 Katalon Studio 中，转到**File > New Sample Project > Sample Web UI Tests Project (Shopping Cart)**。

![](Sample Projects.assets/img-003-14.png)

或者，您可以从我们的 Github 存储库下载购物车示例项目：[购物车示例](https://github.com/katalon-studio-samples/shopping-cart-tests)。

## 购物车示例项目组件

### 简介

要打开执行配置文件，请转到**Profiles > default**。

![](Sample Projects.assets/img-003-15.png)

您可以在执行配置文件中创建和保存所有全局变量。它们可以在项目中的测试用例中使用。要了解有关执行配置文件和全局变量的更多信息，您可以参考此文档：[执行配置文件和全局变量](https://docs.katalon.com/katalon-studio/docs/execution-profile-v54.html)。

Katalon 在这个示例项目中创建了 19 个全局变量，如下所示：

| 名称                    | 价值                                   |
| :---------------------- | :------------------------------------- |
| 网址登录                | http://cms.demo.katalon.com/my-account |
| 用户名                  | customer                               |
| 密码                    | crz7mrb.KNG3yxv1fbn                    |
| waitPresent超时         | 5                                      |
| 网址商店                | http://cms.demo.katalon.com            |
| 公司名                  | 知识管理系统KMS                        |
| 地址                    | 119 Nguyen Thi Thap                    |
| 城市                    | HCM                                    |
| 国家                    | Vietnam越南                            |
| 邮政编码                | 70000                                  |
| 电话                    | 0359912894                             |
| uploadPlaceOrderTimeout | 60                                     |
| 数据文件                | 产品列表                               |
| 输入列标题              | 产品名称                               |
| urlProduct              | http://cms.demo.katalon.com/product    |
| 产品名称                | Flying Ninja                           |
| 优惠券                  | KBAW662S                               |
| 名                      | katalon                                |
| 姓                      | customer                               |

### 自定义关键字

Katalon 还在此示例项目中创建示例自定义关键字。要了解更多关于自定义关键字的信息，您可以参考本文档：[自定义关键字简介](https://docs.katalon.com/katalon-studio/docs/introduction-to-custom-keywords.html)。

要查看我们的示例自定义关键字，请在“**测试资源管理器**”面板中，转到“**关键字”>“示例**” 。双击以下 .groovy 文件之一：

| 自定义关键字文件        | 描述                                                       |
| :---------------------- | :--------------------------------------------------------- |
| BlockUIDismissed.groovy | 此文件包含一个自定义关键字，等待**结帐**页面中的覆盖消失。 |
| Checkout.groovy         | 此文件包含执行结帐操作的自定义关键字。                     |
| Login.groovy            | 此文件包含执行登录操作的自定义关键字。                     |
| Select2.groovy          | 此文件包含执行选择操作的自定义关键字。                     |
| Shop.groovy             | 此文件包含执行添加到购物车操作的自定义关键字。             |
| Utils.groovy            | 此文件包含辅助文件中的关键字的关键字`Select2.groovy`。     |

![](Sample Projects.assets/img-003-17.png)

自定义关键字可以在测试用例中多次重复使用，以执行不同的操作，例如登录、将商品添加到购物车和签出。您可以在我们的示例测试用例中看到自定义关键字的使用，如下所示：[测试用例](https://docs.katalon.com/katalon-studio/docs/shopping-cart-prj.html#test-cases)。

### 测试用例

1. 自定义关键字示例测试用例

要查看此项目中的**Custom-keyword samples**测试用例，在**Test Explorer**面板中，转到**Test Cases > Custom-keyword samples**。双击打开以下测试用例之一：

![](Sample Projects.assets/img-003-18.png)

- 测试用例**Order and check out single product**将**单个产品**添加到购物车，然后结帐。这个测试用例的流程如下：

  1. 我们使用`loginIntoApplicationWithGlobalVariable`自定义关键字来：

     - `http://cms.demo.katalon.com`以最大化的窗口打开网站。
     - 使用在执行配置文件中定义为全局变量的用户名和密码登录。

  2. 我们进入**商店**页面。

  3. 接下来，我们使用`addToCartWithGlobalVariable`自定义关键字来：

     - 将产品添加到购物车。产品在执行配置文件中被定义为全局变量。
     - 转到**购物车**页面。
     - 单击**继续结帐**以转到**结帐**页面。

  4. 对于结帐步骤，我们使用`CheckoutShop`自定义关键字来：

     - 单击**结帐**页面。

     - 填写结帐信息。**检出信息在“变量**”选项卡中定义为测试用例变量。

       ![](Sample Projects.assets/img-003-19.png)

  5. 最后，我们使用`logoutFromApplication`自定义关键字来：

     - 转到**我的帐户**页面。

     - 单击**注销**。

       ![](Sample Projects.assets/img-003-20.gif)

       *单击 gif 将其放大。*

       **点击查看测试脚本**

       ```
       import static com.kms.katalon.core.checkpoint.CheckpointFactory.findCheckpoint
       import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase
       import static com.kms.katalon.core.testdata.TestDataFactory.findTestData
       import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
       import com.kms.katalon.core.checkpoint.Checkpoint as Checkpoint
       import com.kms.katalon.core.cucumber.keyword.CucumberBuiltinKeywords as CucumberKW
       import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
       import com.kms.katalon.core.model.FailureHandling as FailureHandling
       import com.kms.katalon.core.testcase.TestCase as TestCase
       import com.kms.katalon.core.testdata.TestData as TestData
       import com.kms.katalon.core.testobject.TestObject as TestObject
       import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS
       import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI
       import internal.GlobalVariable as GlobalVariable
       
       CustomKeywords.'sample.Login.loginIntoApplicationWithGlobalVariable'()
       
       WebUI.waitForElementPresent(findTestObject('Pages/Shop page/lnkShop'), GlobalVariable.waitPresentTimeout)
       
       WebUI.click(findTestObject('Pages/Shop page/lnkShop'))
       
       CustomKeywords.'sample.Shop.addToCartWithGlobalVariable'()
       
       CustomKeywords.'sample.Checkout.CheckoutShop'(firstName,lastName,companyName, country, address, city, postCode, Phone)
       
       CustomKeywords.'sample.Login.logoutFromApplication'()
       
       WebUI.closeBrowser()
       ```

测试用例**Order and check out single product using coupon**将单个产品添加到购物车，应用 50% off 优惠券，然后结帐。这个测试用例的流程如下：

1. 我们使用`loginIntoApplicationWithGlobalVariable`自定义关键字来：

   - `http://cms.demo.katalon.com`以最大化的窗口打开网站。
   - 使用在执行配置文件中定义为全局变量的用户名和密码登录。

2. 我们进入**商店**页面。

3. 接下来，我们使用`applyCouponAndAddToCartWithGlobalVariable`自定义关键字来：

   - 将产品添加到购物车。产品在执行配置文件中被定义为全局变量。
   - 转到**购物车**页面。
   - 填写定义为全局变量的优惠券代码。

4. 对于结帐步骤，我们使用`CheckoutShopWithGlobalVariable`自定义关键字来：

   - 单击**结帐**页面。
   - 填写结帐信息。检出信息被定义为执行配置文件中的全局变量。

5. 最后，我们使用`logoutFromApplication`自定义关键字来：

   - 转到**我的帐户**页面。

   - 单击**注销**。

     ![](Sample Projects.assets/img-003-21.gif)

     *单击 gif 将其放大。*

     **点击查看测试脚本**

     ```
     import static com.kms.katalon.core.checkpoint.CheckpointFactory.findCheckpoint
     import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase
     import static com.kms.katalon.core.testdata.TestDataFactory.findTestData
     import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
     import com.kms.katalon.core.checkpoint.Checkpoint as Checkpoint
     import com.kms.katalon.core.cucumber.keyword.CucumberBuiltinKeywords as CucumberKW
     import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
     import com.kms.katalon.core.model.FailureHandling as FailureHandling
     import com.kms.katalon.core.testcase.TestCase as TestCase
     import com.kms.katalon.core.testdata.TestData as TestData
     import com.kms.katalon.core.testobject.TestObject as TestObject
     import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS
     import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI
     import internal.GlobalVariable as GlobalVariable
     
     CustomKeywords.'sample.Login.loginIntoApplicationWithGlobalVariable'()
     
     WebUI.waitForElementPresent(findTestObject('Pages/Shop page/lnkShop'), GlobalVariable.waitPresentTimeout)
     
     WebUI.click(findTestObject('Pages/Shop page/lnkShop'))
     
     CustomKeywords.'sample.Shop.applyCouponAndAddToCartWithGlobalVariable'()
     
     CustomKeywords.'sample.Checkout.CheckoutShopWithGlobalVariable'()
     
     CustomKeywords.'sample.Login.logoutFromApplication'()
     
     WebUI.closeBrowser()
     ```

     1. 数据驱动的样本测试用例

     要查看此项目中的**数据驱动示例**测试用例，请在“**测试资源管理器**”面板中，转到“**测试用例”>“数据驱动示例”>“订购”并签出多个产品**。

     ![](Sample Projects.assets/img-003-22.png)

     测试用例**Order and check out multiple products**将产品列表中的产品添加到购物车，然后结帐。这个测试用例的流程如下：

     1. 我们使用`loginIntoApplicationWithGlobalVariable`自定义关键字来：

        - `http://cms.demo.katalon.com`以最大化的窗口打开网站。
        - 使用在执行配置文件中定义为全局变量的用户名和密码登录。

     2. 我们进入**商店**页面。

     3. 接下来，我们希望测试用例读取数据文件。为此，我们使用`getAllData()`关键字从产品列表中提取产品名称，如下所示：

        ```
        TestData product = findTestData(GlobalVariable.dataFile)
        List<String> productList = product.getAllData().stream()
        .map{data -> data[0]}/*get first column of each row in data file */
        .collect(Collectors.toList())/*add collect and parse to list*/
        ```

     4. 然后，我们使用`addToCart`自定义关键字将提取的产品名称添加到购物车。

        ```
        for(def productName : productList){
        CustomKeywords.'sample.Shop.addToCart'(productName.toString(), GlobalVariable.urlProduct)
        }
        ```

     5. 最后，我们使用`CheckoutShopWithGlobalVariable`自定义关键字来：

        - 单击**结帐**页面。

        - 填写结帐信息。检出信息被定义为执行配置文件中的全局变量。

          ![](Sample Projects.assets/img-003-23.gif)

          *单击 gif 将其放大。*

          **点击查看测试脚本**

          ```
          import static com.kms.katalon.core.checkpoint.CheckpointFactory.findCheckpoint
          import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase
          import static com.kms.katalon.core.testdata.TestDataFactory.findTestData
          import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
          
          import java.util.stream.Collectors
          
          import com.kms.katalon.core.checkpoint.Checkpoint as Checkpoint
          import com.kms.katalon.core.cucumber.keyword.CucumberBuiltinKeywords as CucumberKW
          import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
          import com.kms.katalon.core.model.FailureHandling as FailureHandling
          import com.kms.katalon.core.testcase.TestCase as TestCase
          import com.kms.katalon.core.testdata.TestData as TestData
          import com.kms.katalon.core.testobject.TestObject as TestObject
          import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS
          import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI
          import internal.GlobalVariable as GlobalVariable
          
          CustomKeywords.'sample.Login.loginIntoApplicationWithGlobalVariable'()
          
          WebUI.waitForElementPresent(findTestObject('Pages/Shop page/lnkShop'), GlobalVariable.waitPresentTimeout)
          
          WebUI.click(findTestObject('Pages/Shop page/lnkShop'))
          
          TestData product = findTestData(GlobalVariable.dataFile)
          List<String> productList = product.getAllData().stream()
                        .map{data -> data[0]}/*get first column of each row in data file */
                        .collect(Collectors.toList())/*add collect and parse to list*/
          
          for(def productName : productList){
            CustomKeywords.'sample.Shop.addToCart'(productName.toString(), GlobalVariable.urlProduct)
          }
          CustomKeywords.'sample.Checkout.CheckoutShopWithGlobalVariable'()
          WebUI.closeBrowser()
          ```

          ### 数据文件

          要查看此示例项目中的数据文件，请在**Test Explorer**面板中，转到**Data Files > Product List/Multiple Checkout**。

          ![](Sample Projects.assets/img-003-24.png)

          或者，您可以转到`<your-project-folder>\Data Files`并选择要打开的文件：

          - `Constants.xlsx`包含`Product List`和`Multiple Checkout`工作表。
          - `Product List.dat` 是您要添加到购物车的产品列表。
          - `Multiple Checkout.dat`**是结帐**页面上运送所需的客户个人信息列表。

          ### 测试套件

          示例测试套件演示了 Katalon Studio 中的数据驱动测试。要查看示例测试套件，请转到“**测试资源管理器**”面板中的“**测试套件**”文件夹。双击打开以下三个测试套件之一：

          1. 测试套件**多次订购和签出单个产品**演示了通过数据绑定进行的数据驱动测试。

             此测试套件绑定测试用例Order 并使用**Multiple Checkout**数据文件**签出单个产品。**打开**Test Suite**后，点击**Show Data Binding**查看绑定数据。

             想了解更多关于绑定数据的内容，可以参考以下文档：[数据绑定](https://docs.katalon.com/katalon-studio/docs/run-test-case-external-data.html#manage-data-binding)。

             ![](Sample Projects.assets/img-003-25.png)

             *点击图片放大。*

          2. 测试套件**Order and check out multiple products**演示了 Groovy 脚本的数据驱动测试。

             该测试套件调用测试用例**Order 并检查多个产品**。此测试用例使用 Groovy 脚本读取**产品列表**测试数据文件。在测试用例**Order and checkout multiple products**的脚本模式下，可以看到如下示例代码：

             ```
             TestData product = findTestData(GlobalVariable.dataFile)
             List<String> productList = product.getAllData().stream()
             .map{data -> data[0]}/*get first column of each row in data file */
             .collect(Collectors.toList())/*add collect and parse to list*/
             
               /*Add extracted product names to cart*/
             for(def productName : productList){
             CustomKeywords.'sample.Shop.addToCart'(productName.toString(), GlobalVariable.urlProduct)
             }
             ```

             ![](Sample Projects.assets/img-003-26.png)

             3. 测试套件**Order and check out with Global Variable**演示**了全局变量的**数据驱动测试。

             为了**使用全局变量**测试套件进行检查，我们将**自定义关键字示例**称为测试用例。这些测试用例使用带有全局变量的自定义关键字。

             ![](Sample Projects.assets/img-003-27.png)

             ### 测试套件集合

             测试套件集合**Shopping-cart-tests - Run All Test Suites**将上面显示的三个测试套件与不同的测试环境结合在一起。

             ![](Sample Projects.assets/img-003-28.png)

             *点击图片放大。*

             ## 执行选定的测试用例或测试套件/测试套件集合

             要在示例项目中执行测试用例或测试套件/测试套件集合：

             1. 选择您要执行的测试用例/测试套件/测试套件集合。

             2. 单击**运行**或按 Ctrl + Shift + A（macOS：Cmd+Shift+A）。

                **您可以在Run**旁边的下拉列表中选择不同的浏览器来执行您的测试。

                ![](Sample Projects.assets/img-003-29.png)

             3. **在Log Viewer**选项卡中观察测试结果。想要了解更多关于分析测试执行日志的内容，可以参考这篇文档：[【WebUI】分析测试执行日志和调试测试用例](https://docs.katalon.com/katalon-studio/tutorials/webui-analyze-test-case-execution-logs-and-resolve-errors.html#analyze-test-execution-logs-in-log-viewer)。

                ![](Sample Projects.assets/img-003-30.png)

                > 笔记：
                >
                > - 您可以在测试套件或测试套件集合级别的**结果选项卡中查看测试结果。**测试结果可以是通过、失败、错误或不完整。要了解有关测试状态的更多信息，您可以参考本文档：[查看和自定义执行日志](https://docs.katalon.com/katalon-studio/docs/working-with-execution-log.html#view-execution-log)。
                > - 执行测试套件或测试套件集合后，您可以在`<your-project-folder>/Reports`. Katalon Studio 还支持将测试报告导出为不同的格式，例如 HTML、CSV、PDF 和 JUnit。
                > - 要获得实时监控和更好的报告功能，请考虑将您的项目与 Katalon TestOps 集成。在此处了解有关测试结果报告的更多信息：[从 Katalon Studio 将测试结果上传到 Katalon TestOps](https://docs.katalon.com/katalon-studio/docs/katalon-analytics-beta-integration.html)。

# Web 服务测试示例--示例API测试项目

Web 服务测试示例项目可[在此处](https://github.com/katalon-studio-samples/web-service-tests)获得。

> [执行测试后，您可以在Katalon TestOps](https://analytics.katalon.com/)中查看您的报告和详细信息。
>
> - [与 Katalon TestOps 集成](https://docs.katalon.com/katalon-studio/docs/katalon-analytics-beta-integration.html)
> - [查看测试报告](https://docs.katalon.com/katalon-analytics/docs/project-management-view-reports.html)
> - [查看测试执行、测试套件和测试用例详细信息](https://docs.katalon.com/katalon-analytics/docs/project-management-view-details.html)

也可以看看：

- [验证片段](https://docs.katalon.com/katalon-studio/docs/verification-snippets.html)。
- [自定义关键字](https://docs.katalon.com/katalon-studio/docs/introduction-to-custom-keywords.html)。
- [数据绑定](https://docs.katalon.com/katalon-studio/docs/run-test-case-external-data.html#create-a-new-test-suite-with-test-case-variables)。

# 从 Katalon Studio 将测试结果上传到 Katalon TestOps

> 笔记：
>
> - Katalon Studio 7.0 及更高版本支持在将测试结果上传到 Katalon TestOps 时对其进行视频捕获。

从 Katalon Studio，您可以手动或自动将测试结果上传到 Katalon TestOps。

## 自动上传测试结果

跟着这些步骤：

1. 打开 Katalon 工作室。

2. 转到**项目**>**设置**> **Katalon TestOps**。

   ![](Sample Projects.assets/img-003-31.png)

   或者，您也可以单击主工具栏中的**TestOps**图标以导航到 TestOps 设置。

   ![](Sample Projects.assets/img-003-32.png)

3. 勾选**启用 Katalon TestOps 集成**复选框。

   等待 Katalon Studio 连接到 Katalon TestOps。

   连接成功后，Katalon Studio 会从您所属的组织中检索所有团队和项目。

4. **在团队** 和 **项目**部分的下拉菜单中选择您的团队和项目 。

   如果您是所有者或管理员，您也可以单击**新建项目**来创建新项目。

5. 单击**应用并关闭**。

在 Katalon Studio 中启用 Katalon TestOps 集成后，每次在 Katalon Studio 中运行测试套件时，您的测试结果都会自动上传到 Katalon TestOps。

![](Sample Projects.assets/img-003-33.png)

## 手动上传测试结果

您也可以按照以下步骤手动上传测试结果：

1. 打开 Katalon Studio 并转到您正在处理的项目。

2. 转到**测试套件**或**测试套件集合**并选择您的测试套件。

   选择**结果**选项卡。

   ![](Sample Projects.assets/img-003-34.png)

3. 单击右上角的**Katalon TestOps**选项卡，然后选择**Upload**。

4. 选择要将测试结果上传到的团队和项目。

5. 点击**上传**。

您已手动将测试结果上传到 Katalon Testops。

## Katalon Studio 中的切换组织

您可以按照以下步骤在 Katalon Studio 中切换到不同的组织：

1. 打开 Katalon Studio 并单击右上角的*配置文件*图标。

   ![](Sample Projects.assets/img-003-35.png)

2. 选择**注销**。

   Katalon **Studio 激活**框显示。

3. 输入新的电子邮件地址和密码，然后单击**激活**。

您已登录到不同的组织。

要验证您是否已成功覆盖身份验证，请再次单击*Profile*图标并选择**View Dashboard**。

![](Sample Projects.assets/img-003-36.png)

您将被导航到 Katalon TestOps 中的新组织。

# 查看报告

## 访问报告

Katalon TestOps 中的报告是基于以 Katalon Studio、Katalon Recorder 和 JUnit 等不同格式导入的一个或多个自动化测试结果数据集自动生成的。

报告可以在**测试结果**页面中查看。目前，Katalon TestOps 与您分享几份报告，其中包含不同的见解和发现，包括状态和性能报告；测试执行表；[测试执行、测试套件和测试用例详细信息](https://docs.katalon.com/katalon-analytics/docs/project-management-view-details.html)。

## 查看报告

**状态报告**根据测试状态提供历史测试结果数据的可视化演示，您可以从中轻松识别每个状态的趋势和模式。状态报告是根据这些值创建的，如下所示：

- 试运行次数
- 测试执行次数
- 每次测试运行的状态（通过、失败、错误、未完成）

**性能报告**可视化完成一个测试执行所花费的时间长度，说明持续时间随时间变化的趋势。趋势的任何剧烈变化都可能意味着 AUT 的性能问题。绩效报告是根据这些值创建的，如下所示：

- 每个测试套件的持续时间
- 每个测试套件的执行次数

**测试执行表**提供了数据集的全面视图。测试人员可以轻松读取某些值之间的比较。

用户可以通过查看、下载、删除和重新导入测试结果来管理他们的数据。

- **状态**：每个测试套件的测试状态

- **ID**：唯一标识项目中每个测试套件的序号

- **测试套件**：每个测试套件的名称

- **配置文件**：默认或用户的自定义输入

- **Started**：执行测试套件或测试套件集合的时间

- **Duration**：测试持续的时间长度

- **Total**：一次执行中的测试用例总数

- **P/F/E 和 I**：根据每种类型的测试结果执行测试的次数。

- **By**：导入数据的用户。

  # 查看测试执行、测试套件和测试用例详细信息

  用户只需单击其 ID 或名称即可查看每个测试执行、测试套件和测试用例的执行摘要和详细信息。

  > 注意：每个测试执行都用一个 ID 唯一标识。测试执行中有许多测试运行，它们也被授予一个 ID。

  ## 每个测试执行的详细信息

  要查看每个执行的详细信息，请在测试执行表中单击其 ID，然后将显示其摘要和详细信息。在其摘要仪表板中，有三个子页面：结果、测试运行和文件。

  **结果：**

  - **Test Runs**：根据测试状态，本次执行的测试总次数。
  - **失败的测试运行**：未通过的测试运行记录列表。
  - **Coverage**：在测试套件集合中执行的测试套件列表及其详细信息，例如名称、配置文件、平台、已启动和持续时间。
  - **API 性能**：根据 ID、名称、总持续时间、平均持续时间和请求计数来查看执行中的 API 对象。

  **测试运行：**该测试套件中所有测试运行的列表。

  **文件：**存储可供用户下载的执行日志文件。

  ## 每个测试套件的详细信息

  单击测试套件的名称，将显示摘要仪表板，您可以查看四个子页面：结果、测试运行、环境和评论。

  **Result**：本次执行中的测试运行总数；状态趋势、性能趋势、所有未通过的试运行记录。

  **测试运行**：该测试套件中的测试运行列表。

  **Environments**：执行环境的详细信息。

  **评论**：用户对此测试套件的评论。

  ## 每个测试用例的详细信息

  单击测试用例的 ID，将显示摘要仪表板，您可以查看按五个子页面组织的详细信息：结果、步骤、请求、环境和注释。

  **摘要字段**：状态、配置文件、操作系统、已启动、持续时间和历史记录。在历史记录中，您可以查看：

  - 历史：单个测试用例的所有迭代运行。要查看详细信息，请单击测试运行的 ID。
  - 性能：每个测试用例的性能报告。

  **结果**：

  - **日志**：来自 Katalon Studio 的详细执行日志的预览。
  - **测试套件**：包含此测试用例的测试套件。
  - **Path**：测试用例在 Katalon Studio 中的位置路径。
  - **Jira 问题**：Jira 中的相关问题。
  - **Age**：最近重复测试状态的出现次数（例如Status：Failed；Age：5。*此测试用例连续失败5次*）。
  - **相同的失败**：无或测试运行有类似的失败。
  - **附件**：来自 Katalon Studio 的错误日志或报告文件。
  - **任务**：与此测试用例相关的那些任务。

  **步骤：**测试运行中的测试步骤。

  **请求：** API 请求列表。要查看 HAR 格式的请求详细信息，请单击其 ID。

  **Environments：**测试运行的执行环境。

  **评论：**用户对本次试运行的评论。

  # 验证片段

  Katalon Studio 支持直接在 Web 服务对象的详细信息中编写验证脚本的能力。这种支持将大大减少在测试用例和请求对象之间来回添加测试脚本的时间。验证响应可以立即完成。

  可以通过单击Web 服务对象视图中的**验证选项卡来访问验证片段。**

  ![](Sample Projects.assets/img-003-37.png)

  ## 使用验证片段

  当您单击其中一个可用片段时，Katalon Studio 将自动为您生成一个片段。 

  > 生成的片段只是一个示例。不要尝试立即使用它们而不进行调整以满足您的需求。

  您还可以验证 XML 或 JSON 响应正文的数据。为此，在响应面板中，切换到 JSON 或 XML 响应页面，选择数据并按组合键“Ctrl/Command + K”添加验证脚本。

  ![](Sample Projects.assets/img-003-38.png)

  Katalon Studio 会将响应正文中的值与验证脚本中的预定义值进行比较。

  生成验证片段后，您可以在当前 Web 服务的对象或测试用例中使用它

  - ***在 Web 服务对象\*****中：单击 Web 服务对象详细信息中“播放**”按钮旁边的下拉按钮，然后选择“测试请求和验证”。

    ![](Sample Projects.assets/img-003-39.png)

    它将发送当前请求并执行验证片段。使用验证片段执行的验证日志将显示在“**验证日志**”选项卡上。如果您不想使用当前验证片段发送测试请求，则只需单击“**播放”** 按钮。
    ![](Sample Projects.assets/img-003-40.png)

  - ***在测试用例中\***：使用发送请求和验证关键字。这还将发送当前请求并执行验证片段。 

    ```
    WS.sendRequestAndVerify(findTestObject('REST_CommentDetails'))
    ```

    执行结果将显示在“**日志查看器**”选项卡中。

    ![](Sample Projects.assets/img-003-41.png)

  ## 可用验证片段列表

  在“验证”选项卡的右侧面板上是常见的预构建片段列表，可以在大多数验证案例中为您提供帮助。 

  | 片段                         | 描述                                        |
  | :--------------------------- | :------------------------------------------ |
  | 获取当前响应                 | 发送请求成功后返回响应对象。                |
  | 获取全局变量                 | 返回一个全局变量的值。                      |
  | 获取变量                     | 返回您在 Web 服务测试对象中创建的变量的值。 |
  | 响应正文：包含字符串         | 验证响应的正文是否包含特定字符串。          |
  | 响应正文：转换为 JSON 对象   | 将响应的正文转换为 JSON。                   |
  | 响应标头：Content-Type 标头  | 验证 Content-Type 标头的值。                |
  | 状态码：代码为 200           | 验证响应的状态码是 200 还是否。             |
  | 状态码：请求成功             | 验证请求是否发送成功                        |
  | 响应正文：元素数量           | 验证响应中的元素数量                        |
  | 响应正文：元素不为空         | 验证指定元素不为空                          |
  | 响应：数组包含               | 验证指定的数组是否包含值                    |
  | 响应：获取数组列表的单个信息 | 获取数组列表的单个信息                      |

# 自定义关键字简介

除了内置关键字，您还可以定义自定义关键字来扩展 Katalon Studio 的功能。创建后，自定义关键字可以在实现测试用例时使用，就像其他内置关键字一样。

## 创建一个包

*包* 是组织一组相关类和接口的命名空间。 因为用 Java 编程语言或类似语言编写的软件可以由数百或 *数千个*单独的类组成，所以通过将相关的类和接口放入包中来保持事物的组织是有意义的。

1.  从主菜单中选择 **文件 > 新建 > 包。**将 显示**新建关键字包** 对话框。为您的包输入一个名称，然后单击 **OK**。

   ![](Sample Projects.assets/img-003-42.png)

2. 相应地，在测试资源管理器的**关键字**文件夹下创建一个新包。

   ![](Sample Projects.assets/img-003-43.png)

## 创建自定义关键字

1.  从主菜单中选择 **文件 > 新建 > 关键字。**将 显示**新建关键字** 对话框。输入关键字的名称并指定关键字的 **包** 。单击 **确定**。

   默认情况下，类名不能以数字开头，不能包含空格或特殊字符。Java 命名约定建议使用名词或名词短语来创建类名，每个单词的首字母大写，以便更好地管理项目。

   ![](Sample Projects.assets/img-003-44.png)

   > 您可以为 Web、移动和 API 测试生成示例自定义关键字。请参阅[本指南](https://docs.katalon.com/katalon-studio/docs/sample-custom-keywords.html)。

2.  相应地在指定的**包**下创建一个新关键字 。

   ![](Sample Projects.assets/img-003-45.png)

3. 在您的类中输入以下代码片段以定义自定义关键字：

   ```
   @Keyword (keywordObject = "<category_name>")
   def keywordName(parameters…) {
   // enter your code here
   // you can use either Groovy or Java
   }
   ```

   在哪里：

   | 物品          | 描述                                            | 必需的 |
   | :------------ | :---------------------------------------------- | :----- |
   | @Keyword      | 注解表示下面的代码块是关键字的定义。            | 强制的 |
   | keywordObject | 您的自定义关键字的类别（从版本 7.5.5 开始提供） | 选修的 |
   | keywordName   | 您想用于自定义关键字的名称                      | 强制的 |
   | parameters    | 将在自定义关键字中使用的参数列表                | 强制的 |
   | 例如：        |                                                 |        |

   ![](Sample Projects.assets/img-003-46.png)

   从**7.5.5**版本开始，关键字浏览器中的自定义关键字按字母顺序排列，您可以对其进行分类。特别是，类别名称应使用`keywordObject`与内置关键字相同的机制声明。以下示例描述了“浏览器”类别的关键字：

   ```
   @Keyword(keywordObject = "Browser")
   def refreshBrowser() {
   }
   ```

4. 完成后保存 **关键字** 文件。

## 使用自定义关键字

### 在手动视图中

按照以下步骤在测试用例的**手动视图中使用您定义的自定义关键字：**

1. 在手动视图中打开一个测试用例，然后 从命令工具栏中选择**自定义关键字。**

   ![](Sample Projects.assets/img-003-47.png)

2. 添加了一个新的测试步骤。选择您的自定义关键字之一。

   ![](Sample Projects.assets/img-003-48.png)

### 在脚本视图中

按照以下步骤在测试用例的**脚本视图中使用您定义的自定义关键字：**

1. *Katalon* Studio的 自定义关键字**类** 允许您访问所有自定义关键字。在脚本编辑器中输入以下语法：

   ```
   CustomKeywords.
   ```

2. **键入点** 字符 后将立即调用 **Content Assist**功能。 **Content Assist** 为用户提供上下文相关的代码完成建议。因此，您的测试项目中定义的所有自定义关键字将显示如下：

   ![](Sample Projects.assets/img-003-49.png)

3. 选择最近创建的关键字并根据需要提供所有参数。

也可以看看：

在使用自定义关键字时，以下 API 文档可能很有用：

| 班级                                                         | 方法                                                         | 描述                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :--------------------------- |
| [驱动工厂](https://docs.katalon.com/javadoc/com/kms/katalon/core/webui/driver/DriverFactory.html) | [获取WebDriver()](https://docs.katalon.com/javadoc/com/kms/katalon/core/webui/driver/DriverFactory.html#getWebDriver()) | 获取当前活动的网络驱动程序。 |
| [测试对象](https://docs.katalon.com/javadoc/com/kms/katalon/core/testobject/TestObject.html) | [addProperty（字符串名称，ConditionType 条件，字符串值）](https://docs.katalon.com/javadoc/com/kms/katalon/core/testobject/TestObject.html#addProperty(java.lang.String, com.kms.katalon.core.testobject.ConditionType, java.lang.String)) | 向测试对象添加新属性         |
|                                                              | [setProperties(List 属性)](https://docs.katalon.com/javadoc/com/kms/katalon/core/testobject/TestObject.html#setProperties(List)) | 设置测试对象的属性           |
|                                                              | [获取对象标识（）](https://docs.katalon.com/javadoc/com/kms/katalon/core/testobject/TestObject.html#getObjectId()) | 获取对象 ID。                |
|                                                              | [findPropertyValue（字符串名称，布尔大小写敏感）](https://docs.katalon.com/javadoc/com/kms/katalon/core/testobject/TestObject.html#findPropertyValue(java.lang.String, boolean)) | 使用属性名称查找属性的值     |
| [关键字实用程序](https://docs.katalon.com/javadoc/com/kms/katalon/core/util/KeywordUtil.html) | [logInfo（字符串消息）](https://docs.katalon.com/javadoc/com/kms/katalon/core/util/KeywordUtil.html#logInfo(java.lang.String)) | 将消息记录为信息             |
|                                                              | [标记错误（字符串消息）](https://docs.katalon.com/javadoc/com/kms/katalon/core/util/KeywordUtil.html#markError(java.lang.String)) | 将关键字标记为错误           |
|                                                              | [markErrorAndStop（字符串消息）](https://docs.katalon.com/javadoc/com/kms/katalon/core/util/KeywordUtil.html#markErrorAndStop(java.lang.String)) | 将关键字标记为错误并停止执行 |
|                                                              | [标记失败（字符串消息）](https://docs.katalon.com/javadoc/com/kms/katalon/core/util/KeywordUtil.html#markFailed(java.lang.String)) | 将关键字标记为失败并继续执行 |
|                                                              | [markFailedAndStop（字符串消息）](https://docs.katalon.com/javadoc/com/kms/katalon/core/util/KeywordUtil.html#markFailedAndStop(java.lang.String)) | 将关键字标记为失败并停止执行 |
|                                                              | [标记通过（字符串消息）](https://docs.katalon.com/javadoc/com/kms/katalon/core/util/KeywordUtil.html#markPassed(java.lang.String)) | 标记要传递的关键字           |
|                                                              | [标记警告（字符串消息）](https://docs.katalon.com/javadoc/com/kms/katalon/core/util/KeywordUtil.html#markWarning(java.lang.String)) | 将关键字标记为警告           |

# 数据绑定--使用外部数据源运行测试用例

Katalon Studio 提供了使用外部数据源执行自动化测试的能力。

## 将 Excel 文件导入测试数据

请参阅[本文](https://docs.katalon.com/katalon-studio/docs/manage-test-data.html#create-an-excel-test-data)了解如何在 Katalon Studio 中创建新的 Excel 测试数据。所选 Excel 文件中的数据将填充到预览部分，如下例所示。

![](Sample Projects.assets/img-003-50.png)

## 使用测试用例变量创建新的测试套件

打开一个测试套件，从命令工具栏中选择**添加。**Katalon Studio 中的所有测试用例都将显示在“**测试用例浏览器**”对话框中。选定的测试用例将被添加到测试用例列表中，如下例所示。

![](Sample Projects.assets/img-003-51.png)

## 管理数据绑定

1. 在测试套件编辑器中，单击**Show Data Binding**以展开包含**Test Data**和**Variable Binding**表的**Data Binding**部分。

   ![](Sample Projects.assets/img-003-52.png)

2. 在**测试数据**表中，选择**添加**> 选择要用于执行的数据 > 将所选测试数据相应地添加到列表中。

   ![](Sample Projects.assets/img-003-53.png)

3. 在显示所选测试用例的所有变量的**数据绑定表中，选择所有行 > 选择****设置类型**> 选择**数据列**作为它们的类型。

   ![](Sample Projects.assets/img-003-54.png)

4. 单击**设置测试数据**以决定列表中要用于执行的测试数据。

   ![](Sample Projects.assets/img-003-55.png)

5. 单击**值**列中的每个单元格以指定所选数据文件中的数据字段。例如：

   ![](Sample Projects.assets/img-003-56.png)

6. 完成上述所有步骤后，保存并运行您的测试套件以查看以下结果：

   ![](Sample Projects.assets/img-003-57-164300549547345.png)

> **小建议：**
>
> 使用 **Map All** 按钮，您可以将所选测试用例的公共变量快速映射到测试数据中的相应列。要自动将变量绑定到数据，测试数据中的变量和相应列应共享**相同的名称**。\
>
> 例如，当您单击**Map All**时，所选测试用例的“用户名”和“密码”变量可以自动映射到测试数据的“用户名”和“密码”列。
>
> ![](Sample Projects.assets/img-003-58.png)





# 示例 Android 移动测试项目

此示例演示了 Katalon Studio 中的 Android 测试基础知识。

被测应用程序 (AUT) 是`APIDemos.apk`应用程序。您可以在本文档中了解有关移动测试的更多信息：移动测试[简介](https://docs.katalon.com/katalon-studio/docs/katalon_mobile_recorder_introduction.html#mobile-recorder)。

> 要求：
>
> - 安卓设置。要了解更多关于设置 Android 设备的信息，您可以参考此文档：[[Mobile\] Android Setup](https://docs.katalon.com/katalon-studio/tutorials/mobile-android-setup.html#set-up-android-tests-on-windows-linux-and-macos)。
> - 如果您使用的是 Android Studio，您可以参考此文档进行设置：[[手机\] 配置 Android Studio](https://docs.katalon.com/katalon-studio/docs/configure-android-studio.html)。

## 打开示例 Android 测试项目

要打开 Android 示例项目，请在 Katalon Studio 中转到**File > New Sample Project > Sample Android Mobile Tests Project**。如果您当前的机器没有安装 Android SDK 或者您的 Android SDK 不在默认文件夹中，Katalon Studio 会自动检测并要求您安装它：`~/.katalon/tools/android_sdk`.

![](Sample Projects.assets/img-003-59.png)

或者，您可以从我们的 Github 存储库下载 Android 示例项目：[Android 示例](https://github.com/katalon-studio-samples/android-mobile-tests)。

## Android 示例项目组件

### 简介

要打开执行配置文件，请转到**Profiles > default**。

![](Sample Projects.assets/img-003-60.png)

您可以在执行配置文件中创建和保存所有全局变量。它们可以在项目中的测试用例中使用。要了解有关执行配置文件和全局变量的更多信息，您可以参考此文档：[执行配置文件和全局变量](https://docs.katalon.com/katalon-studio/docs/execution-profile-v54.html)。

Katalon 在这个示例项目中创建了四个全局变量，如下所示：

| 名称                  | 价值                     |
| :-------------------- | :----------------------- |
| G_timeout             | 10                       |
| G_NotificationMessage | 您的留言已发送。查看消息 |
| G_AndroidApp          | androidapp/APIDemos.apk  |
| G_ShortTimeOut        | 5                        |

### 测试用例

要访问此项目中的测试用例，请转到“**测试资源管理器**”面板中的“**测试用例**”文件夹。

![](Sample Projects.assets/img-003-61.png)

有两个用于不同目的的测试用例：

1. 测试用例**Verify Correct Alarm Message**是为了验证我们是否能得到正确的显示信息。这个测试用例的流程如下：

   - 启动`APIDemos.apk`应用程序。在这里，AUT 的位置在`<sample-project-folder>/androidapp`文件夹下。我们使用以下示例代码来识别应用程序的绝对路径：

     ```
     /*Get full directory's path of android application*/
     def appPath = PathUtil.relativeToAbsolutePath(GlobalVariable.G_AndroidApp, RunConfiguration.getProjectDir())
     
     /*Start the AUT*/
     Mobile.startApplication(appPath, false)
     ```

   - 点击**应用程序**。我们将超时设置为 10 秒。

   - 点击**活动**。我们将超时设置为 10 秒。

   - 点击**自定义对话框**。我们将超时设置为 10 秒。

   - **验证App/Activity/Custom Dialog**对话框上显示的文本是否正确。

     ![](Sample Projects.assets/img-003-62.gif)

     ​											*单击 gif 将其放大。*

- 以脚本方式查看测试用例

  ```
  import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase
  import static com.kms.katalon.core.testdata.TestDataFactory.findTestData
  import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
  import internal.GlobalVariable as GlobalVariable
  import com.kms.katalon.core.configuration.RunConfiguration as RunConfiguration
  import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
  import com.kms.katalon.core.util.internal.PathUtil as PathUtil
  import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI
  import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS
  import static com.kms.katalon.core.checkpoint.CheckpointFactory.findCheckpoint
  import com.kms.katalon.core.model.FailureHandling as FailureHandling
  import com.kms.katalon.core.testcase.TestCase as TestCase
  import com.kms.katalon.core.testdata.TestData as TestData
  import com.kms.katalon.core.testobject.TestObject as TestObject
  import com.kms.katalon.core.checkpoint.Checkpoint as Checkpoint
  
  Mobile.comment('Story: Verify correct alarm message')
  
  Mobile.comment('Given that user has started an application')
  
  'Get full directory\'s path of android application'
  def appPath = PathUtil.relativeToAbsolutePath(GlobalVariable.G_AndroidApp, RunConfiguration.getProjectDir())
  
  Mobile.startApplication(appPath, false)
  
  Mobile.comment('And he navigates the application to Activity form')
  
  Mobile.tap(findTestObject('Alarm Message/android.widget.TextView - App'), 10)
  
  Mobile.tap(findTestObject('Alarm Message/android.widget.TextView - Activity'), 10)
  
  Mobile.comment('When he taps on the Custom Dialog button')
  
  Mobile.tap(findTestObject('Alarm Message/android.widget.TextView - Custom Dialog'), 10)
  
  'Get displayed message on the dialog'
  def message = Mobile.getText(findTestObject('Application/App/Activity/Custom Dialog/android.widget.TextViewCustomDialog'), 
      10)
  
  Mobile.comment('Then the correct dialog message should be displayed')
  
  Mobile.verifyEqual(message, 'Example of how you can use a custom Theme.Dialog theme to make an activity that looks like a customized dialog, here with an ugly frame.')
  
  Mobile.closeApplication()
  ```

2. 测试用例**Verify Last Items In List**是为了验证我们是否能识别出正确的列表中的最后一项。

- 启动`APIDemos.apk`应用程序。在这里，AUT 的位置在`<sample-project-folder>/androidapp`文件夹下。我们使用以下示例代码来识别应用程序的绝对路径：

  ```
  /*Get full directory path of the android application*/
  def appPath = PathUtil.relativeToAbsolutePath(GlobalVariable.G_AndroidApp, RunConfiguration.getProjectDir())
  
  /*Start the AUT*/
  Mobile.startApplication(appPath, false)
  ```

- 点击**图形**。我们使用`G_Timeout`全局变量作为超时值。

- 滚动到**Xfermodes**项目。

- 验证当前屏幕是否应在滚动后显示 Xfermodes 文本

![](Sample Projects.assets/img-003-63.gif)

- 以脚本方式查看测试用例

  ```
  import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase
  import static com.kms.katalon.core.testdata.TestDataFactory.findTestData
  import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
  import internal.GlobalVariable as GlobalVariable
  import com.kms.katalon.core.configuration.RunConfiguration as RunConfiguration
  import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
  import com.kms.katalon.core.util.internal.PathUtil as PathUtil
  
  Mobile.comment('Story: Verify correct alarm message')
  
  Mobile.comment('Given that user has started an application')
  
  'Get full directory\'s path of android application'
  def appPath = PathUtil.relativeToAbsolutePath(GlobalVariable.G_AndroidApp, RunConfiguration.getProjectDir())
  
  Mobile.startApplication(appPath, false)
  
  Mobile.comment('And he navigates the application to Graphics form')
  
  Mobile.tap(findTestObject('Last Items/android.widget.TextView - Graphics'), GlobalVariable.G_Timeout)
  
  Mobile.comment('When he scroll to Xfermodes text')
  
  Mobile.scrollToText('Xfermodes')
  
  Mobile.comment('Then the current screen should show Xfermodes text after scrolling')
  
  'Get item\'s label'
  def itemText = Mobile.getText(findTestObject('Last Items/android.widget.TextView - Xfermodes'), GlobalVariable.G_Timeout)
  
  Mobile.verifyEqual(itemText, 'Xfermodes')
  
  Mobile.closeApplication()
  ```

  ### 测试套件

  要访问此项目中的测试套件，请在“**测试资源管理器**”面板中，转到“**测试套件”>“回归测试**”文件夹。该测试套件结合了上面显示的两个测试用例。

  ![](Sample Projects.assets/img-003-64.png)

  ## 执行选定的测试用例或测试套件

  要在示例项目中执行测试用例或测试套件：

  1. 选择您要执行的测试用例/测试套件。

  2. 在主工具栏上，在**Run**旁边的下拉列表中选择**Android**作为设备类型。

     ![](Sample Projects.assets/img-003-65.png)

  3. 从 **Android 设备** 列表中选择您的设备。单击 **确定**。 

     ![](Sample Projects.assets/img-003-66.png)

  4. **在Log Viewer**选项卡中观察测试结果。想要了解更多关于分析测试执行日志的内容，可以参考这篇文档：[【WebUI】分析测试执行日志和调试测试用例](https://docs.katalon.com/katalon-studio/tutorials/webui-analyze-test-case-execution-logs-and-resolve-errors.html#analyze-test-execution-logs-in-log-viewer)。

     ![](Sample Projects.assets/img-003-67.png)

     *点击图片放大。*

     > 笔记：
     >
     > - 您可以在测试套件级别的**结果选项卡中查看测试结果。**测试结果可以是通过、失败、错误或不完整。要了解有关测试状态的更多信息，您可以参考此文档：[查看和自定义执行日志](https://docs.katalon.com/katalon-studio/docs/working-with-execution-log.html#view-execution-log)。
     > - 执行测试套件后，您可以在`<your-project-folder>/Reports`. Katalon Studio 还支持将测试报告导出为不同的格式，例如 HTML、CSV、PDF 和 JUnit。
     > - 要获得实时监控和更好的报告功能，请考虑将您的项目与 Katalon TestOps 集成。在此处了解有关测试结果报告的更多信息：[从 Katalon Studio 将测试结果上传到 Katalon TestOps](https://docs.katalon.com/katalon-studio/docs/katalon-analytics-beta-integration.html)。



# BDD 测试框架（Cucumber 集成）

## 添加功能文件

> 为了获得最佳性能，请经常清理 Katalon 工作区。导航到**文件**>**清理**。

功能文件位于项目文件夹中**的“包含/功能”**文件夹中，可以从*测试资源管理器*中看到：

![](Sample Projects.assets/img-003-68.png)

*功能*文件的内容将遵循 BDD 约定（_Given、When、The_n）。创建新*功能*文件时，将有一个“**生成示例功能模板**”选项，它将为您的*功能*文件生成示例模板。这将确保创建的*功能*文件与 BDD 约定匹配，以便您减少以正确格式 创建*功能文件的工作。*

![](Sample Projects.assets/img-003-69.png)

让我们看一个 Katalon Demo Cura System ( [http://demoaut.katalon.com) 的示例。](http://demoaut.katalon.com)./) 我们想使用有效和无效的凭据测试*登录*功能，因此内容将如下所示：

> 标签是组织功能和场景的好方法。[阅读更多...](https://docs.cucumber.io/cucumber/api/#tags)

![](Sample Projects.assets/img-003-70.png)

**样本特征文件**

```
#Author: your.email@your.domain.com
#Keywords Summary :
#Feature: List of scenarios.
#Scenario: Business rule through list of steps with arguments.
#Given: Some precondition step
#When: Some key actions
#Then: To observe outcomes or validation
#And,But: To enumerate more Given,When,Then steps
#Scenario Outline: List of steps for data-driven as an Examples and <placeholder>
#Examples: Container for s table
#Background: List of steps run before each of the scenarios
#""" (Doc Strings)
#| (Data Tables)
#@ (Tags/Labels):To group Scenarios
#<> (placeholder)
#""
## (Comments)
#Sample Feature Definition Template
@Login
Feature: Login Feature
  
  As a user, I want to login to Cura System
  so that I can make an appointment.

  @Valid
  Scenario Outline: Login with a valid credential
    Given I navigate to Cura System homepage
    When I click Make Appointment button
    And I enter username <username> and password <password>
    And I click Log in button 
	Then I should be able to login successfully

    Examples: 
      | username | password           |
      | John Doe | ThisIsNotAPassword |

  @InValid
  Scenario Outline: Login with an invalid credential
    Given I navigate to Cura System homepage
    When I click Make Appointment button
    And I enter an invalid username <username> and password <password>
    And I click Log in button
	Then I should NOT be able to login successfully

    Examples: 
      | username | password           |
      | Jane Doe | ThisIsNotAPassword |
```

## 维护特征文件

> Katalon Studio 代码检查将检测并突出显示*功能文件中任何缺失的**步骤定义*，以帮助用户创建所需的步骤定义。

当前*功能*文件会遇到以下维护困难之一：

- 当前格式组织不正确。
- 找出与当前*Gherkin*步骤映射的 *步骤定义*。
- *当步骤定义*发生变化时，重新计算*特征*文件中的步骤。

以上困难已直接从功能文件编辑器的上下文菜单中处理。

![](Sample Projects.assets/img-003-71.png)

**漂亮的格式**

重新做格式。

**查找步骤**

在现有步骤定义文件中查找当前 Gherkin 步骤的相关步骤。

**重新计算步骤**

当步骤定义发生变化时，重新计算特征文件中的步骤。

## 定义步骤

### 如何定义步骤

*Features*文件中的每个 Gherkin 步骤都需要定义为一组编程代码，以便机器可以执行这些步骤的动作。这些*步骤定义*可以通过利用**脚本模式在***关键字*文件夹中实现。Katalon Studio 内置关键字也可以在步骤定义文件中重复使用。当 Katalon Studio 执行测试用例中的任何*功能*文件时，它还将在源文件夹中查找匹配的步骤定义。

> 步骤定义可以用任何 Cucumber 支持的编程语言编写，包括 Groovy 和 Java。

例如，让我们从上面的*Features* File 中获取 Gherkin 场景并定义步骤：

![](Sample Projects.assets/img-003-72.png)

**步骤定义**

```
class MyStepDefinition {

	/**
	 * The step definitions below match with Katalon sample Gherkin steps
	 */

	@Given("I navigate to Cura System homepage")
	def I_navigate_to_Cura_System_homepage() {

		WebUI.openBrowser("http://demoaut.katalon.com")
		//WebUI.waitForPageLoad(30)
	}

	@When("I click Make Appointment button")
	def I_click_makeAppointment_button() {

		WebUI.click(findTestObject('Page_CURA Healthcare Service/a_Make Appointment'))
	}
 
	@And("I enter username (.*) and password (.*)")
	def I_enter_valid_username_password(String username, String password) {

		WebUI.setText(findTestObject('Page_CURA Healthcare Service/input_userName'), username)
		WebUI.setText(findTestObject('Page_CURA Healthcare Service/input_password'), password)
	}
 
	@And("I click Log in button")
	def I_click_login_btn() {

		WebUI.click(findTestObject('Page_CURA Healthcare Service/button_Login'))
	}
 
	@Then("I should be able to login successfully")
	def I_login_successfully() {

		WebUI.click(findTestObject('Page_CURA Healthcare Service/button_Login'))
		WebUI.verifyTextPresent('Make Appointment', false)
		WebUI.closeBrowser()
	}

	@And("I enter an invalid username (.*) and password (.*)")
	def I_enter_invalid_username_password(String username, String password) {
		
		WebUI.setText(findTestObject('Page_CURA Healthcare Service/input_userName'), username)
		WebUI.setText(findTestObject('Page_CURA Healthcare Service/input_password'), password)
	}

 
	@Then("I should NOT be able to login successfully")
	def I_login_unsuccessfully() {

		WebUI.verifyTextPresent('Login failed! Please ensure the username and password are valid.', false)
		WebUI.closeBrowser()
	}

}
```

### 为步骤定义设置默认包

> 在 7.8 及更高版本中可用

您可以使用 为 Cucumber 定义步骤定义的位置`CucumberKW.GLUE = ['package1', 'package2']`。的默认值`CucumberKW.GLUE = ['']`是所有包，这意味着测试引擎需要时间来扫描所有包。定义特定位置可以缩小包的范围，以便在执行功能文件之前找到步骤定义；因此，减少了执行时间。

我们建议将指向包的脚本放在测试侦听器中。

```
import com.kms.katalon.core.annotation.AfterTestCase
import com.kms.katalon.core.annotation.BeforeTestCase
import com.kms.katalon.core.context.TestCaseContext
import com.kms.katalon.core.cucumber.keyword.CucumberBuiltinKeywords as CucumberKW

class NewTestListener {
	@BeforeTestCase
	def sampleBeforeTestCase(TestCaseContext testCaseContext) {
		CucumberKW.GLUE = ['package1', 'package2']
	}
}
```

## 运行功能文件

### 从工具栏

Katalon Studio 允许您立即自行运行功能文件，以确保其正常工作。打开所需的**功能**文件，单击主工具栏上的 **播放** 按钮。

![](Sample Projects.assets/img-003-73.png)

### 在测试用例中

Katalon Studio 支持 Cucumber 关键字以及原始内置关键字。用户不必将 Cucumber 库导入 Katalon Studio。

在 Katalon Studio 测试用例中包含 Cucumber *Feature文件：*

**执行单个功能文件（带或不带标签）**

- [运行特征文件](https://docs.katalon.com/katalon-studio/docs/cucumber-kw-run-feature-file.html)
- [运行FeatureFileWithTags](https://docs.katalon.com/katalon-studio/docs/cucumber-kw-run-feature-file-tag.html)

**执行多个功能文件（带或不带标签）**

- [运行功能文件夹](https://docs.katalon.com/katalon-studio/docs/cucumber-kw-run-feature-folder.html)
- [运行FeatureFolderWithTags](https://docs.katalon.com/katalon-studio/docs/cucumber-kw-run-feature-folder-tag.html)

**使用[Cucumber Runner执行](http://toolsqa.com/cucumber/junit-test-runner-class/)**

- [runWithCucumberRunner](https://docs.katalon.com/katalon-studio/docs/cucumber-kw-run-cucumber-runner.html)

## Cucumber报告

### 在 Katalon 测试操作中

Katalon TestOps 专门支持查看 BDD 测试结果以及高级分析和报告，例如 Traceability Matrix Report。要了解溯源矩阵报告，可以参考本文档：[溯源矩阵报告](https://docs.katalon.com/katalon-analytics/docs/view-traceability-matrix.html)。

默认情况下，Katalon TestOps 上的 BDD 测试报告功能被禁用，以避免混合 BDD 和 Katalon Studio 格式的数据。要启用该功能，您可以参考本指南：[在 Katalon TestOps 中查看 BDD 测试结果](https://docs.katalon.com/katalon-analytics/docs/bdd-test-results.html)。

### In Katalon Studio

没有用于执行特征文件的自定义报告**。**Katalon Studio 仅使用为 **Test Suite/Test Suite Collection**执行**级别生成的 Cucumber****报告**，其中测试用例包含 Cucumber Features 文件。

Test Suite/Test Suite Collection 生成的 Cucumber 报告将位于 Katalon Studio 报告文件夹的同一文件夹中。在 Katalon Studio 测试资源管理器中，右键单击所需的 **Report > Open Containing Folder**。Katalon Studio 会将您重定向到存储 Cucumber 报告的本地文件夹。 

Katalon Studio 支持Cucumber 报告的**三种**格式：JSON、XML、HTML。

![](Sample Projects.assets/img-003-74.png)

