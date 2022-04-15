# Version 8.2.0
## 新功能
* 【Web服务】引入 `setHarFileGeneration(boolean enable)`和`getHarFileGeneration Web`服务关键字禁用按需生成HAR文件。参见
[[WS] Set HAR File Generation](https://docs.katalon.com/katalon-studio/docs/ws-set-har-file-generation.html "")和
[[WS] Get HAR File Generation](https://docs.katalon.com/katalon-studio/docs/ws-get-har-file-generation.html "")。

## 加强功能
* 增加了Chrome 95的兼容性。
* 增加了微软Edge(Chromium)95的兼容性。
* 【安全】解决开源软件的安全漏洞。
* 在Katalon Studio Preferences中增加了一个选项，自动禁用连接到外部域。
* 改进了Katalon Studio IDE和Katalon Runtime Engine的性能：
    * 在Katalon Studio中引入了延迟实例选项和Katalon Runtime Engine的-delayBetweenInstances参数用以并行模式执行测试套件集合。
    参见[命令语法](https://docs.katalon.com/katalon-studio/docs/console-mode-execution.html "")，快速提示:搜索-delay。
    * 在Katalon Runtime Engine中改进了加载时间。我们的基准测试结果显示:大型项目的速度要快2倍，中小型项目的速度要快1.5倍。
    * 在Katalon Studio中提高了大项目的响应能力和加载时间。我们的基准测试的结果显示:重命名/打开测试用例的速度快了2倍，移动测试用例的速度快了1.5倍。
    * 打开/执行测试时，Katalon Studio平均减少了12%的内存消耗。
    * 长时间执行会话的 Katalon 运行时引擎平均减少 30% 的内存消耗。
* \[Web测试]改进了Web测试的同步处理:
    * \[Katalon Studio和Katalon Runtime Engine]改进了点击和**偏移点击**关键字自动延迟和再次点击一个元素后面的加载覆盖。请参见
    [Click](https://docs.katalon.com/katalon-studio/docs/webui-click.html "")和[Click OffSet](https://docs.katalon.com/katalon-studio/docs/webui-click-offset.html "")。
    * \[智能等待]增加了检测和等待功能，以完成基于读取的请求，然后继续下一个动作。
    * \[智能等待]为智能等待增加了Edge Chromium的兼容性。请参见[[WebUI]智能等待功能](https://docs.katalon.com/katalon-studio/docs/webui-smartwait.html "")。
* \[Katalon Studio Enterprise]引入空闲超时绕过限制，自动注销许可用户超时。请参见[配置空闲超时时间](https://docs.katalon.com/katalon-studio/docs/license-idle-timeout.html "")。
* \[BDD]增加BDD(行为驱动开发)测试引导流程。
* \[Jira 集成]在最终测试结果中只显示Bug图标。
* \[控制台日志]Katalon Studio Enterprise和Katalon Runtime Engine控制台日志加载插件增强。
* [Katalon运行时引擎]在执行日志中删除了“离线激活失败”的消息。
* [DDT]数据驱动测试报告中迭代输入数据。

# 修复缺陷
* 缺陷:\[CSV报告]在CSV报告中跳过测试套件的状态不正确。
* 缺陷:无法识别SOAP信封体中的名称空间。
* 缺陷:\[BDD]调用自定义关键字时第二次运行失败的特性文件。
* 缺陷:当取消激活当前帐户并激活一个新帐户时，在报表查看器中返回null Katalon版本。
* 缺陷:日志报告查看器中的测试用例信息不正确。
* 缺陷:在Katalon Studio中执行时间和生成的报告之间不匹配。
* 缺陷:\[Jira整合]无法与嵌入的Jira页面交互。修正了Jira集成版本1.0.22的变化。下载:Jira Integration。
* 缺陷:\[Jira整合]Jira链接的票在描述中没有步骤。
* 缺陷:\[WebUI]当使用replace, trim, split功能和打开web Recorder时，无法生成测试步骤。
* 缺陷:在macOS上的Katalon Studio和Katalon Runtime Engine的版权和版本信息不正确。
