---
title: 如何：以编程方式在隐藏模式下使用 Word 对话框
description: 了解如何使用 Visual Studio 以编程方式在隐藏模式下使用 Microsoft Word 对话框。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 39a81ccec284541d93d3a5901211d8a46ea6b61a
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826182"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>如何：以编程方式在隐藏模式下使用 Word 对话框
  您可以通过调用 Microsoft Office Word 中的内置对话框而不向用户显示这些对话框，使用一个方法调用执行复杂的操作。 可以通过使用 <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> 对象的方法 <xref:Microsoft.Office.Interop.Word.Dialog> 而不调用方法来执行此操作 <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> 。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>示例
 下面的代码示例演示如何在隐藏模式下使用 " **页面设置** " 对话框来设置不带用户输入的多个页面设置属性。 这些示例使用 <xref:Microsoft.Office.Interop.Word.Dialog> 对象来配置自定义页面大小。 页面设置的特定设置，如上边距、下边距等，可用作对象的后期绑定属性 <xref:Microsoft.Office.Interop.Word.Dialog> 。 这些属性是在运行时由 Word 动态创建的。

 下面的示例演示了如何在 **选项 Strict** 处于关闭状态的项目和面向的 Visual c # 项目中执行此任务 Visual Basic [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 。 在这些项目中，可以在 Visual Basic 和 Visual c # 编译器中使用后期绑定功能。 若要使用此示例，请从 `ThisDocument` 项目的或 `ThisAddIn` 类中运行它。

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet123":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet123":::

 下面的示例演示如何在 **选项 Strict** 处于打开 Visual Basic 项目中执行此任务。 在这些项目中，您必须使用反射来访问后期绑定属性。 若要使用此示例，请从 `ThisDocument` 项目的或 `ThisAddIn` 类中运行它。

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet104":::

## <a name="see-also"></a>请参阅
- [如何：以编程方式使用 Word 中的内置对话框](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Word 对象模型概述](../vsto/word-object-model-overview.md)
- [Office 解决方案中的后期绑定](../vsto/late-binding-in-office-solutions.md)
- [反射 (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [反射 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
