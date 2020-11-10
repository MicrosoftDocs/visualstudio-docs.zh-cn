---
title: 工作流设计器 TerminateWorkflow 活动设计器
description: 了解如何使用 TerminateWorkflow 活动设计器创建和配置 TerminateWorkflow 活动。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5af1f8656e796d9551e1d140b07868551d563a90
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433864"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow 活动设计器

" **TerminateWorkflow** " 活动设计器用于创建和配置 <xref:System.Activities.Statements.TerminateWorkflow> 活动。

## <a name="the-terminateworkflow-activity"></a>TerminateWorkflow 活动

<xref:System.Activities.Statements.TerminateWorkflow> 活动终止工作流的执行。

### <a name="using-the-terminateworkflow-activity-designer"></a>使用 TerminateWorkflow 活动设计器

" **TerminateWorkflow** " 活动设计器可在 " **工具箱** " 的 " **运行时** " 类别中找到，可通过单击 " **工具箱** " 选项卡 (或者，从 " **视图** " 菜单中选择 " **工具箱** " 或按 CTRL + ALT + X。 ) 

可以将 " **TerminateWorkflow** " 活动设计器从 " **工具箱** " 拖放到工作流设计器图面上通常放置活动的任何位置，例如中 <xref:System.Activities.Statements.Sequence> 。 这将创建 <xref:System.Activities.Statements.TerminateWorkflow> 具有 TerminateWorkflow 的默认 **DisplayName** 的活动。 <xref:System.Activities.Activity.DisplayName%2A>可以在 " **TerminateWorkflow** " 活动设计器的标头中或在属性网格的 " **DisplayName** " 框中编辑。

### <a name="the-terminateworkflow-properties"></a>TerminateWorkflow 属性

下表列出 <xref:System.Activities.Statements.TerminateWorkflow> 属性并说明如何在设计器中使用它们。 这些属性可以在属性网格中进行编辑，其中一些属性可以在工作流设计器图面上进行编辑。

|属性名称|必选|使用情况|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|错误|<xref:System.Activities.Statements.TerminateWorkflow> 活动的友好名称。 默认值为 TerminateWorkflow。 虽然显示名称不是绝对必需的，但最好使用显示名称。|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|错误|终止工作流时要引发的异常。 此属性在属性网格中设置。|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|错误|解释终止工作流的原因。 此属性在属性网格中设置。|

## <a name="see-also"></a>另请参阅

- [运行时](../workflow-designer/runtime-activity-designers.md)
- [保留](../workflow-designer/persist-activity-designer.md)
