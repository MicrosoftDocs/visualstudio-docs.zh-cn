---
title: 定义和使用活动委托
description: 在工作流设计器中，了解 .NET Framework 4.5 如何包含 InvokeDelegate 活动的现成设计器，你可以使用该设计器来定义和使用活动委托。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 48cab69de11ce006792e0fda72245048c6897acf
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993271"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>如何：在工作流设计器中定义和使用活动委托

.NET Framework 4.5 包括活动的现成设计器 <xref:System.Activities.Statements.InvokeDelegate> 。 此设计器可用于将委托分配给从 <xref:System.Activities.ActivityDelegate> 派生的活动，例如 <xref:System.Activities.ActivityAction> 或 <xref:System.Activities.ActivityFunc%601>。

## <a name="define-an-activity-delegate"></a>定义活动委托

1. 创建新的 **工作流控制台应用程序** 项目。

   > [!NOTE]
   > 如果看不到 **工作流** 项目模板，请先安装 **Windows Workflow Foundation** Visual Studio 组件。 有关详细说明，请参阅 [安装 Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)。

3. 在 **解决方案资源管理器** 中右键单击该项目，然后选择 "**添加**  >  **新项**"。 选择 " **工作流** " 类别，然后选择 " **活动** 项" 模板。 将新活动命名为 **MyForEach** ，然后选择 **"确定"**。

   该活动在工作流设计器中打开。

4. 在工作流设计器中，单击 " **参数** " 选项卡。

5. 单击 **“创建参数”**。 将新参数命名为 **Items**。

6. 在 " **参数类型** " 列中，选择 " **[T] 的数组**"。

7. 在类型浏览器中，选择 " **对象** "，然后选择 **"确定"**。

8. 再次单击 " **创建参数** "。 命名新的参数 **体**。 在新参数的 " **方向** " 列中，选择 " **属性**"。

9. 在 "参数类型" 列中，选择 "**浏览类型**"

10. 在类型浏览器的 "**类型名称**" 字段中，输入 **ActivityAction** 。 在树视图中选择 " **ActivityAction \<T>** "。 在显示的下拉列表中选择 "**对象**"，将类型 **ActivityAction \<Object>** 分配给参数。

11. 将 <xref:System.Activities.Statements.While> 活动从 "工具箱" 的 " **控制流** " 部分拖到设计器图面。

12. 选择 <xref:System.Activities.Statements.While> 活动，然后选择 " **变量** " 选项卡。

13. 选择 " **创建变量**"。 命名新的变量 **索引**。

14. 在 " **变量类型** " 列中，选择 " **Int32**"。 将 **范围** 保持为 **While**，并将 **默认** 列留空。

15. 将活动的 **Condition** 属性设置 <xref:System.Activities.Statements.While> 为 **索引 < 项。 Length;**。

16. 将 <xref:System.Activities.Statements.InvokeDelegate> 活动从工具箱的 " **基元** " 部分拖到活动的 " **正文** " <xref:System.Activities.Statements.While> 。

17. 选择委托下拉的 " **正文** "。

18. 在活动的 "**属性**" 网格中 <xref:System.Activities.Statements.InvokeDelegate> ，在 "**委托参数**" 属性中单击 " **...** " 按钮。

19. 在 "参数命名 **参数**" 的 "**值**" 列中，输入 **Items [Index]**。 单击 **"确定"** 以关闭 " **DelegateArguments** " 对话框。

20. 将 <xref:System.Activities.Statements.Assign> 活动拖到 <xref:System.Activities.Statements.InvokeDelegate> 活动的水平线下。 <xref:System.Activities.Statements.Assign>创建活动后，将 <xref:System.Activities.Statements.Sequence> 自动创建一个活动，以包含 **MyForEach** 活动的 "**正文**" 部分中的两个活动。 需要序列，因为 **正文** 部分只能包含单个活动。 自动创建新 <xref:System.Activities.Statements.Sequence> 活动是 .NET Framework 4.5 的一项新功能。

21. 将活动的 " **到** " 属性设置为 " <xref:System.Activities.Statements.Assign> **索引**"。 将 " **Assign** " 活动的 "**值**" 属性设置为 "**索引 + 1**"。

    自定义 **MyForEach** 活动为通过 **Items** 集合传入的每个值调用一次任意活动，并将集合中的值用作活动的输入。

## <a name="use-the-custom-activity-in-a-workflow"></a>使用工作流中的自定义活动

1. 按 **Ctrl** + **Shift** + **B** 生成项目。

2. 在 **解决方案资源管理器** 中，在设计器中打开 **workflow1.xaml** 。

3. 将 **MyForEach** 活动从工具箱拖到设计器图面。 活动位于工具箱中与项目同名的部分中。

4. 将 **MyForEach** 活动的 **Items** 属性设置为 **new Object [] {1，"abc"}**。

5. 将 <xref:System.Activities.Statements.WriteLine> 活动从工具箱的 "**基元**" 部分拖到 " **MyForEach** " 活动的 "**委托：正文**" 部分。

6. 将活动的 " **Text** " 属性设置 <xref:System.Activities.Statements.WriteLine> 为 " **Argument ( # B1**"。

当执行工作流时，控制台将显示以下输出：

**1** 
**abc**
