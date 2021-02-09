---
title: BP_COND_STYLE |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f98f02e7e756a744d8042a9955802165065d54d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862157"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
为挂起断点和绑定断点指定断点条件样式。

## <a name="syntax"></a>语法

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="fields"></a>字段
`BP_COND_NONE`\
当到达断点的位置时，将激发断点。 未指定断点条件。

`BP_COND_WHEN_TRUE`\
仅当与断点关联的条件表达式的计算结果为时，才引发断点 `true` 。

`BP_COND_WHEN_CHANGED`\
仅当与断点关联的条件表达式的值与以前的计算发生了更改时，才会激发断点。

## <a name="remarks"></a>备注
用于 `styleCondition` [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 结构的成员。

## <a name="requirements"></a>要求
标头： msdbg

命名空间： VisualStudio

程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>请参阅
- [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
