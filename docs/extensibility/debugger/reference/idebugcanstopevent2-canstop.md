---
description: 通知调试引擎 (取消) 是否在当前代码位置停止或只是继续执行。
title: IDebugCanStopEvent2：： CanStop |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38b4d528ae1aa5a89853dc4873a9c07aa051a14c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173631"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
通知调试引擎 (取消) 是否在当前代码位置停止或只是继续执行。

## <a name="syntax"></a>语法

```cpp
HRESULT CanStop ( 
   BOOL fCanStop
);
```

```csharp
int CanStop ( 
   int fCanStop
);
```

## <a name="parameters"></a>参数
`fCanStop`\
中 `TRUE` 如果 DE 应停止在当前代码位置，则为非零 () ; 否则为零 (`FALSE`) 。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
 此事件的接收方通常会调用 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) 方法来确定 DE 要停止的原因，然后调用 `IDebugCanStopEvent2::CanStop` 方法并提供适当的响应。

 如果停止，则会发送描述停止原因的事件。 通常发送两个事件： [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) 接口表示的用户或信号中断，以及由 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) 接口表示的断点事件。

## <a name="see-also"></a>另请参阅
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
