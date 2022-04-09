- # [移动] Android 设置

  本文将向您展示如何设置真正的 Android 设备以使用 Katalon Studio 测试 Android 应用程序。

  > 如果你想用 Android Studio (Emulator) 进行 Android 移动端测试，可以参考这篇文档：[[移动端\] 配置 Android Studio (模拟器)](https://docs.katalon.com/katalon-studio/docs/configure-android-studio.html#configure-android-studio)。

  ## 在 Windows、Linux 和 macOS 上设置 Android 测试

  ### 在 Windows 机器上

  1. 支持的环境

  - Appium：1.12.1 起。
  - Android：6.x 以上（官方版本）。

  1. 安装 Appium。安装可以参考这里的 Appium 文档：[入门](http://appium.io/docs/en/about-appium/getting-started/#installing-appium)。

     > 笔记：
     >
     > 确保将 Node.js 安装到您拥有完整读/写权限的位置。

  2. 设置设备

  - 打开手机的开发者模式。转到**设置**>**开发人员选项**，启用：
    - USB 调试 – 连接 USB 时的调试模式。
    - 通过 USB 安装 - 允许通过 USB 安装应用程序。
    - USB 调试（安全设置）——允许通过 USB 调试授予权限和模拟输入。
  - 通过 USB 数据线将您的 Android 手机连接到计算机。
  - 确认接受或信任该设备。

  1. 安装安卓 SDK

     如果您当前的机器没有安装**Android SDK**，Katalon Studio 会自动检测并要求您安装。

  ### 在 macOS 机器上

  1. 支持的环境

  - Appium：1.12.1 起。

  - 安卓：6.x 以上。

    > 笔记：
    >
    > 一些模拟器在安装时直接支持 Appium。如果您想在模拟器上运行应用程序，请在继续安装 Appium 之前检查您的模拟器设置。

  1. 安装 Appium。安装可以参考这里的 Appium 文档：[入门](http://appium.io/docs/en/about-appium/getting-started/#installing-appium)。

  ```shell
  brew install node` `npm install -g appium
  ```

     > 笔记：
     >
     > 确保将 Node.js 安装到您拥有完整读/写权限的位置。

  2. 设置设备

  - 在您的 Android 设备上打开开发者模式。转到**设置**>**开发人员选项**。
  - 通过 USB 数据线将您的 Android 手机连接到计算机。只需确认是否提示接受或信任该设备。

  1. 安装安卓 SDK

     如果您当前的机器没有安装**Android SDK**，Katalon Studio 会自动检测并要求您安装。

  ### 在 Linux 机器上

  1. 支持的环境

  - Appium：1.12.1 起。

  - 安卓：6.x 以上。

    > 笔记：
    >
    > 一些模拟器在安装时直接支持 Appium。如果您想在模拟器上运行应用程序，请在继续安装 Appium 之前检查您的模拟器设置。

  1. 通过在终端中输入以下内容来安装 Appium：

     ```shell
     npm install -g appium
     ```

     - 如果您在 Appium 安装命令中看到 EACCES 错误，请按照此处的 npm 文档说明进行操作：[解决全局安装时的 EACCES 权限错误](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally) 。
     - 如果遇到`jar`找不到 Java 文件的错误，您可能需要添加环境变量：`KATALON_JAVA_HOME= <JRE_location>`. 请参阅 Ask Ubuntu：[如何为 Java 设置 JAVA_HOME？](https://askubuntu.com/questions/175514/how-to-set-java-home-for-java?utm_medim=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)
     - **在Katalon Studio Preferences**中手动设置 Appium 目录。默认目录应该是 `/usr/lib/node_modules/appium/`.

     > 笔记：
     >
     > 确保将 Node.js 安装到您拥有完整读/写权限的位置。请参阅 Node.js 文档：[适用于 Linux 的](https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions)Node.js。

  2. 设置设备

  - 在您的 Android 设备上打开开发者模式。转到**设置**>**开发人员选项**。
  - 通过 USB 数据线将您的 Android 设备连接到计算机。只需确认是否提示接受或信任该设备。

  1. 安装 Android SDK（可选）

     如果您当前的机器没有安装**Android SDK**，Katalon Studio 会自动检测并要求您安装它。

  ## 验证成功的 Android 设备连接

  完成环境设置后，要检查 Katalon 是否成功识别您的 Android 设备，您可以在**文件 > 新示例项目 > 示例 Android 移动测试项目**中打开一个移动测试示例项目。

  ![avatar](D:\test\katalon-manual-zh\imgs\zs\img-014-01.png)

  在主工具栏上，在**Run**旁边的下拉列表中选择**Android**设备。

  ![avatar](D:\test\katalon-manual-zh\imgs\zs\img-014-02.png)

  您应该会在弹出对话框中看到您的 Android 设备的名称。

  ![avatar](D:\test\katalon-manual-zh\imgs\zs\img-014-03.png)

  **下一步：**

  - [创建您的第一个 Android 测试用例](https://docs.katalon.com/katalon-studio/tutorials/mobile-create-android-test-case.html)

  ## 也可以看看：

  - [对自动化移动测试进行故障排除](https://docs.katalon.com/katalon-studio/docs/troubleshooting-automated-mobile-testing.html)
  - 通过我们的 Katalon Academy 课程了解更多信息：[使用无代码解决方案解决移动测试挑战](https://academy.katalon.com/courses/codeless-solution-mobile-testing/?utm_source=kat_docs&utm_medium=android_setup)

  
