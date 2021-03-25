---
description: 描述错误断点的解决方法，包括位置、程序和线程。
title: BP_ERROR_RESOLUTION_INFO |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 44bf92db77bf39e7e4a214e902781e27a7a731ef
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085294"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
描述错误断点的解决方法，包括位置、程序和线程。

## <a name="syntax"></a>语法

```cpp
typedef struct _BP_ERROR_RESOLUTION_INFO {
    BPERESI_FIELDS         dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
    BSTR                   bstrMessage;
    BP_ERROR_TYPE          dwType;
} BP_ERROR_RESOLUTION_INFO;
```

```csharp
public struct BP_ERROR_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
    public string                 bstrMessage;
    public uint                   dwType;
};
```

## <a name="members"></a>成员
`dwFields`\
[BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md)枚举中的值的组合，用于指定要填写此结构的哪些字段。

`bpResLocation`\
[BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)联合，它指定断点解析位置。

`pProgram`\
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)对象，它表示发生断点错误的应用程序。

`pThread`\
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)对象，它表示在其上运行生成断点错误的应用程序的线程。

`bstrMessage`\
包含此错误解析产生的任何警告或错误消息的字符串。

`dwType`\
[BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)枚举中指定断点错误类型的值。

## <a name="remarks"></a>备注
此结构是从 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) 方法返回的。

## <a name="requirements"></a>要求
标头： msdbg

命名空间： VisualStudio

程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另请参阅
- [结构和联合](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
