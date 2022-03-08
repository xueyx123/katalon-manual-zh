# 管理测试数据

> 从 Katalon Studio 版本 6.3.0 开始，您可以配置变量绑定以读取测试数据值作为预期的数据类型。有关测试数据的变量绑定示例，请参阅[本文档](https://docs.katalon.com/katalon-studio/docs/bind-as-string.html)，其中选项绑定到测试用例作为启用/禁用字符串。

## 创建 Excel 测试数据

1.  从主菜单中选择 **文件 > 新建 > 测试数据。**将 显示**新建测试数据** 对话框。输入测试数据的名称并选择**Data Type** as **Excel File**。单击**确定**。
   ![](Manage and Assign Test Data.assets/img-012-001.png)

2. 浏览到要导入 Katalon Studio 的 Excel 文件。
   ![](Manage and Assign Test Data.assets/img-012-002.png)

3. 所选 Excel 文件中的数据将填充到下面的**预览部分**中。
   ![](Manage and Assign Test Data.assets/img-012-003.png)

4. 完成后保存测试数据。此处定义的数据集可用于其他配置。例如，您可以在设置测试套件时使用它来输入[手动视图](https://docs.katalon.com/display/KD/Manual+View)中的关键字数据或[测试执行数据。](https://docs.katalon.com/katalon-studio/docs/run-test-case-external-data.html#manage-data-binding)

   

## 创建 CSV 测试数据

1.  从主菜单中选择 **文件 > 新建 > 测试数据。**将 显示**新建测试数据** 对话框。输入测试数据的名称并选择 **Data Type** as **CSV File**。单击 **确定**。
   ![](Manage and Assign Test Data.assets/img-012-004.png)
2. 浏览到要导入 Katalon Studio 的 CSV 文件。
   ![](Manage and Assign Test Data.assets/img-012-005.png)
3. 所选 CSV 文件中的数据将填充到下面的**预览部分**。
   ![](Manage and Assign Test Data.assets/img-012-006.png)
4. 完成后保存测试数据。此处定义的数据集可用于其他配置。例如，您可以在设置测试套件时使用它来输入[手动视图](https://docs.katalon.com/display/KD/Manual+View)中的关键字数据或[测试执行数据。](https://docs.katalon.com/x/7AAM)

## 创建内部测试数据

使用 **内部数据**，您可以自由定义表格格式的数据。由您决定每个单元格的列数、行数和值。

1.  从主菜单中选择 **文件 > 新建 > 测试数据。**将 显示**新建测试数据** 对话框。输入测试数据的名称并选择 **Data Type** 作为**Internal Data**。单击 **确定**。
   ![](Manage and Assign Test Data.assets/img-012-007.png)
2. 在编辑器视图中，选择添加新列的选项。
   ![](Manage and Assign Test Data.assets/img-012-008.png)
3. 选择添加新行的选项。
   ![](Manage and Assign Test Data.assets/img-012-009.png)
4. 最后，单击每个单元格以输入它们的值。
   ![](Manage and Assign Test Data.assets/img-012-010.png)
5. 您可以通过右键单击访问上下文菜单来编辑或删除列（或行）。
   ![](Manage and Assign Test Data.assets/img-012-011.png)
6. 完成后保存测试数据。此处定义的数据集可用于其他配置。例如，您可以在设置测试套件时使用它来输入[手动视图](https://docs.katalon.com/display/KD/Manual+View)中的关键字数据或[测试执行数据。](https://docs.katalon.com/x/7AAM)

## 创建数据库数据

使用 **内部数据**，您可以自由定义表格格式的数据。由您决定每个单元格的列数、行数和值。

1.  从主菜单中选择 **文件 > 新建 > 测试数据。**将 显示**新建测试数据** 对话框。输入测试数据的名称并选择 **Database Data** 作为 **Data Type**。单击 **确定**
   ![](Manage and Assign Test Data.assets/img-012-012.png)

2. 单击**编辑查询**以打开**数据库连接和查询设置** 对话框。
   ![](Manage and Assign Test Data.assets/img-012-013.png)

3. 输入连接详细信息以及数据查询，然后单击**OK**。

   ![](Manage and Assign Test Data.assets/img-012-014.png)

   从**Katalon Studio 版本 7.0.0 及更高版本开始，您可以使用对话框中的****JDBC Driver**字段从其他数据库源查询数据。您可以输入具有库支持连接 (JDBC) 的数据库的 ClassDriverName。

   > 您可以选中**使用全局数据库连接设置**以使用项目设置中定义的连接。有关详细信息，请参阅[数据库设置](https://docs.katalon.com/display/KD/Database+Settings)。

4. 查询的数据被分别获取并加载到下面的**预览部分**。
   ![](Manage and Assign Test Data.assets/img-012-015.png)

5. 完成后保存测试数据。此处定义的数据集可用于其他配置。例如，您可以在设置测试套件时使用它来输入[手动视图](https://docs.katalon.com/display/KD/Manual+View)中的关键字数据或[测试执行数据。](https://docs.katalon.com/x/7AAM)

