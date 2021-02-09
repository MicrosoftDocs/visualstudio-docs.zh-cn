---
title: 如何：以编程方式隐藏文档中的文本
description: 了解如何在 Microsoft Word 文档中隐藏文本，方法是为特定范围的文本设置字体的隐藏属性。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e74a7a48effafefdc945b0e86dbec6d9692dabd7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885373"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>如何：以编程方式隐藏文档中的文本
  通过将 <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> 属性设置为某个特定范围文本的 <xref:Microsoft.Office.Interop.Word.Range.Font%2A> 。

 例如，可以在将文档 <xref:Microsoft.Office.Tools.Word.Bookmark> 发送到打印机之前，暂时隐藏文档级自定义项中的 (中的文本) 或 <xref:Microsoft.Office.Interop.Word.Bookmark> VSTO 外接程序) 中的 (。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>打印文档时在 Bookmark 控件中隐藏文本

1. 创建一个过程，它会隐藏特定范围内的所有文本。

     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]

2. 创建一个过程，它会取消隐藏特定范围内的所有文本。

     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]

3. 将书签的范围传递到 `HideText` 方法，打印文档，然后将相同范围传递到 `UnhideText` 方法。

     下面的代码示例可用于文档级自定义项。 若要使用此示例，请从项目的 `ThisDocument` 类中运行它。

     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]

     以下代码示例可用于 VSTO 外接程序。 本示例使用活动文档。 若要使用此示例，请从项目的 `ThisAddIn` 类中运行它。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]

## <a name="compile-the-code"></a>编译代码
 此代码示例假定文档包含 <xref:Microsoft.Office.Tools.Word.Bookmark> 文档级自定义项中的控件 () 或 <xref:Microsoft.Office.Interop.Word.Bookmark> 在名为的 VSTO 外接程序) 中的控件 (`bookmark1` 。

## <a name="see-also"></a>另请参阅
- [如何：以编程方式打印文档](../vsto/how-to-programmatically-print-documents.md)
- [如何：以编程方式在文档中定义和选择范围](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [如何：以编程方式重置 Word 文档中的范围](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [如何：以编程方式更新书签文本](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)
