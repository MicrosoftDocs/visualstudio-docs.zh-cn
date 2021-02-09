---
title: 演练：创建您的第一个 Word VSTO 外接程序
description: 创建用于 Microsoft Word 的应用程序级外接程序。 此功能可用于应用程序本身，无论打开的是哪个文档。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Word [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 43104ad8b26045056ca8d8d653fcb9625734f7eb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899434"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-word"></a>演练：创建您的第一个 Word VSTO 外接程序
  本介绍性演练说明如何创建 Microsoft Office Word 的 VSTO 外接程序。 你在此类解决方案中创建的功能可用于应用程序本身，而与所打开的文档无关。

 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

 本演练演示以下任务：

- 创建 Word VSTO 外接程序项目。

- 编写代码，使用 Word 的对象模型在保存文档时向文档中添加文本。

- 生成并运行项目，以对其进行测试。

- 清理已完成的项目，使 VSTO 外接程序在开发计算机上不再自动运行。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>先决条件
 您需要满足以下条件才能完成本演练：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>创建项目

### <a name="to-create-a-new-word-vsto-add-in-project-in-visual-studio"></a>在 Visual Studio 中创建新的 Word VSTO 外接程序项目

1. 启动 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。

2. 在 **“文件”** 菜单上，指向 **“新建”** ，再单击 **“项目”** 。

3. 在模板窗格中，展开 **“Visual C#”** 或 **“Visual Basic”**，然后展开 **“Office/SharePoint”**。

4. 在展开的 **“Office/SharePoint”** 节点下方，选择 **“Office 外接程序”** 节点。

5. 在项目模板列表中，选择 Word VSTO 外接程序项目。

6. 在 " **名称** " 框中，键入 **FirstWordAddIn**。

7. 单击“确定”。

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 创建 **FirstWordAddIn** 项目，并在编辑器中打开 ThisAddIn 代码文件。

## <a name="write-code-to-add-text-to-the-saved-document"></a>编写用于向保存的文档添加文本的代码
 接下来，将代码添加到 ThisAddIn 代码文件。 新的代码则使用 Word 的对象模型向每个已保存文档添加样本文本。 默认情况下，ThisAddIn 代码文件包含以下生成的代码：

- `ThisAddIn` 类的部分定义。 此类提供代码的入口点，并提供对 Word 对象模型的访问权限。 有关详细信息，请参阅 [PROGRAM VSTO 外接程序](../vsto/programming-vsto-add-ins.md)。类的其余部分 `ThisAddIn` 是在不应修改的隐藏代码文件中定义的。

- `ThisAddIn_Startup` 和 `ThisAddIn_Shutdown` 事件处理程序。 Word 加载和卸载 VSTO 外接程序时会调用这些事件处理程序。 使用这些事件处理程序，可在加载 VSTO 外接程序对其进行初始化，并在卸载 VSTO 外接程序时清理其使用的资源。 有关详细信息，请参阅 [Office 项目中的事件](../vsto/events-in-office-projects.md)。

### <a name="to-add-a-paragraph-of-text-to-the-saved-document"></a>向已保存的文档添加文本段落

1. 在 ThisAddIn 代码文件中，将下面的代码添加到 `ThisAddIn` 类中。 新的代码定义 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> 事件的事件处理程序，该事件在保存文档时引发。

    用户保存文档时，该事件处理程序会将新文本添加到文档的开头。

    [!code-vb[Trin_WordAddInTutorial#1](../vsto/codesnippet/VisualBasic/FirstWordAddIn/ThisAddIn.vb#1)]
    [!code-csharp[Trin_WordAddInTutorial#1](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#1)]

   > [!NOTE]
   > 此代码使用索引值为 1 来访问 <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A> 集合中的第一个段落。 尽管 Visual Basic 和 Visual C# 使用从 0 开始的数组，但 Word 对象模型中大多数集合的数组下限都是 1。 有关详细信息，请参阅 [在 Office 解决方案中编写代码](../vsto/writing-code-in-office-solutions.md)。

2. 如果你使用的是 C#，请将以下必需代码添加到 `ThisAddIn_Startup` 事件处理程序中。 此代码用于将 `Application_DocumentBeforeSave` 事件处理程序与 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> 事件连接在一起。

    [!code-csharp[Trin_WordAddInTutorial#2](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#2)]

   为了在保存文档后对其进行修改，前面的代码示例使用以下对象：

- `Application` 类的 `ThisAddIn` 字段。 `Application` 字段返回一个 <xref:Microsoft.Office.Interop.Word.Application> 对象，该对象表示 Word 的当前实例。

- `Doc` 事件的事件处理程序的 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> 参数。 `Doc` 参数是一个 <xref:Microsoft.Office.Interop.Word.Document> 对象，用于表示已保存的文档。 有关详细信息，请参阅 [Word 对象模型概述](../vsto/word-object-model-overview.md)。

## <a name="test-the-project"></a>测试项目

### <a name="to-test-the-project"></a>测试项目

1. 按 **F5** 生成并运行项目。

     生成项目时，代码会编译成一个程序集，此程序集包含在项目的生成输出文件夹中。 Visual Studio 还会创建一组注册表项，通过这些注册表项，Word 能够发现和加载 VSTO 外接程序，Visual Studio 还将开发计算机上的安全设置配置为允许 VSTO 外接程序运行。 有关详细信息，请参阅 [生成 Office 解决方案](../vsto/building-office-solutions.md)。

2. 在 Word 中，保存活动文档。

3. 验证下面的文本是否已添加到文档中。

     **This text was added by using code.**

4. 关闭 Word。

## <a name="clean-up-the-project"></a>清理项目
 完成项目开发后，请从开发计算机上删除 VSTO 外接程序程序集、注册表项和安全设置。 否则，每次在开发计算机上打开 Word 时，VSTO 外接程序都将继续运行。

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>在开发计算机上清理已完成的项目

1. 在 Visual Studio 中，在 **“生成”** 菜单上，单击 **“清理解决方案”**。

## <a name="next-steps"></a>后续步骤
 既然你已经创建了一个基本的 Word VSTO 外接程序，就可以从下面这些主题中了解有关如何开发 VSTO 外接程序的详细信息：

- 可在 VSTO 外接程序中执行的常规编程任务： [PROGRAM VSTO 外](../vsto/programming-vsto-add-ins.md)接程序。

- 特定于 Word VSTO 外接程序的编程任务： [word 解决方案](../vsto/word-solutions.md)。

- 使用 Word 的对象模型： [word 对象模型概述](../vsto/word-object-model-overview.md)。

- 自定义 Word 的 UI，例如通过向功能区添加自定义选项卡或创建自己的自定义任务窗格： [OFFICE UI 自定义](../vsto/office-ui-customization.md)。

- 生成和调试 Word 的 VSTO 外接程序： [生成 Office 解决方案](../vsto/building-office-solutions.md)。

- 部署 Word 的 VSTO 外接程序： [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)。

## <a name="see-also"></a>另请参阅
- [Office 解决方案开发概述 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Word 解决方案](../vsto/word-solutions.md)
- [程序 VSTO 外接程序](../vsto/programming-vsto-add-ins.md)
- [Word 对象模型概述](../vsto/word-object-model-overview.md)
- [Office UI 自定义](../vsto/office-ui-customization.md)
- [构建 Office 解决方案](../vsto/building-office-solutions.md)
- [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)
- [Office 项目模板概述](../vsto/office-project-templates-overview.md)
