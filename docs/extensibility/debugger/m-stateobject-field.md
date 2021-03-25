---
description: 表示操作将使用的数据的对象。
title: m_stateObject 字段 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2128073f47c76244a18e18005a431f9317686c3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054785"
---
# <a name="m_stateobject-field"></a>m_stateObject 字段
表示操作将使用的数据的对象。

 **命名空间：** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly：** mscorlib (*mscorlib.dll*) 

 由于无法从 .NET Framework 访问此内部成员，因此在公共中间语言 (CIL) 中提供了以下语法。

## <a name="syntax"></a>语法

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>备注
 这是 `state` 构造函数中的 <xref:System.Threading.Tasks.Task.%23ctor%2A> 参数。 它也是属性的支持字段 <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> 。

## <a name="see-also"></a>另请参阅
- [Task 类](../../extensibility/debugger/task-class-internal-members.md)
