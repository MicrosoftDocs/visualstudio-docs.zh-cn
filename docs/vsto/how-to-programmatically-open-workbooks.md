---
title: 如何：以编程方式打开工作簿
description: 了解如何使用 Visual Studio 以编程方式打开 Microsoft Excel 工作簿或使用现有工作簿。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f7de4072df177bd9a7c6ae23bf59e44e50d56e32
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523898"
---
# <a name="how-to-programmatically-open-workbooks"></a>如何：以编程方式打开工作簿
  <xref:Microsoft.Office.Interop.Excel.Workbooks>使用 Microsoft Office Excel 中的集合，可以使用所有打开的工作簿并打开工作簿。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>打开现有工作簿

1. 使用 <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> 集合的方法 <xref:Microsoft.Office.Interop.Excel.Workbooks> ，并传入工作簿的路径。

     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]

## <a name="compile-the-code"></a>编译代码
 此代码示例要求满足以下条件：

- 在 `YourWorkbook.xls` 驱动器 C 上名为的目录中必须存在名为的工作簿 `Test` 。

## <a name="see-also"></a>另请参阅
- [使用工作簿](../vsto/working-with-workbooks.md)
- [如何：以编程方式将文本文件作为工作簿打开](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [如何：以编程方式创建新的工作簿](../vsto/how-to-programmatically-create-new-workbooks.md)
- [如何：以编程方式保存工作簿](../vsto/how-to-programmatically-save-workbooks.md)
- [如何：以编程方式关闭工作簿](../vsto/how-to-programmatically-close-workbooks.md)
- [宿主项和宿主控件的编程限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 解决方案中的可选参数](../vsto/optional-parameters-in-office-solutions.md)
- [主机项和主机控件概述](../vsto/host-items-and-host-controls-overview.md)
