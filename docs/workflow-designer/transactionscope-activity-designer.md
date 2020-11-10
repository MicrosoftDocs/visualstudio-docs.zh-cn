---
title: 工作流设计器-TransactionScope 活动设计器
description: 了解如何使用 "TransactionScope" 活动设计器来创建和配置 TransactionScope 活动。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1fde6dabb372bfa20f55335008ce91e8de2481a
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433578"
---
# <a name="transactionscope-activity-designer"></a>TransactionScope 活动设计器

" **TransactionScope** " 活动设计器用于创建和配置 <xref:System.Activities.Statements.TransactionScope> 活动。

## <a name="the-transactionscope-activity"></a>TransactionScope 活动

<xref:System.Activities.Statements.TransactionScope> 活动在单个事务中执行所包含的活动。 在 <xref:System.Activities.Statements.TransactionScope.Body%2A> 活动以及该事务中的所有其他参与者成功完成时将提交该事务。

### <a name="using-the-transactionscope-activity-designer"></a>使用 TransactionScope 活动设计器

访问 " **工具箱** " 的 " **事务** " 类别中的 " **TransactionScope** " 活动设计器。 可以将 " **TransactionScope** " 活动设计器从 " **工具箱** " 拖放到工作流设计器图面上通常放置活动的任何位置，例如中 <xref:System.Activities.Statements.Sequence> 。 这将创建具有 TransactionScope 的默认 <xref:System.Activities.Statements.TransactionScope> 的 <xref:System.Activities.Activity.DisplayName%2A> 活动。 <xref:System.Activities.Activity.DisplayName%2A>可以在 " **TransactionScope** " 活动设计器的标头中或在属性网格的 " **DisplayName** " 框中编辑值。

### <a name="the-transactionscope-properties"></a>TransactionScope 属性

下表列出 <xref:System.Activities.Statements.TransactionScope> 属性并说明如何在设计器中使用它们。 <xref:System.Activities.Activity.DisplayName%2A>和 <xref:System.Activities.Statements.TransactionScope.Body%2A> 属性可在工作流设计器图面上进行编辑。 但其他属性必须在属性网格上编辑。

|属性名称|必选|使用情况|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|错误|<xref:System.Activities.Statements.TransactionScope> 活动的可选友好名称。 默认值为 TransactionScope。 虽然 <xref:System.Activities.Activity.DisplayName%2A> 值不是绝对必需的，但最好使用该属性值。|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|正确|指定要在单个事务中执行的活动。 若要添加 <xref:System.Activities.Statements.TransactionScope.Body%2A> 活动，请将活动从 " **工具箱** " 拖放到 " **TransactionScope** " 活动设计器上的 " **正文** " 框中，其中包含提示文本 "将活动放在此处"。|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|正确|指定此 <xref:System.Transactions.IsolationLevel> 的 <xref:System.Activities.Statements.TransactionScope>。|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|错误|指定必须在其间完成事务的时间间隔（格式为 00:00:00，表示小时:分钟:秒）。 默认值为 1 分钟 (00:01:00)。|
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure*>|正确|指定指示在事务中止的情况下是否应中止工作流的值。|

## <a name="see-also"></a>另请参阅

- [事务](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [逐条](../workflow-designer/confirm-activity-designer.md)
