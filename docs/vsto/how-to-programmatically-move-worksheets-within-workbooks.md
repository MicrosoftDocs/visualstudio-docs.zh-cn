---
title: 如何：以编程方式在工作簿中移动工作表
description: 了解如何在 Microsoft Excel 工作簿中以编程方式更改工作表相对于其他工作表的位置。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fd05dcb39c295d4d1ebb39d933c643f61c6d921c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827287"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>如何：以编程方式在工作簿中移动工作表
  可以通过编程方式更改工作簿中工作表相对于其他工作表的位置。 如果不为移动的工作表指定位置，Excel 将创建新的工作簿来容纳它。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>在文档级自定义项中移动工作表

1. 将工作簿中的工作表的总数分配给一个变量，然后移动第一个工作表，使其成为最后一个工作表。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet24":::

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>在 VSTO 外接程序中移动工作表

1. 将工作簿中的工作表的总数分配给一个变量，然后移动第一个工作表，使其成为最后一个工作表。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet16":::

## <a name="see-also"></a>请参阅
- [使用工作表](../vsto/working-with-worksheets.md)
- [如何：以编程方式隐藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)
- [如何：以编程方式从工作簿中删除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [如何：以编程方式保护工作表](../vsto/how-to-programmatically-protect-worksheets.md)
- [对 Office 项目中对象的全局访问](../vsto/global-access-to-objects-in-office-projects.md)
