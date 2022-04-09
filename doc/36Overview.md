# BDD 测试框架（Cucumber 集成）

## 添加功能文件

> 为了获得最佳性能，请经常清理 Katalon 工作区。导航到**文件**>**清理**。

功能文件位于项目文件夹中的**“包含/功能”**文件夹中，可以从*测试资源管理器*中看到：

![](../img/zs/img-036-01.png)

*功能*文件的内容遵循 BDD 约定（_Given、When、The_n）。创建新*功能*文件时，将有一个“**生成示例功能模板**”选项，它将为您的*功能*文件生成示例模板。这将确保创建的*功能*文件与 BDD 约定匹配，以便您减少以正确格式 创建*功能文件*的校核工作。

![](../img/zs/img-036-02.png)

考察一个卡塔隆演示 Cura 系统 ( [http://demoaut.katalon.com ](http://demoaut.katalon.com) ).的示例。我们想使用有效和无效的凭据测试*登录*功能，因此内容将如下所示：

> 标签是组织功能和场景的好方法。[阅读更多...](https://docs.cucumber.io/cucumber/api/#tags)

![](../img/zs/img-036-03.png)

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

> Katalon Studio 代码检查将检测并突出显示*功能文件*中任何缺失的*步骤定义*，以帮助用户创建所需的步骤定义。

当前*功能*文件会遇到以下的维护问题之一：

- 当前格式组织得不正确。
- 找出与当前“*Gherkin“*步骤映射的 *“步骤定义”*。
- *当步骤定义*发生变化时，重新计算*特征*文件中的步骤。

以上困境已直接从功能文件编辑器的上下文菜单中处理掉了。

![](../img/zs/img-036-04.png)

**完美的格式**

重新做格式。

**查找步骤**

在现有步骤定义文件中查找当前 Gherkin 步骤的相关步骤。

**重新计算步骤**

当步骤定义发生变化时，重新计算特征文件中的步骤。

## 定义步骤

### 如何定义步骤

*Features*文件中的每个 Gherkin 步骤都需要定义为一组编程代码，以便机器可以执行这些步骤的动作。

这些*步骤定义*可以通过利用**脚本模式**在*关键字*文件夹中实现。

Katalon Studio 内置关键字也可以在步骤定义文件中重复使用。

不论 Katalon Studio 执行测试用例中的哪个*功能*文件时，它都会在源文件夹中查找匹配的步骤定义。

> 步骤定义可以用任何 Cucumber 支持的编程语言编写，包括 Groovy 和 Java。

例如，让我们从上面的*Features* File 中获取 Gherkin 场景并定义步骤：

![](../img/zs/img-036-05.png)

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

您可以使用`CucumberKW.GLUE = ['package1', 'package2']`为 Cucumber 定义“步骤定义”的位置。

`CucumberKW.GLUE = ['']`的默认值是所有包，这意味着测试引擎需要时间来扫描所有包。

定义特定位置可以缩小包的范围，以便在执行功能文件之前找到步骤定义；因此，减少了执行时间。

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

Katalon Studio 允许您随时自行运行功能文件，以确保其正常工作。

打开所需的**功能**文件，单击主工具栏上的 **播放** 按钮。

![](../img/zs/img-036-06.png)

### 在测试用例中

Katalon Studio 支持 Cucumber 关键字以及原始内置关键字。用户不必将 Cucumber 库导入 Katalon Studio。

在 Katalon Studio 测试用例中包含 Cucumber *Feature文件：*

**执行单个功能文件（带或不带标签）**

- [运行特征文件](https://docs.katalon.com/katalon-studio/docs/cucumber-kw-run-feature-file.html)
- [运行带标签的特征文件](https://docs.katalon.com/katalon-studio/docs/cucumber-kw-run-feature-file-tag.html)

**执行多个功能文件（带或不带标签）**

- [运行功能文件夹](https://docs.katalon.com/katalon-studio/docs/cucumber-kw-run-feature-folder.html)
- [运行带标签的功能文件夹](https://docs.katalon.com/katalon-studio/docs/cucumber-kw-run-feature-folder-tag.html)

**使用[Cucumber 运行器执行](http://toolsqa.com/cucumber/junit-test-runner-class/)**

- [运行Cucumber 运行器](https://docs.katalon.com/katalon-studio/docs/cucumber-kw-run-cucumber-runner.html)

## Cucumber 报告

### 在 Katalon TestOps中

Katalon TestOps 专门支持查看 BDD 测试结果以及高级分析和报告，例如 可追溯性矩阵报告。要了解溯源矩阵报告，可以参考本文档：[溯源矩阵报告](https://docs.katalon.com/katalon-analytics/docs/view-traceability-matrix.html)。

默认情况下，Katalon TestOps 上的 BDD 测试报告功能被禁用，以避免混合 BDD 和 Katalon Studio 格式的数据。要启用该功能，您可以参考本指南：[在 Katalon TestOps 中查看 BDD 测试结果](https://docs.katalon.com/katalon-analytics/docs/bdd-test-results.html)。

### 在Katalon Studio中

没有用于执行特征文件的自定义报告**。**Katalon Studio 仅使用 **测试套件/测试套件集合**执行**级别**生成的 Cucumber 报告，其中的测试用例包含 Cucumber Features 文件。

测试套件/测试套件集合 生成的 Cucumber 报告将位于 Katalon Studio 报告文件夹的同一文件夹中。在 Katalon Studio 测试资源管理器中，右键单击所需的 **报告> 打开已有的文件夹**。Katalon Studio 会将您重定向到存储 Cucumber 报告的本地文件夹。 

Katalon Studio 支持Cucumber 报告的**三种**格式：JSON、XML、HTML。

![](../img/zs/img-036-07.png)