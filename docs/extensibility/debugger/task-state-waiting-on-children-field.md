---
description: 任务已完成执行其委托，并隐式等待附加的子任务完成。
title: TASK_STATE_WAITING_ON_CHILDREN 字段 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 955523b58703023add8b4bf312a98df8f792d3ef
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075284"
---
# <a name="task_state_waiting_on_children-field"></a>TASK_STATE_WAITING_ON_CHILDREN 字段
任务已完成执行其委托，并隐式等待附加的子任务完成。

 **命名空间：** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly：** mscorlib (*mscorlib.dll*) 

 由于无法从 .NET Framework 访问此内部成员，因此在公共中间语言 (CIL) 中提供了以下语法。

## <a name="syntax"></a>语法

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>备注
 如果 [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) 字段包含此值，则 <xref:System.Threading.Tasks.Task.Status%2A> 属性将返回 <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> 。

## <a name="see-also"></a>另请参阅
- [Task 类](../../extensibility/debugger/task-class-internal-members.md)
