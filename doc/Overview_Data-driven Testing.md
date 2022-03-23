# 一、使用 Katalon Studio 进行数据驱动测试

Katalon Studio 通过多种方法支持数据驱动测试，这些方法允许测试脚本从内部或外部数据文件中读取输入。特别是，在 Katalon 测试用例中，测试对象或其属性可以参数化为占位符并在执行期间接收值。您可以使用以下方法在 Katalon Studio 中设计数据驱动的测试脚本：

- [Web 测试对象参数化](https://docs.katalon.com/katalon-studio/docs/manage-test-object.html)
- [移动测试对象参数化](https://docs.katalon.com/katalon-studio/docs/parameterize-mobile-test-object-properties.html)
- [Web 服务对象参数化](https://docs.katalon.com/katalon-studio/docs/parameterize-a-web-service-object.html)

有许多方法可以通过测试脚本中的参数传递不同的值集。

1. [全局变量和参数化全局变量](https://docs.katalon.com/katalon-studio/docs/global-variables.html)。
2. [测试用例变量](https://docs.katalon.com/katalon-studio/docs/test-case-variables.html)。
3. [数据绑定功能](https://docs.katalon.com/katalon-studio/docs/run-test-case-external-data.html)和[增强的变量绑定](https://docs.katalon.com/katalon-studio/docs/bind-as-string.html)。
4. `findTestData`Groovy 脚本中的方法。了解[TestData](https://docs.katalon.com/javadoc/com/kms/katalon/core/testdata/TestData.html)。

通过测试脚本传递的输入可以从外部文件中读取，例如 Excel、CSV、内部文件和数据库。了解如何[管理测试数据](https://docs.katalon.com/katalon-studio/docs/manage-test-data.html)。

对于 Katalon Studio 的高级 DDT 功能，Katalon Studio Enterprise 用户可以在数据绑定部分[组合多个数据源](https://docs.katalon.com/katalon-studio/docs/combine-multiple-data-sources.html)。

Katalon Studio 中的 DDT 示例可以在[购物车项目](https://docs.katalon.com/katalon-studio/docs/shopping-cart-prj.html#test-suites)中具体查看，这是 Katalon 团队编写的示例项目。



# 1、Web 测试对象

## 在手动视图中

### 创建测试对象

您可以通过两种方式创建测试对象：

- 从主菜单中，选择 **File > New > Test Object**；要么
- 右键单击**对象存储库**> 选择**新建 > 测试对象**

在显示的 **新测试对象** 对话框中，为新测试对象提供名称，然后单击 **确定** 按钮。新的测试对象在 Katalon Studio的**Object Repository下创建。**

[此外，您可以使用 Web Spy](https://docs.katalon.com/katalon-studio/docs/spy-web-utility.html)或[Recorder](https://docs.katalon.com/katalon-studio/docs/record-web-utility.html)捕获对象。

### 创建对象的定位器

您可以将多个定位器添加到一个对象，但您必须选择其中一个作为默认定位器。默认定位器用于在测试执行期间检测对象。从 7.6 开始，您可以使用[自愈机制](https://docs.katalon.com/katalon-studio/docs/self-healing.html)来利用对象的多个定位器。

Katalon Studio 支持[以下选择方法](https://docs.katalon.com/katalon-studio/docs/web-selection-methods.html)：XPath、Attributes、CSS 和 Image。您可以自由地从一种选择方法切换到另一种选择方法。自动保存每种选择方法的详细内容。

- **XPath/CSS ：在****Selected Locator**中输入所需的 XPath 定位器。

- **图像**：浏览图像以构成对象的图像定位器。[了解更多](https://docs.katalon.com/katalon-studio/docs/web-image-based-object-recognition.html)

- **属性**：在**对象的属性**表中检查一个或多个**检测对象，**为对象组成此方法的**选定定位器。**

  您可以将多个对象属性添加到**对象的属性**表中。请注意，对象属性不能在对象中共享相同的名称。

1. 在**Test Object**的视图中，选择**Attributes**作为默认选择方法。
2. 在**对象的属性**表中，单击 **添加**。
3. 在显示的 **添加属性** 对话框中，指定所需的信息：
   ![](Overview_Data-driven Testing.assets/img-011-01.png)

在哪里：

- **Name**：对象属性的名称。您可以选择提供的选项之一（类、css、id、名称、标题、xpath）或手动输入名称。

- **匹配条件**：该条件用于在执行过程中检测目标对象。

- **Value**：完成匹配条件的值。

  新属性将添加到上面配置的属性列表中。您还可以在此处更改属性的值。

  

## 管理父对象

[如今，在iframe](https://www.w3schools.com/tags/tag_iframe.asp)中有许多 Web 应用程序渲染元素 。因此，您必须告诉您的脚本如何遍历网站的 **iframe**并选择 文本及其对象所在 的正确 **iframe 。**为此，您必须在与元素交互之前使用“[切换到框架”关键字。](https://docs.katalon.com/display/KD/[WebUI]+Switch+To+Frame)

Katalon Studio 支持在测试对象视图中定义父 iframe 对象的功能，因此您只需选择父 iframe，执行会自动切换到该 iframe。

![img-011-02](Overview_Data-driven Testing.assets/img-011-02.png)

## 在脚本视图中

**脚本视图**允许以编程方式定义 **测试对象。**以下示例演示了如何使用 Attributes、XPath 和 CSS 选择方法定义**Medicare选项。**

![img-011-03](Overview_Data-driven Testing.assets/img-011-03.png)

1. 使用类以编程方式创建一个新对象 `TestObject` ：

   ```
   // Create a new object programmatically
   TestObject myNewObject = new TestObject('ObjectID')
   ```

2. 添加对象定位器

- 使用**Attributes**选择方法，使用以下`addProperty()` 方法向对象添加属性：

  ```
  //Attributes
  //Add property to Test Object, a property is defined by:
  // property name,
  // condition type,
  // property value,
  // a boolean value to indicate if the property will be used to identify the object during execution
  myNewObject.setSelectorMethod(SelectorMethod.BASIC)
  myNewObject.addProperty('xpath', "//*[@id=\"appointment\"]/div/div/form/div[3]/div/label[1]", true) //Medicare
  ```

- 使用**XPath**或**CSS**选择方法：指定选择方法并为定位器设置值：

  ```
  //XPATH
  myNewObject.setSelectorValue(SelectorMethod.XPATH,"//*[@id=\"appointment\"]/div/div/form/div[3]/div/label[1]") //Medicare
  myNewObject.setSelectorMethod(SelectorMethod.XPATH)
  ```

![](Overview_Data-driven Testing.assets/img-011-04.png)

```
//CSS
myNewObject.setSelectorValue(SelectorMethod.CSS,"#appointment > div > div > form > div:nth-child(3) > div > label:nth-child(1)") //Medicare
myNewObject.setSelectorMethod(SelectorMethod.CSS)
```

![](Overview_Data-driven Testing.assets/img-011-05.png)

以下 Java 文档在使用测试对象时可能会很有用：

| 班级                                                         | 方法                                                         | 描述                       |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :------------------------- |
| [测试对象](https://docs.katalon.com/javadoc/com/kms/katalon/core/testobject/TestObject.html) | [addProperty（字符串名称，ConditionType 条件，字符串值）](https://docs.katalon.com/javadoc/com/kms/katalon/core/testobject/TestObject.html#addProperty(java.lang.String, com.kms.katalon.core.testobject.ConditionType, java.lang.String)) | 向测试对象添加一个新属性。 |
|                                                              | [setProperties（列出  属性）](https://docs.katalon.com/javadoc/com/kms/katalon/core/testobject/TestObject.html#setProperties(List)) | 设置测试对象的属性。       |
|                                                              | [获取对象标识（）](https://docs.katalon.com/javadoc/com/kms/katalon/core/testobject/TestObject.html#getObjectId()) | 获取对象 ID。              |
|                                                              | [findPropertyValue（字符串名称，布尔大小写敏感）](https://docs.katalon.com/javadoc/com/kms/katalon/core/testobject/TestObject.html#findPropertyValue(java.lang.String, boolean)) | 使用属性名称查找属性的值。 |

## 验证测试对象

您可以将测试对象添加到 **Web Object Spy** 对话框，以验证被测应用程序中的检测。要将对象添加到 **Web Object Spy**，请右键单击该项目以打开其上下文菜单并选择该选项。

![](Overview_Data-driven Testing.assets/img-011-06.png)

### 验证并突出显示

Katalon Studio **对象属性** 具有内置的 **验证和突出显示**功能，可帮助用户仔细检查是否可以找到 Web 对象。 Katalon Studio 将显示有关使用生成的 XPath 定位器**找到** 或未 **找到**多少元素的消息 。如果 **找到**对象，它将以 **红色**边框突出显示。

![](Overview_Data-driven Testing.assets/img-011-07.png)

完成后，单击 **保存**将对象正常 添加到 **对象存储库** 。

## 视觉对象识别

图像定位器允许您使用图像识别测试对象并执行基于 Web 图像的测试。[在基于 Web 图像的测试](https://docs.katalon.com/katalon-studio/docs/web-image-based-testing.html)中了解更多信息。

### 启用基于图像的对象识别

**从 7.6 开始**

**默认情况下，在Project > Settings > Self-Healing > Web UI > Test Execution**中为 Web 测试执行启用基于图像的对象识别（[请参阅自我修复测试](https://docs.katalon.com/katalon-studio/docs/self-healing.html)）。

![](Overview_Data-driven Testing.assets/img-011-08.png)

**7.6之前**

默认情况下，在项目设置中禁用基于图像的对象识别。请前往**Project > Settings > Execution**并勾选**Enable Image Recognition**以开启此回退策略。

![](Overview_Data-driven Testing.assets/img-011-09.png)

### 捕获屏幕截图并创建对象的屏幕截图属性

基于图像的对象定位工作所需的要素包括：

- 目标网页元素的屏幕截图
- 该元素的屏幕截图属性

有两种方法可以创建所需的成分：

- [使用 Web Recorder 和 Spy 中的内置功能](https://docs.katalon.com/katalon-studio/docs/web-image-based-object-recognition.html#use-built-in-tool)
- [使用手动方式](https://docs.katalon.com/katalon-studio/docs/web-image-based-object-recognition.html#use-other-tools)

在 Tests Explorer 的**Screenshots**文件夹下，您可以看到**Matched Elements**和**Targets**文件夹。

- **Matched Elements**文件夹包含 Katalon Studio 基于目标图像定位的对象。

- **Targets**文件夹用于包含 Katalon Studio 用于定位对象的图像 。

  ![](Overview_Data-driven Testing.assets/img-011-10.png)

> 有关示例项目，请[在此处下载](https://github.com/katalon-studio-samples/image-recognition-web)

### 影响图像比较的因素

**屏幕分辨率**：测试执行机和截屏机的屏幕分辨率可能会影响图像比对的有效性。我们建议在同一台机器上捕获屏幕截图并执行测试以获得更好的结果。

**捕获工具**：要捕获与您喜欢的 Web 元素相关的屏幕截图，我们建议使用 Web Recorder 和 Spy Tools 中的内置屏幕捕获功能。特别是，在单击**Show Captured Objects**后的展开视图中，选择右下角 的**Add Screenshot按钮。**

![](Overview_Data-driven Testing.assets/img-011-11.png)

## 使用 Shadow DOM 对象

[Shadow DOM](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Shadow_DOM)为 Web 开发人员提供了一个强大而有用的解决方案。然而，这对自动化测试来说是一个挑战，因为影子根中的影子 DOM 元素在技术上并不存在于主文档中。因此，依赖 XPath 或 querySelector 来发现元素的测试自动化框架不适用于 Shadow DOM。

Katalon Studio 允许用户使用 Shadow DOM 元素。首先，用户需要使用 Spy Web 功能来捕获包含 Shadow DOM 元素的父对象。

下一步是识别 Shadow DOM 元素的属性，并在 Katalon Studio 中创建一个具有相应定义属性的新对象。

在新的对象设置中，选择**Shadow Root Parent**选项并从第一步中定义父对象。这允许 Katalon Studio 通过生成的 CSS 选择器遍历父对象，以通过其属性检测 Shadow DOM 对象（请参阅[对象属性](https://docs.katalon.com/display/KD/Manage+Test+Object#ManageTestObject-Propertiesusedfordetectingobject)）。

![](Overview_Data-driven Testing.assets/img-011-12.png)

例如，以下测试执行日志显示 Katalon Studio 尝试首先查找父对象。一旦找到父对象，Katalon Studio 将尝试通过 CSS 选择器查找 Shadow DOM 元素：

![](Overview_Data-driven Testing.assets/img-011-13.png)

### 限制

- 仅适用于**[Chrome](http://caniuse.com/#feat=shadowdom)**浏览器（53 至最新版本）。其他浏览器将被考虑用于未来的版本。
- 仅允许 1 级嵌套 Shadow DOM 父级
- 记录和间谍功能不适用于 Shadow DOM（由于 DOM 中不存在元素）。

## 在运行时修改对象属性

如果您有多个相似的对象想要在测试执行期间快速交互，并且您真的不想花时间编写重复的步骤来与它们交互，那么下面的方法将帮助您减少时间并使您的代码更好：

使用 CSS 或 XPath 定位您的元素，然后您开始更改 ID（比方说）。例如：

```
TestObject yourObject = WebUI.modifyObjectProperty(findTestObject('Object Repository/Some object'), 'css', 'equals', '#${i}', true)
```

其中“i”是循环计数器。您可以将其全部放在一个循环中，该循环将读取您的 excel 表：

```
for (def i=0; i <= fineTestData('Path to your excel').getRowNumbers(); i++) {}
https://www.katalon.com/resources-center/tutorials/data-driven-testing/ for linking data with test.
```

*[归功于 Mate](https://forum.katalon.com/discussion/7010/how-to-test-clicking-multiple-objects-without-starting-over#lComment_16209) Mrse*

## 在运行时在内存中创建测试对象

您可以在运行时使用此自定义关键字在对象存储库中创建新的测试对象：

```
/**
* Construct a Katalon-compatible TestObject in memory.
* @param css (String) The CSS selector used to find the target element.
* @return (TestObject) The constructed TestObject. 
*/
@Keyword
static TestObject makeTO(String css) {
	TestObject to = new TestObject()
	to.addProperty("css", ConditionType.EQUALS, css)
	return to
}
```

*归功于[ *[Russ Thomas](https://forum.katalon.com/discussion/6171/creation-of-test-object-in-object-repository-in-runtime#Comment_13991)*](https://forum.katalon.com/discussion/6171/creation-of-test-object-in-object-repository-in-runtime#Comment_13991)*



# 2、参数化移动测试对象

> 参数化移动测试对象属性仅适用于**属性**选择方法。

参数化移动测试对象的好处类似于参数化 Web 测试对象的好处。有关详细信息，请参阅[本文档](https://docs.katalon.com/katalon-studio/docs/parameterize-web-test-object-properties.html)。

## 使用示例

以下是如何在移动测试中参数化测试对象的示例。**通过访问File> New Sample Project> Sample Android Mobile Tests Project**打开 Android 设备上的移动测试示例项目。

在 Tests Explorer 中导航到**Object Repository/Application/android.widget.TextView - App**`android.widget.TextView - App` ，打开其属性将被参数化的测试对象视图。

在这个例子中，我们想要找到一个具有`//*[(text() = 'demokatalon' or . = 'demokatalon')]`选择器的测试对象。以下是应用此功能的步骤：

### 步骤 1：参数化测试对象的动态属性

创建一个属性，其值为具有以下语法的变量：`${Variable_name}`. 对于这个例子，在**对象的属性**面板中，添加一个对象的属性：

- 姓名：`text`
- 价值：`${text}`

其选定的定位器`//*[(text() = '${text}' or . = '${text}')]`在运行时生成并通过传递数据进行标识。

![](Overview_Data-driven Testing.assets/img-011-14.png)

### 步骤 2：在测试用例中使用参数化的测试对象

- **在手动视图中**

  在`Verify Correct Alarm Message`测试用例中，双击包含参数化属性的测试对象，即`android.widget.TextView - App`. 将显示**测试对象输入**对话框。

  ![](Overview_Data-driven Testing.assets/img-011-15.png)

在“变量”面板中，添加具有以下属性的新变量：

- Param Type：变量类型（默认类型为String）。

- param：第一步创建的属性的变量名。

- 值类型：变量值的类型。

- 值：该变量的特定值。

  ![](Overview_Data-driven Testing.assets/img-011-16.png)

- **在脚本视图中**

  您也可以随时切换到当前测试用例的**脚本模式来调整属性的值。**当您从手动模式选择移动对象时，预定义变量会自动映射，因此您无需再次手动定义它们。

### 第 3 步：在关键字中调用 findTestObject 方法

在此示例中，`tap`关键字是在具有我们刚刚指定的文本值的对象上执行的。

```
Mobile.tap(findTestObject('Application/android.widget.TextView - App', [('text') : 'demokatalon']), 10)
```

## 转义特殊字符

要在任何使用参数化测试对象的地方使用特殊字符`$`或常规字符，请在其前面加上反斜杠：（所谓的转义字符）。`\``\`

```
{
 	"productName": ${GlobalVariable.productName},
  	"unit": "\\bottle\",
  	"quantity": 50,
  	"discount": ${ if (productName == "wine") { return 30 } else { return 0}}
	"note": "Currency unit of ${GlobalVariable.productName} is \$."

}
```

- 没有`\`:*注意： ${GlobalVariable.productName} 的货币单位是 $*。
- 附`\`：*注意：酒的货币单位是$*。



# 3、参数化 Web 服务对象

## 查询参数

> 仅适用于**RESTful** Web 服务请求

可以将查询参数添加到 REST 请求的 URL 以定制和过滤响应输出。当您输入 URL 时，Katalon Studio 会检测查询参数（在问号之后`?`）并将其列在表格中以便更好地管理。

![img-011-17](Overview_Data-driven Testing.assets/img-011-17.png)

## 变量和参数化请求对象

> 适用于**RESTful**和**SOAP** Web 服务请求

Katalon Studio 为**变量**部分提供手动和脚本编辑器。通过在请求对象中使用变量，您可以处理对象属性的动态值并对它们进行更多控制。**您可以在“变量**”选项卡中添加新变量并声明其属性 。要调用 Web 服务对象中的变量，请在任何受支持的位置使用**${variable_name}**语法作为占位符。预定义变量的值在运行时分别传递给它们的占位符。它称为参数化，方法与[参数化 WebUI 对象](https://docs.katalon.com/katalon-studio/docs/manage-web-test-object.html#parameterize-web-test-objects)相同。

在测试用例的手动视图中，当您添加请求对象时，会**自动**添加预定义变量；因此，您无需再次定义它们。

### 对于 RESTful 请求

Katalon Studio 支持在 RESTful Web 服务对象的以下位置调用声明的变量。

- 网址
- 查询参数
- HTTP 标头
- HTTP 正文
- 确认

下面的屏幕截图说明了在 URL 中使用“**状态**”变量的示例。

![](Overview_Data-driven Testing.assets/img-011-18.png)

### 对于基于 SOAP 的请求

您可以在以下位置使用预定义变量：

- WSDL 网址
- 服务端点（从 7.5.5 版开始提供）
- HTTP 标头
- 请求消息
- 确认

下面是在 SOAP 请求的服务端点中参数化域 URL 的示例。

![](Overview_Data-driven Testing.assets/img-011-19.png)

## 将测试请求添加到测试用例

有多种方法可以将测试请求对象添加到测试用例 Katalon Studio。您可以在测试用例的手动视图（关键字测试）或脚本视图（测试脚本）中调用 Web 服务请求，并验证响应。



# 4、在测试用例中使用 Web 服务

Katalon Studio 支持在测试用例中使用 Web 服务对象的各种方式。您可以从手动视图（关键字测试）、脚本视图（测试脚本）调用 Web 服务方法，并验证响应。 

### 在测试请求对象视图中

您可以直接从*对象详细信息视图***将**Web 服务请求添加到测试用例。只需单击*加号*图标即可添加到*新*测试用例或任何*现有*测试用例。

![](Overview_Data-driven Testing.assets/img-011-20.png)

### 在测试用例编辑器的手动视图中

按照以下步骤在 **手动** 视图中使用 Web 服务对象：

1. **在手动**视图中打开一个测试用例 ，然后 从命令工具栏中 选择添加 ****Web Service Keyword**。**
   ![](Overview_Data-driven Testing.assets/img-011-21.png)

2. 一个 Web 服务步骤被添加到测试用例中。 
   要向 Web 服务发送请求，您需要使用 **[Send Request](https://docs.katalon.com/display/KD/[WS]+Send+Request)** 关键字。现在选择 **[发送请求](https://docs.katalon.com/display/KD/[WS]+Send+Request)** 关键字。
   ![](Overview_Data-driven Testing.assets/img-011-22.png)

3. 双击对象单元格以指定要 **[发送请求](https://docs.katalon.com/display/KD/[WS]+Send+Request)**的 Web 服务对象。

   > Web 服务测试对象的变量
   >
   > 当您在测试用例中修改 Web 服务测试对象的变量时，这些值将仅适用于该特定测试用例。如果您在另一个测试用例中重用该测试对象，Katalon Studio 将获得在测试对象编辑器中定义的原始值。

   ![](Overview_Data-driven Testing.assets/img-011-23.png)

4.  如果需要，可以根据您的情况 使用不同的 **[Verify...关键字来验证](https://docs.katalon.com/display/KD/Web+Service)****[Send Request](https://docs.katalon.com/display/KD/[WS]+Send+Request)**关键字的输出 。

### 在测试用例编辑器的脚本视图中

您可以使用 Web 服务对象 的**[Send Request关键字和](https://docs.katalon.com/display/KD/[WS]+Send+Request)****[Verify...](https://docs.katalon.com/display/KD/Web+Service)** 关键字来验证 Web 服务响应。您可能需要参考 [处理响应消息](https://docs.katalon.com/katalon-studio/docs/using-web-services-in-a-test-case.html#UsingWebServicesinaTestCase5.8-HandleResponsemessages) 以获取有关 **Element Locator**的更多详细信息：

```
//Send a SOAP request and returns its response
def response = WS.sendRequest(findTestObject([]))
//Verify if a value at a specific location in response is as expected
WS.verifyElementPropertyValue(response, <Element Locator>, <expected value>)
```

例如：

![img-011-24](Overview_Data-driven Testing.assets/img-011-24.png)

如果您[在测试请求中使用了变量和参数](https://docs.katalon.com/katalon-studio/docs/parameterize-a-web-service-object.html#variables-and-parameterizing-request-objects)，则可以将值传递给变量，如下所示：

```
//Send a test request and pass values to variables used in that request
def response = WS.sendRequest(findTestObject([the ID of Web Service object], ["variable1": value1, "variable2": value2, ... , "variableN": valueN]))
```

例如：

![img-011-25](Overview_Data-driven Testing.assets/img-011-25.png)

以下 API 文档在使用 Web 服务对象时可能很有用：

| 班级                                                         | 描述                       |
| :----------------------------------------------------------- | :------------------------- |
| **[请求对象](http://api-docs.katalon.com/studio/v4.6.0.2/api/com/kms/katalon/core/testobject/RequestObject.html)** | 描述请求对象的所有可用方法 |
| **[响应对象](http://api-docs.katalon.com/studio/v4.6.0.2/api/com/kms/katalon/core/testobject/ResponseObject.html)** | 描述响应对象的所有可用方法 |



# 5、全局变量和执行配置文件

## 执行配置文件

**执行配置文件**有助于覆盖多种不同的环境，以轻松执行您的自动化测试脚本。**您可以通过全局变量**在数据和行为方面配置测试环境。

### 创建个人资料

与其他测试工件一样，您可以在**Tests Explorer中对****执行配置文件**进行CRUD 。

![](Overview_Data-driven Testing.assets/img-011-26.png)

您需要通过添加[全局变量](https://docs.katalon.com/katalon-studio/docs/execution-profile-v54.html#global-variables)来定义配置文件的内容。执行以下操作：

1. 选择配置文件 > 单击**添加**。

2. 在“**新建变量”**对话框中，指定变量的详细信息 > 单击“**确定**” 。
   ![](Overview_Data-driven Testing.assets/img-011-27.png)

3. 该变量被相应地添加到配置文件中。

   ![](Overview_Data-driven Testing.assets/img-011-28.png)

### 查看个人资料

执行配置文件提供**手动视图**和**脚本视图**。在脚本视图中，可以使用 XML 编辑器通过脚本添加变量。根据项目需要，您可以创建任意数量的配置文件。

在**脚本视图**中，一旦需要类似的**全局变量**列表来测试不同的环境类型，配置文件就会同步。要执行，请将变量列表从一个配置文件复制并粘贴到另一个配置文件。

 ![](Overview_Data-driven Testing.assets/img-011-29.png)

### 在项目级别设置默认配置文件

> 在**v7.4.2**中引入，您可以在项目级别设置默认配置文件。

默认配置文件被视为包含常用全局变量的位置。其他配置文件可以继承或覆盖存储在默认配置文件中的全局变量。阅读有关[配置文件继承](https://docs.katalon.com/katalon-studio/docs/execution-profile-v54.html#inheritance-profile)的更多信息。

您可能有多个配置文件来执行您的测试，例如，*登台*和*生产*配置文件。在项目的每次执行中将配置文件设置为默认配置文件会很方便。

右键单击所需的执行配置文件并选择**Set as default Execution Profile**。

![](Overview_Data-driven Testing.assets/img-011-30.png)

此配置文件成为测试用例、测试套件和测试套件集合的默认执行选项。

![](Overview_Data-driven Testing.assets/img-011-31.png)

如果您使用 Katalon 运行时引擎，它也适用于命令生成器的执行平台。

![](Overview_Data-driven Testing.assets/img-011-32.png)

### 配置文件继承

**配置文件继承**减少了您在派生配置文件中修改和重新创建相同全局变量的工作量。假设 Katalon Studio 在指定配置文件（除默认配置外的任何配置文件）中找不到测试中使用的变量。在这种情况下，它将查看默认配置文件并使用其变量来执行测试。

**如何使用配置文件继承**

常用的全局变量应存储在**默认**配置文件中，并应将其他全局变量集存储在**派生**（自定义）配置文件中，以避免重复代码并更好地管理。

**运行示例**

以下示例说明了**配置文件继承**功能的工作原理。

- 给定以下测试用例：
  ![](Overview_Data-driven Testing.assets/img-011-33.png)
- 使用给定的测试用例执行默认配置文件：

![](Overview_Data-driven Testing.assets/img-011-34.png)

结果如下图所示：

![](Overview_Data-driven Testing.assets/img-011-35.png)

★ 使用给定的测试用例执行分段和生产配置文件：

在执行 staging 和 production 配置文件时，**name**、**serveURL**和**credential**变量被覆盖（以红色突出显示），而**usage**和**reference**变量从默认配置文件中的全局变量继承（以蓝色突出显示）。

- 分期简介：

![](Overview_Data-driven Testing.assets/img-011-36.png)

结果如下图所示：

![](Overview_Data-driven Testing.assets/img-011-37.png)

生产概况：

![](Overview_Data-driven Testing.assets/img-011-38.png)

结果如下图所示：

![](Overview_Data-driven Testing.assets/img-011-39.png)

### 使用个人资料

默认情况下，Katalon Studio 使用**默认**配置文件执行测试，如屏幕右上角所示。您可以在下拉菜单中选择任何可用的执行配置文件。

以下部分向您展示了一个使用示例。有基于测试环境的三个配置文件：**local**、**staging**和**production**。

- **对于测试用例或测试套件**：在右上角选择所需的配置文件 >当前项目中的**所有全局变量自动使用这些值。**
  ![](Overview_Data-driven Testing.assets/img-011-40.png)
- **对于测试套件集合：在****Profile**列中选择要与您的测试套件一起执行的所需配置文件。
  ![](Overview_Data-driven Testing.assets/img-011-41.png)
- **对于[控制台模式](https://docs.katalon.com/display/KD/Console+Mode+Execution)执行：在****配置文件**字段中选择您想要的配置文件。

![](Overview_Data-driven Testing.assets/img-011-42.png)

- **Generated Command**具有**executionProfile**参数，以便您可以手动更改它。例如：

  ```
  katalonc -noSplash  -runMode=console -consoleLog -projectPath="C:\Users\Admin\Katalon Studio\yourProject.prj" -retry=0 -testSuitePath="Test Suites/TS_RegressionTest" -executionProfile="local" -browserType="Chrome (headless)
  ```

## 全局变量

**全局变量**是在执行配置文件中定义的变量，可用于项目中的测试用例、测试对象、Web 服务对象和电子邮件配置。

### 全局变量的范围

**全局变量是测试套件范围**的。如果在运行时更改了任何全局变量值，则此更改将不会在测试套件之间共享。这意味着您可以在执行特定测试套件时修改全局变量，而不会影响测试套件集合中其他测试套件的全局变量。

您可以发现“测试套件/新测试套件 (1)”在以下屏幕截图中列出了两次。第一个使用“默认”，第二个使用“分期”。此关联证明**Profile 是 Test Suite scoped**。否则，该关联不能在逻辑上有效。

![](Overview_Data-driven Testing.assets/img-011-43.png)

### 使用全局变量

项目中的任何测试用例都可以使用全局变量——例如，[手动视图](https://docs.katalon.com/display/KD/Manual+View)中关键字的输入数据（以蓝色突出显示）或[为测试执行绑定数据](https://docs.katalon.com/display/KD/Design+a+Test+Suite#DesignaTestSuite-VariableBinding)时的参数（以红色突出显示）。

![](Overview_Data-driven Testing.assets/img-011-44.png)

### 参数化全局变量

您可以在 WebUI、Mobile、Windows 和 API 测试对象中直接参数化全局变量。要参数化全局变量，请`${GlobalVariable.name}`在每种类型支持的位置输入语法。

- [Web 测试对象](https://docs.katalon.com/katalon-studio/docs/parameterize-web-objects.html)
- [移动测试对象](https://docs.katalon.com/katalon-studio/docs/parameterize-mobile-test-object-properties.html)
- [Windows 测试对象](https://docs.katalon.com/katalon-studio/docs/windows-test-objects.html#parameterize-windows-test-objects)
- [RESTful 请求](https://docs.katalon.com/katalon-studio/docs/parameterize-a-web-service-object.html#for-restful-request)
- [基于 SOAP 的请求](https://docs.katalon.com/katalon-studio/docs/parameterize-a-web-service-object.html#for-soap-based-request)。

例如：

- 在 API 测试对象的 HTTP 正文中：
  ![](Overview_Data-driven Testing.assets/img-011-45.png)
- 在 WebUI 测试对象的选定定位器中：
  ![](Overview_Data-driven Testing.assets/img-011-46.png)
- 在 Web 服务请求的请求 URL 中：

![](Overview_Data-driven Testing.assets/img-011-47.png)

### 使用转义字符、特殊字符

要在调用参数化全局变量的任何地方使用特殊字符（如`$`或`\`作为常规字符），请在其前面加上反斜杠：（`\`所谓的转义字符）。

```
{
   "productName": ${GlobalVariable.productName},
   "unit": "\\bottle\",
   "quantity": 50,
   "discount": ${ if (productName == "wine") { return 30 } else { return 0}}
   "note": "Currency unit of ${GlobalVariable.productName} is \$."

}
```

- 没有`\`:*注意： ${GlobalVariable.productName} 的货币单位是 $*。
- 附`\`：*注意：酒的货币单位是$*。

### 在运行时创建全局变量

这是[Sergii Tyshchenko](https://forum.katalon.com/t/how-to-pass-user-defined-parameters-from-command-line/8771/22?u=jass)提供的一种方法。

1. 在用于执行 Katalon Studio 的会话中定义环境变量（带有外部配置或属性文件的路径）。
2. 在 中`TestListener`，读取变量的值（文件的路径），加载该文件，然后覆盖项目设置或全局变量。使用以下元编程：

```
 @Keyword
 void addGlobalVariable(String name, def value) {
  GroovyShell shell1 = new GroovyShell()
  MetaClass mc = shell1.evaluate("internal.GlobalVariable").metaClass
  String getterName = "get" + name.capitalize()
  mc.'static'."$getterName" = { -> return value }
  mc.'static'."$name" = value
}
```

可以将 getter 和/或 setter 作为新方法添加到`GlobalVariable`类或添加新字段。然后在脚本中，您可以使用 `GlobalVariable.VarName`VarName 是您的新变量。

```
CustomKeywords.'helper.addGlobalVariable'('localURL', 'katalon.com')
println GlobalVariable.localURL
```

> 转到[原来的讨论](https://forum.katalon.com/t/how-to-define-global-variables-within-scripts-i-e-on-the-fly/)。

### 在运行时更新全局变量

要在运行时更改全局变量的值，请使用以下命令语法`-g_XXX`（[了解更多](https://docs.katalon.com/katalon-studio/docs/console-mode-execution.html#general-options)）。

也可以看看：

- [如何在执行期间更改电子邮件设置](https://docs.katalon.com/katalon-studio/docs/execution-settings.html#support-global-variables-in-email-settings)。



# 6、测试用例变量

您可以在 Katalon Studio 中运行测试用例变量来参数化您的测试用例或使用不同的输入调用该测试用例，而不是使用硬编码值运行测试用例。

在开始之前，让我们看一下带有硬编码值的测试用例示例：

```
String employee = 'John'
String department = 'Marketing'

println "${employee} - ${department}"
```

## 管理测试用例变量

以下语句将用作示例：

```
println "${employee} - ${department}"
```

在**测试用例编辑器的****变量**选项卡中：

1. 要使用网格视图添加变量，请切换到测试用例的**变量选项卡。**
2. 然后单击**添加**。一个新行被添加到变量列表中。
3. 输入变量。

*注意：记住完成后保存测试用例。*

![](Overview_Data-driven Testing.assets/img-011-48.png)

使用变量运行测试用例后的结果将与硬编码值相同：

![](Overview_Data-driven Testing.assets/img-011-49.png)

## 在脚本模式下查看和声明变量

切换到**变量（脚本模式）**选项卡，Katalon Studio 将显示一个 XML 格式的脚本编辑器。例如：

![](Overview_Data-driven Testing.assets/img-011-50.png)

## 使用变量调用测试用例

1. **在手动**视图中打开一个测试用例，然后单击**添加**并选择选项**调用测试用例**。
2. 将显示显示项目中所有现有测试用例的**测试用例浏览器对话框。**选择要调用的测试用例并单击**OK**。

在以下示例中，将调用“带变量的测试用例”。
![](Overview_Data-driven Testing.assets/img-011-51.png)

3. 将添加一个**调用测试用例**步骤，上面选择的测试用例作为其目标。

![](Overview_Data-driven Testing.assets/img-011-52.png)

![](Overview_Data-driven Testing.assets/img-011-53.png)

![](Overview_Data-driven Testing.assets/img-011-54.png)

运行测试用例后的结果如下图所示：

![](Overview_Data-driven Testing.assets/img-011-55.png)

### 以脚本模式调用测试用例

在**Script**选项卡中，callTestCase 方法允许用户调用另一个测试用例。请参考以下示例：

```
WebUI.callTestCase(findTestCase('Data-driven Testing/Test Case with variables'), [('employee') : 'John', ('department') : 'Marketing', ('position') : 'Manager'], FailureHandling.STOP_ON_FAILURE)
```



# 7、使用外部数据源运行测试用例

Katalon Studio 提供了使用外部数据源执行自动化测试的能力。

## 将 Excel 文件导入测试数据

请参阅[本文](https://docs.katalon.com/katalon-studio/docs/manage-test-data.html#create-an-excel-test-data)了解如何在 Katalon Studio 中创建新的 Excel 测试数据。所选 Excel 文件中的数据将填充到预览部分，如下例所示。

![img-011-56](Overview_Data-driven Testing.assets/img-011-56.png)

## 使用测试用例变量创建新的测试套件

打开一个测试套件，从命令工具栏中选择**添加。**Katalon Studio 中的所有测试用例都将显示在“**测试用例浏览器**”对话框中。选定的测试用例将被添加到测试用例列表中，如下例所示。

![img-011-57](Overview_Data-driven Testing.assets/img-011-57.png)

## 管理数据绑定

1. 在测试套件编辑器中，单击**Show Data Binding**以展开包含**Test Data**和**Variable Binding**表的**Data Binding**部分。

   ![img-011-58](Overview_Data-driven Testing.assets/img-011-58.png)

2. 在**测试数据**表中，选择**添加**> 选择要用于执行的数据 > 将所选测试数据相应地添加到列表中。

   ![img-011-59](Overview_Data-driven Testing.assets/img-011-59.png)

3. 在显示所选测试用例的所有变量的**数据绑定表中，选择所有行 > 选择****设置类型**> 选择**数据列**作为它们的类型。

   ![img-011-60](Overview_Data-driven Testing.assets/img-011-60.png)

4. 单击**设置测试数据**以决定列表中要用于执行的测试数据。

   ![img-011-61](Overview_Data-driven Testing.assets/img-011-61.png)

5. 单击**值**列中的每个单元格以指定所选数据文件中的数据字段。例如：

   ![img-011-62](Overview_Data-driven Testing.assets/img-011-62.png)

6. 完成上述所有步骤后，保存并运行您的测试套件以查看以下结果：

   ![](Overview_Data-driven Testing.assets/img-011-63.png)
   

> **小建议：**
>
> 使用 **Map All** 按钮，您可以将所选测试用例的公共变量快速映射到测试数据中的相应列。要自动将变量绑定到数据，测试数据中的变量和相应列应共享**相同的名称**。\
>
> **例如，当您单击Map All**时，所选测试用例的“用户名”和“密码”变量可以自动映射到测试数据的“用户名”和“密码”列。

