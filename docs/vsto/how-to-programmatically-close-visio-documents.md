---
title: 如何：以编程方式关闭 Visio 文档
description: 了解如何使用 Microsoft.Office.Interop.Visio.Docargumentable 关闭 active Microsoft Office Visio 文档。Close 方法。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8802cc34555fcb695c5554209255cb8fd9f154c2
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825298"
---
# <a name="how-to-programmatically-close-visio-documents"></a>如何：以编程方式关闭 Visio 文档
  可以使用 `Microsoft.Office.Interop.Visio.Document.Close` 方法关闭活动 Microsoft Office Visio 文档。

 有关此方法的详细信息，请参阅 [Microsoft.Office.Interop.Visio.Document.Close](/office/vba/api/Visio.Document.Close) 方法的 VBA 参考文档。

## <a name="close-the-active-document"></a>关闭活动文档

### <a name="to-close-the-active-document"></a>关闭活动文档

- 调用 `Microsoft.Office.Interop.Visio.Document.Close` 方法关闭活动文档。

     若要使用下面的代码示例，请在 `ThisAddIn` Visio 的 VSTO 外接程序项目的类中运行它。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet7":::

## <a name="see-also"></a>另请参阅
- [Visio 解决方案](../vsto/visio-solutions.md)
- [Visio 对象模型概述](../vsto/visio-object-model-overview.md)
- [如何：以编程方式创建新的 Visio 文档](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [如何：以编程方式打开 Visio 文档](../vsto/how-to-programmatically-open-visio-documents.md)
- [如何：以编程方式保存 Visio 文档](../vsto/how-to-programmatically-save-visio-documents.md)
- [如何：以编程方式打印 Visio 文档](../vsto/how-to-programmatically-print-visio-documents.md)
