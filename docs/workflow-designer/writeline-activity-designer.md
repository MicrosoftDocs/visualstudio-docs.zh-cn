---
title: 工作流设计器-WriteLine 活动设计器
description: 了解 WriteLine 活动，以及如何使用 WriteLine 活动设计器来创建和配置 WriteLine 活动。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7cb4806949b21a6c92548b91623e63306f2a7722
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875102"
---
# <a name="writeline-activity-designer"></a>WriteLine 活动设计器

" **WriteLine** " 活动设计器用于创建和配置 <xref:System.Activities.Statements.WriteLine> 活动。

## <a name="the-writeline-activity"></a>WriteLine 活动

<xref:System.Activities.Statements.WriteLine> 活动将文本写入指定的 <xref:System.IO.TextWriter> 对象。 如果未指定 <xref:System.IO.TextWriter>，则 <xref:System.Activities.Statements.WriteLine> 会将文本写入控制台中。

### <a name="using-the-writeline-activity-designer"></a>使用 WriteLine 活动设计器

访问 "**工具箱**" 的 "**基元**" 类别中的 " **WriteLine** " 活动设计器。 可以将 " **WriteLine** " 活动设计器从 " **工具箱** " 拖放到工作流设计器图面上通常放置活动的任何位置，例如中 <xref:System.Activities.Statements.Sequence> 。 这将创建具有 WriteLine 的默认 <xref:System.Activities.Statements.WriteLine> 的 <xref:System.Activities.Activity.DisplayName%2A> 活动。 <xref:System.Activities.Activity.DisplayName%2A>可以在 " **WriteLine** " 活动设计器的标头中或在属性网格的 " **DisplayName** " 框中编辑。

### <a name="the-writeline-properties"></a>WriteLine 属性

下表列出 <xref:System.Activities.Statements.WriteLine> 属性并说明如何在设计器中使用它们。 这些属性可以在属性网格中进行编辑，其中一些属性可以在工作流设计器图面上进行编辑。

|属性名称|必选|使用情况|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.WriteLine> 活动的友好名称。 默认值为 WriteLine。 虽然 <xref:System.Activities.Activity.DisplayName%2A> 不是绝对必需的，但最好使用该属性。|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|要写入的文本。 若要设置属性，请在 " **WriteLine** " 活动设计器或属性网格中的 **文本框** 中键入 Visual Basic 表达式。|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.IO.TextWriter> 向其写入 <xref:System.Activities.Statements.WriteLine> 的 <xref:System.Activities.Statements.WriteLine.Text%2A>。 默认为控制台。|

## <a name="see-also"></a>另请参阅

- [基元](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [延迟](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
