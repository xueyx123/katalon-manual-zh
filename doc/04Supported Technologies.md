# 支持的技术

本文档为您提供有关支持的技术和集成的信息。有关支持的环境（包括浏览器和操作系统），请参阅[支持的环境](https://docs.katalon.com/katalon-studio/docs/supported-environments.html)。

### 支持的被测应用程序 (AUT)

(*)限制：Record 和 Spy 实用程序无法自动捕获嵌入式 Web 视图中的元素。

**网页界面**

- 支持所有前端框架：ReactJS、AngularJS、VueJS。

- 跨浏览器兼容性：Chrome、Firefox、Safari、Edge

**移动端**

- 安卓和iOS
- 本机应用程序
- 网络手机
- 混合的（*）

**接口**

- REST：[Swagger](https://docs.katalon.com/katalon-studio/docs/ //docs.katalon.com/katalon-studio/docs/import-rest-requests-from-swagger-20.html)、[OpenAPI 3.0](https://docs.katalon.com/katalon-studio/docs/import-openapi30.html)和[WADL](https://docs.katalon.com/katalon-studio/docs/import-wadl.html)
- SOAP (SOAP 1.1 & 1.2)
- Authentication: [Basic](https://docs.katalon.com/katalon-studio/docs/authorization-basic.html), [OAuth 1.0](https://docs.katalon.com/katalon-studio/docs/authorization-oauth1.html) &[ OAuth 2.0](https://docs.katalon.com/katalon-studio/docs/authorization-oauth2.html)

**windows**

- 通用 Windows 平台 (UWP)
- Windows 窗体 (WinForms)
- Windows 演示基础 (WPF)
- Windows 10 PC 上的经典 Windows (Win32) 应用程序

### 编程技巧和语言

| 低代码 | 丰富的实用程序集，无需编程经验即可生成和维护自动化脚本。 |
| ------ | -------------------------------------------------------- |
| groovy | v2.4.x+                                                  |
| java   | 从 Java 8 (Java 1.8) 开始                                |

### 测试方法

|                                                              | **内置数据库** | **版本**  | **Katalon Studio 版本** | **Katalon Studio 企业版** |
| ------------------------------------------------------------ | -------------- | --------- | ----------------------- | ------------------------- |
| [数据驱动测试 - DDT](https://docs.katalon.com/katalon-studio/docs/ddt.html) | PostgreSQL     | v42.2.17  | v7.0.0+                 | v7.0.0+                   |
| [数据驱动测试 - DDT](https://docs.katalon.com/katalon-studio/docs/ddt.html) | 甲骨文 SQL     | v12.1.0.2 | 不支持                  | v7.0.0+                   |
| [数据驱动测试 - DDT](https://docs.katalon.com/katalon-studio/docs/ddt.html) | SQL 服务器     | v6.2.2    | 不支持                  | v7.0.0+                   |
| [行为驱动开发 - BDD](https://docs.katalon.com/katalon-studio/docs/cucumber-features-file.html) |                |           | v7.0.0+                 | v7.0.0+                   |
| 关键字驱动测试 - KDT                                         |                |           | v7.0.0+                 | v7.0.0+                   |
| 页面对象模型 - POM                                           |                |           | v7.0.0+                 | v7.0.0+                   |

### 测试能力

| **测试能力**                                                 | **支持的 Katalon Studio 版本** |
| ------------------------------------------------------------ | ------------------------------ |
| 集成测试                                                     | v7.8.0+                        |
| 功能测试                                                     | v7.8.0+                        |
| 端到端（E2E）测试                                            | v7.8.0+                        |
| [视觉测试](https://github.com/katalon-studio-samples/web-visual-testing-samples) | v7.8.0+                        |

### 特有的能力

| 特有的能力             | 描述                                                         | 支持的 Katalon Studio 版本 |
| --------------------------- | :----------------------------------------------------------- | :------------------------- |
| 被测应用 (AUT) 测试组合 | Katalon Studio 允许在一个项目和执行流程中组合多种应用程序类型（Web UI、API、移动和桌面）。 您可以[在此处](https://github.com/katalon-studio-samples/api-web-combination-sample/tree/master)使用我们的 Github 示例项目测试此功能。 | v7.0.0+                    |
| 双编辑界面              | Katalon Studio 测试脚本可以在两个界面之间互换：手动和脚本编辑器。 这使水平良莠不齐的自动化测试技能的团队能够在同一个项目中有效且高效地工作。 | v7.0.0+                    |
| 自我修复                | 自愈机制用于解决执行过程中定位器损坏的问题，以减少测试维护工作。 [了解更多](https://docs.katalon.com/katalon-studio/docs/self-healing.html)。 | v7.6.0+                    |
| 智能等待                | 智能等待功能令 WebDriver 在执行任何操作之前等待网页变为静态。 这可以令页面未完全加载时导致测试失败的风险降低。[了解更多](https://docs.katalon.com/katalon-studio/docs/webui-smartwait.html#sample-tests)。 | v7.0.0+                    |
| 时间胶囊                | 用户能够利用此功能将被测应用程序恢复到测试失败之前的状态，例如，定位器没有找到预期的 Web UI 对象时可用。[了解更多](https://docs.katalon.com/katalon-studio/docs/time-capsule.html)。 | v7.8.0+                    |

### 报告

| **报告类型**                                                 | **支持的 Katalon Studio 版本** |
| ------------------------------------------------------------ | ------------------------------ |
| [HTML、PDF、CSV](https://docs.katalon.com/katalon-studio/docs/test-suite-report.html#export-reports-to-other-formats) | v7.0.0+                        |
| [动态电子邮件配置](https://docs.katalon.com/katalon-studio/docs/execution-settings.html#emails-settings) | v7.5.0+                        |
| [基于发布/构建的报告](https://docs.katalon.com/katalon-studio/docs/record-screen-based-videos.html#configure-screen-based-recorder) | v7.8.0+                        |
| [绩效、趋势和洞察报告](https://docs.katalon.com/katalon-studio/docs/view-execution-list.html#prerequisites) (*) | v7.6.2+                        |

（*）前提/要求：Katalon TestOps 集成。

### 云设备集成

| **产品**                                                     | **支持的 Katalon Studio 版本** |
| ------------------------------------------------------------ | ------------------------------ |
| [Kobiton](https://docs.katalon.com/katalon-studio/docs/integrate_with_kobiton.html#enable-kobiton-integration) | v7.0.1+                        |
| [Sauce Labs](https://docs.katalon.com/katalon-studio/docs/saucelabs-plugin.html) | v7.0.0+                        |
| [Browserstack](https://docs.katalon.com/katalon-studio/docs/browserstack-integration.html) | v7.0.0+                        |
| [LambdaTest](https://docs.katalon.com/katalon-studio/docs/lambdatest-integration.html) | v7.8.0+                        |
| [Custom integration](https://docs.katalon.com/katalon-studio/docs/introduction-to-desired-capabilities.html#remote-server) | v7.0.0+                        |

### ALM 集成

| **产品**                                                     | **支持的 Katalon Studio 版本** |
| ------------------------------------------------------------ | ------------------------------ |
| [Jira](https://docs.katalon.com/katalon-studio/docs/jira-integration.html) | v7.0.0+                        |
| [Git](https://docs.katalon.com/katalon-studio/docs/git-integration.html) | v7.0.0+                        |
| [qTest](https://docs.katalon.com/katalon-studio/docs/qtest-integration.html) | v7.0.0+                        |
| [TestRail](https://docs.katalon.com/katalon-studio/docs/testrail-integration.html) | v7.6.5+                        |
| [Rally](https://docs.katalon.com/katalon-studio/docs/rally-integration.html) | v7.0.0+                        |
| [TestLink](https://docs.katalon.com/katalon-studio/docs/testlink-integration.html) | v7.0.0+                        |
| [Custom ALM integration](https://docs.katalon.com/katalon-store/docs/publisher/example-plugin-testrail.html) | v7.0.0+                        |

### CI/CD 集成

| **产品**                                                     | **版本**              | **支持的 Katalon Studio 版本** |
| ------------------------------------------------------------ | --------------------- | ------------------------------ |
| [Jenkins](https://docs.katalon.com/katalon-studio/docs/jenkins-integration-overview.html) |                       | v7.8.0+                        |
| [Azure DevOps Pipeline](https://docs.katalon.com/katalon-studio/docs/azure-devops-integration.html) |                       | v8.0.0+                        |
| [CircleCI](https://docs.katalon.com/katalon-studio/docs/integration-circleci.html#setup-and-configuration) |                       | v7.8.0+                        |
| [Bamboo](https://marketplace.atlassian.com/apps/1220235/katalon-testops-for-bamboo/version-history) | Bamboo Server v6.0.0+ | v7.8.0+                        |
| [TeamCity](https://plugins.jetbrains.com/plugin/12653-katalon-studio-runner/versions) |                       | v7.8.0+                        |
| [Katalon Studio Github Action](https://docs.katalon.com/katalon-studio/docs/katalon-studio-github-action.html) |                       | v7.8.0+                        |

### 与其他 Katalon 产品和扩展集成

| **产品**                                                     | **支持的 Katalon Studio 版本** |
| ------------------------------------------------------------ | ------------------------------ |
| [卡塔隆记录器](https://docs.katalon.com/katalon-recorder/docs/export-test-project-to-ks.html#export-to-katalon-studio) | v7.8.0+                        |
| [卡塔隆测试操作](https://docs.katalon.com/katalon-studio/docs/katalon-analytics-beta-integration.html#upload-test-results-automatically) | v7.0.0+                        |

### 从其他工具迁移

| **工具**                                                     | **支持的 Katalon Studio 版本** |
| ------------------------------------------------------------ | ------------------------------ |
| [Selenium](https://docs.katalon.com/katalon-studio/docs/selenium-testng-junit-migration.html) | v7.4.0+                        |
| [Selenium IDE](https://docs.katalon.com/katalon-studio/docs/import-selenium-ide.html) | v7.5.10+                       |
| [Postman](https://docs.katalon.com/katalon-studio/docs/import-postman.html) | v7.8.0+                        |
| [SoapUI](https://docs.katalon.com/katalon-studio/docs/import-soapui.html) | v7.8.0+                        |

### 提供

|                                                    | **支持的 Katalon Studio 版本** |
| -------------------------------------------------- | ------------------------------ |
| 社区包（[比较](https://www.katalon.com/pricing/)） | v7.0.0+                        |
| 企业套餐                                           | v7.0.0+                        |

 

### 支持

|                                                  | **支持的 Katalon Studio 版本** |
| ------------------------------------------------ | ------------------------------ |
| [卡塔隆论坛](https://forum.katalon.com/)         | v7.0.0+                        |
| [专属支持服务](https://www.katalon.com/pricing/) | v7.0.0+                        |