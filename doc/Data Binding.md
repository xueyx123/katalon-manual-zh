# 使用外部数据源运行测试用例

Katalon Studio 提供了使用外部数据源执行自动化测试的能力。

## 将 Excel 文件导入测试数据

请参阅[本文](https://docs.katalon.com/katalon-studio/docs/manage-test-data.html#create-an-excel-test-data)了解如何在 Katalon Studio 中创建新的 Excel 测试数据。所选 Excel 文件中的数据将填充到预览部分，如下例所示。

![img-011-56](Data Binding.assets/img-011-56.png)

## 使用测试用例变量创建新的测试套件

打开一个测试套件，从命令工具栏中选择**添加。**Katalon Studio 中的所有测试用例都将显示在“**测试用例浏览器**”对话框中。选定的测试用例将被添加到测试用例列表中，如下例所示。

![img-011-57](Data Binding.assets/img-011-57.png)

## 管理数据绑定

1. 在测试套件编辑器中，单击**Show Data Binding**以展开包含**Test Data**和**Variable Binding**表的**Data Binding**部分。

   ![img-011-58](Data Binding.assets/img-011-58.png)

2. 在**测试数据**表中，选择**添加**> 选择要用于执行的数据 > 将所选测试数据相应地添加到列表中。

   ![img-011-59](Data Binding.assets/img-011-59.png)

3. 在显示所选测试用例的所有变量的**数据绑定表中，选择所有行 > 选择****设置类型**> 选择**数据列**作为它们的类型。

   ![img-011-60](Data Binding.assets/img-011-60.png)

4. 单击**设置测试数据**以决定列表中要用于执行的测试数据。

   ![img-011-61](Data Binding.assets/img-011-61.png)

5. 单击**值**列中的每个单元格以指定所选数据文件中的数据字段。例如：

   ![img-011-62](Data Binding.assets/img-011-62.png)

6. 完成上述所有步骤后，保存并运行您的测试套件以查看以下结果：

   ![](Data Binding.assets/img-011-63.png)

> **小建议：**
>
> 使用 **Map All** 按钮，您可以将所选测试用例的公共变量快速映射到测试数据中的相应列。要自动将变量绑定到数据，测试数据中的变量和相应列应共享**相同的名称**。\
>
> **例如，当您单击Map All**时，所选测试用例的“用户名”和“密码”变量可以自动映射到测试数据的“用户名”和“密码”列。

