---
description: 指定要转储的程序状态 (如运行线程、堆栈帧和当前指令地址) 的数量。
title: DUMPTYPE |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc27474b0012e60cccadda44665dc368178a02da
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095961"
---
# <a name="dumptype"></a>DUMPTYPE
指定要转储的程序状态 (如运行线程、堆栈帧和当前指令地址) 的数量。

## <a name="syntax"></a>语法

```cpp
enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
typedef DWORD DUMPTYPE;
```

```csharp
public enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
```

## <a name="fields"></a>字段
`DUMP_MINIDUMP`\
指定小型的精简转储。

`DUMP_FULLDUMP`\
指定大的完整转储。

## <a name="remarks"></a>备注
作为参数传递给 [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) 方法。

## <a name="requirements"></a>要求
标头： msdbg

命名空间： VisualStudio

程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>请参阅
- [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)
