---
description: 当正在调试的程序完成单步执行、逐过程执行或跳出源代码或语句或指令行时，调试引擎会将此接口发送 (DE) 到会话调试管理器 (SDM) 。
title: IDebugStepCompleteEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStepCompleteEvent2
helpviewer_keywords:
- IDebugStepCompleteEvent2 interface
ms.assetid: eba2b76e-f90d-486b-ae5c-c47f1b8ba2e5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f366b9eb1d9406ba5207016ca97ea40d1fd48529
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149530"
---
# <a name="idebugstepcompleteevent2"></a>IDebugStepCompleteEvent2
当正在调试的程序完成单步执行、逐过程执行或跳出源代码或语句或指令行时，调试引擎会将此接口发送 (DE) 到会话调试管理器 (SDM) 。

## <a name="syntax"></a>语法

```
IDebugStepCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>实施者注意事项
 DE 实现此接口来报告步骤操作的完成。 必须在与此接口相同的对象上实现 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口。 SDM 使用 [QueryInterface](/cpp/atl/queryinterface) 访问 `IDebugEvent2` 接口。

## <a name="notes-for-callers"></a>调用方说明
 DE 创建并发送此事件对象，以报告步骤操作的完成。 此事件在附加到正在调试的程序时，使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数发送。

## <a name="remarks"></a>备注
 完成该步骤后，要调试的程序将再次暂停，IDE 将更新其所有窗口。

## <a name="requirements"></a>要求
 标头： msdbg

 命名空间： VisualStudio

 程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另请参阅
- [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
