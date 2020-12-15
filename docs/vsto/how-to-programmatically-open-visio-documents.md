---
title: 如何：以编程方式打开 Visio 文档
description: 了解如何使用 Open 或 Microsoft.office.interop.visio.documents.open 方法以编程方式打开 Visio 文档。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ec46f4fd7be136d16e15e9fa366b7a4cb921b62e
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523843"
---
# <a name="how-to-programmatically-open-visio-documents"></a>如何：以编程方式打开 Visio 文档
  可以通过两种方法打开现有 Microsoft Office Visio 文档： Open 和 Microsoft.office.interop.visio.documents.open。 Microsoft.office.interop.visio.documents.open 方法与 Open 方法相同，不同之处在于它提供调用方可以在其中指定文档打开方式的参数。

 有关对象模型的详细信息，请参阅 [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Documents.Open) 方法和 [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Documents.OpenEx) 方法的 VBA 参考文档。

## <a name="open-a-visio-document"></a>打开 Visio 文档

### <a name="to-open-a-visio-document"></a>若要打开 Visio 文档

- 调用 `Microsoft.Office.Interop.Visio.Documents.Open` 方法并提供 Visio 文档的完全限定路径。

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]

## <a name="open-a-visio-document-with-specified-arguments"></a>使用指定参数打开 Visio 文档

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>如要以只读和停靠方式打开 Visio 文档

- 调用 `Microsoft.Office.Interop.Visio.Documents.OpenEx` 方法，提供 Visio 文档的完全限定路径，并包括想要使用的参数，在本例中为 Docked 和 Read-only。

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]

## <a name="compile-the-code"></a>编译代码
 此代码示例要求满足以下条件：

- 名为的 Visio 文档 `myDrawing.vsd` 必须位于 `Test` windows XP 和更早) 版本的 " *我的文档* " 文件夹 (中名为的目录中，或 windows Vista)  (的 *documents* 文件夹中。

## <a name="see-also"></a>另请参阅
- [Visio 解决方案](../vsto/visio-solutions.md)
- [Visio 对象模型概述](../vsto/visio-object-model-overview.md)
- [如何：以编程方式创建新的 Visio 文档](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [如何：以编程方式关闭 Visio 文档](../vsto/how-to-programmatically-close-visio-documents.md)
- [如何：以编程方式保存 Visio 文档](../vsto/how-to-programmatically-save-visio-documents.md)
- [如何：以编程方式打印 Visio 文档](../vsto/how-to-programmatically-print-visio-documents.md)
