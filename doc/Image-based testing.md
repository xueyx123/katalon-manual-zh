# 基于图像的Web自动化测试
> 要求：

1. Katalon Studio的版本大于7.2.2
2. 激活状态的Katalon Studio企业版

Katalon Studio提供了一个图像定位器方法来将测试对象与图像关联起来。使用此方法，您可以在测试下的web应用程序(AUT)的元素保持其外观时执行基于图像的测试，即使底层结构已经更改。

本指南向您展示如何配置基于映像的对象识别、捕获屏幕截图，以及减少基于映像的测试失败的机会。

## 启用图像识别
**从7.6版本开始**

默认情况下，在“Project ->Setting ->Self-Healing ->Web UI ->Test Execution”中启用了基于图像的对象识别。
![avatar](../imgs/xj/img-031-01.png)

**7.6之前的版本**

默认情况下，在项目设置中禁用基于图像的对象识别。转到Project ->Setting ->Execution，并选中“启用图像识别”，以启用此回退策略。
![avatar](../imgs/xj/img-031-02.png)

## 捕捉识别对象的截图
### 使用内置工具

为了生成与捕获的测试对象相关的图像，Katalon Studio在Web Recorder和Spy实用程序中都包含了添加截图按钮。

这里我们使用间谍网络工具来捕捉屏幕截图。遵循以下步骤:
1. 从主工具栏选择 Spy Web,打开Spy Web Utility
![avatar](../imgs/xj/img-031-03.png)
