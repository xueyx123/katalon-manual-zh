# [移动] iOS 设置

本文将向您展示如何设置 Xcode 模拟器和真实的 iOS 设备，以此来使用 Katalon Studio 测试 iOS 应用程序。

首先，您需要设置 macOS 环境。您无法在 Windows 和 Linux 中执行 iOS 移动测试。

## 第 1 部分：设置 iOS 测试环境

1. 安装 Xcode 10.2 或更高版本。您可以从 App Store 或 Apple 开发者网站下载 Xcode：[Xcode 13](https://developer.apple.com/xcode/)。

   > 笔记：
   >
   > - Xcode 必须支持您的 iOS 设备的当前版本。
   > - Katalon Studio 只能支持 iOS 9.0 或更高版本。要了解更多关于 Katalon Studio 中支持的环境，您可以参考此文档：[支持的环境](https://docs.katalon.com/katalon-studio/docs/supported-environments.html#mobile)。

2. 安装 Xcode 的命令行工具。您可以从 Apple Developer 网站下载与您的 Xcode 版本兼容的命令行工具：[下载入口](https://developer.apple.com/download/all/)。

   **或者，您可以在终端**中按此顺序复制并粘贴以下命令行参数，以安装 Xcode 的命令行工具：

   `xcode-select --install`

   `sudo xcode-select -s /Applications/Xcode.app/Contents/Developer`

3. 安装 Appium 1.12.1 或更新版本。您可以通过 NPM 或下载 Appium Desktop 来安装 Appium。按照此处 Appium 文档中的说明进行操作：[入门](http://appium.io/docs/en/about-appium/getting-started/#installing-appium)。

   > 笔记：
   >
   > - 我们建议安装最新的 Appium 版本。
   > - 如果您通过 NPM 安装 Appium，请确保将 Node.js 安装到您拥有完整读/写权限的位置。
   > - 如果您使用的是 Xcode 模拟器以外的模拟器，一些模拟器会安装 Appium。如果您想在模拟器上运行应用程序，请在安装 Appium 之前检查您的模拟器设置。

## 第 2 部分：安装额外的依赖项以测试真实的 iOS 设备

> 如果您仅在 Xcode 模拟器上执行移动测试，请跳过此部分。

1. 安装Homebrew。Homebrew 是一个包管理器，可以轻松安装额外的依赖项。要安装 Homebrew，请按照 Homebrew 网站上的说明进行操作：[Homebrew](https://brew.sh/)。

2. 安装 Homebrew 后，您现在可以使用它在**终端**中安装以下依赖项：

   - ios-deploy 版本 1.9.4 或更高版本。你可以在这个 Github 项目中了解更多关于 ios-deploy 的信息：[ios-deploy](https://github.com/ios-control/ios-deploy)。要通过 Homebrew 安装 ios-deploy，请复制并粘贴命令行参数，如下所示：

     `brew install ios-deploy`

   - usbmuxd 版本 1.0.10 或更高版本。你可以在这个 Github 项目中了解更多关于 usbmuxd 的信息：[usbmuxd](https://github.com/libimobiledevice/usbmuxd)。要通过 Homebrew 安装 usbmuxd，请按此顺序复制并粘贴以下命令行参数：

     `brew install --HEAD usbmuxd`

     `brew unlink usbmuxd`

     `brew link usbmuxd`

   - libimobiledevice 版本 1.2.0 或更高版本。您可以在 libimobiledevice 网站上了解有关 libimobiledevice 的更多信息：[libimobiledevice](https://libimobiledevice.org/)。要通过 Homebrew 安装 libimobiledevice，请按此顺序复制并粘贴以下命令行参数：

     `brew install --HEAD libimobiledevice`

     `brew unlink libimobiledevice`

     `brew link libimobiledevice`

   - 对于早于 1.20.0 的 Appium 版本，您需要安装 Carthage。您可以在这个 Github 项目中了解有关 Carthage 的更多信息：[Carthage](https://github.com/Carthage/Carthage)。要通过 Homebrew 安装 Carthage，请复制并粘贴以下命令行参数：

     `brew install carthage`

   - 对于早于 1.15.0 的 Appium 版本，还需要安装 ios-webkit-debug-proxy。你可以在这个 Github 项目中了解更多关于 ios-webkit-debug-proxy 的信息：[ios-webkit-debug-proxy](https://github.com/google/ios-webkit-debug-proxy)。要通过 Homebrew 安装 ios-webkit-debug-proxy，请复制并粘贴命令行参数，如下所示：

     `brew install ios-webkit-debug-proxy`

## 第 3 部分：设置 iOS 设备/Xcode 模拟器以在 Katalon Studio 中进行移动测试

- 对于 Xcode 模拟器

安装 Xcode 后，Katalon 会自动将 Xcode 模拟器识别为 iOS 设备。要检查 Katalon 是否成功识别 Xcode 模拟器，请在主工具栏上的**Run**旁边的下拉列表中选择**iOS**设备。

您应该会看到显示为 iOS 设备的预安装 Xcode 模拟器列表。您现在可以继续去[第 4 部分：安装 WebDriverAgent](https://docs.katalon.com/katalon-studio/tutorials/mobile-ios-setup.html#part-4-install-the-webdriveragent)。

- 对于真正的 iOS 设备

1. 任何使用 Xcode 进行开发的设备都必须列在 Apple 开发者门户中。要了解如何在 Apple Developer Portal 中列出您的设备，您可以参考此处的 wikiHow 文档：[如何将新设备添加到您的 Apple Developer Portal](https://www.wikihow.com/Add-a-New-Device-to-Your-Apple-Developer-Portal)。
2. 在**Xcode > Preferences > Account**中，单击*Add* (+) 以输入您的 Mobile Developer Apple ID 和密码。
3. 通过 USB 数据线将您的 iOS 设备连接到您的计算机。确认接受或信任电话。
4. 要在设备上启用**UI 自动化**，请导航至**Settings > Developer**。在**UI Automation**部分，打开**Enable UI Automation**的设置。
5. 如果您想在 iOS（移动浏览器）上使用 Safari 执行测试，您需要在**Settings > Safari > Advanced**中启用以下设置：
   - JavaScript
   - 网络检查员
   - 远程自动化
## 第 4 部分：安装 WebDriverAgent

WebDriverAgent 是一个 WebDriver 服务器，用于远程控制 iOS 设备。要安装 WebDriverAgent，您可以参考此文档：[为 iOS 设备安装 WebDriverAgent](https://docs.katalon.com/katalon-studio/docs/installing-webdriveragent-for-ios-devices.html#setting-up-the-ios-device)。

## 第 5 部分：准备 iOS 应用程序文件

- 对于 Xcode 模拟器

要使用 Xcode 模拟器执行移动测试，您需要准备一个`.app`文件。要从 Xcode 项目中获取`.app`文件，请转到`~/Library/Developer/Xcode/DerivedData/{app name}/Build/Products/{scheme}-iphonesimulator/{app name}.app`.

   > 笔记：
   >
   > 要快速搜索`DerivedData`文件夹，请将以下路径复制并粘贴`~/Library/Developer/Xcode/DerivedData`到**Spotlight**中。

例如：要从**Coffee Timer**`app`项目中查找文件，请转到.`~/Library/Developer/Xcode/DerivedData/Coffee Timer/Build/Products/Debug-iphonesimulator/Coffee Timer.app`

- 对于真实的iOS设备

要使用真实的 iOS 设备执行移动测试，您需要：

1. 准备`.ipa`文件。按着这些次序：

   - 使用 Xcode 打开项目文件。例如，打开`Coffee Timer.xcodeproj`：

   从您存储项目的位置 > **App** > **Your-First-iOS-App** > **Coffee Timer**。双击该`Coffee Timer.xcodeproj`文件。

   - 在 Xcode 中打开项目后，选择一个 iOS 设备来启动应用程序。
   - 在**General**选项卡中，设置部署 iOS 版本并在**Deployment Info**部分选择设备类型。
   - 切换到**签名和功能**选项卡，选中**自动管理签名**框，然后选择之前添加的团队。
   - 要构建`.ipa`文件，请单击**产品 > 构建**。
   - 要导出`.ipa`文件，请单击**产品 > 存档**。按照说明获取`Coffee Timer.ipa`文件。

2. 验证`.ipa`文件，请按照下列步骤操作：

   - 在 Xcode 中导航到 **窗口 > 设备。**

   - 从**设备**列表中选择您的设备。

   - 单击*添加*(+) 以浏览`.ipa`文件。

     

   - 成功安装后，应用程序将出现在已**安装的应用程序**部分。

完成上述步骤后，您现在可以使用 Xcode 模拟器/真实 iOS 设备执行移动测试。要了解有关在 Katalon 中创建和执行 iOS 移动测试的更多信息，您可以参考此文档：[创建您的第一个 iOS 测试用例](https://docs.katalon.com/katalon-studio/tutorials/mobile-create-ios-test-case.html)。

## 也可以看看：

- [对自动化移动测试进行故障排除](https://docs.katalon.com/katalon-studio/docs/troubleshooting-automated-mobile-testing.html)
- 通过我们的 Katalon Academy 课程了解更多信息：[使用无代码解决方案解决移动测试挑战](https://academy.katalon.com/courses/codeless-solution-mobile-testing/?utm_source=kat_docs&utm_medium=ios_setup)
