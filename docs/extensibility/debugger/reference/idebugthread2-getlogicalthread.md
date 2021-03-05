---
description: 调试引擎不实现此方法。
title: IDebugThread2：： GetLogicalThread |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9193cde20ba1035552451143c676aab291d7c684
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168343"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
调试引擎不实现此方法。

## <a name="syntax"></a>语法

```cpp
HRESULT GetLogicalThread( 
   IDebugStackFrame2*     pStackFrame,
   IDebugLogicalThread2** ppLogicalThread
);
```

```csharp
int GetLogicalThread( 
   IDebugStackFrame2        pStackFrame,
   out IDebugLogicalThread2 ppLogicalThread
);
```

## <a name="parameters"></a>参数
`pStackFrame`\
中表示堆栈帧的 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 对象。

`ppLogicalThread`\
弄返回 `IDebugLogicalThread2` 表示关联的逻辑线程的接口。 调试引擎实现应将此值设置为 null 值。

## <a name="return-value"></a>返回值
 调试引擎实现始终返回 `E_NOTIMPL` 。

## <a name="see-also"></a>另请参阅
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
