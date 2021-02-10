---
title: IDebugEventCallback2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fe81a7d8a07a80f38e771e2cfbac3ec23da54b62
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933357"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
调试引擎使用此接口 (DE) 将调试事件发送到会话调试管理器 (SDM) 。

## <a name="syntax"></a>语法

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>实施者注意事项
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 实现此接口，以便从调试引擎接收事件。

## <a name="notes-for-callers"></a>调用方说明
 当 SDM 调用 [attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)、 [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)或 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)时，调试引擎通常会接收此接口。 调试引擎通过调用 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)向 SDM 发送事件。

## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法
 下表显示的方法 `IDebugEventCallback2` 。

|方法|说明|
|------------|-----------------|
|[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|向 SDM 发送调试事件的通知。|

## <a name="remarks"></a>备注
 尽管 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 和 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 指定它们采用 `IDebugEventCallback2` 接口，但并不是这种情况，接口指针将始终为 null 值。 相反，调试引擎必须使用对 `IDebugEventCallback2` [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)、 [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)或 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)的调用中接收的接口。

 如果包在托管代码中实现 [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) ，强烈建议 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> 在传递到 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)的各种接口上调用。

## <a name="requirements"></a>要求
 标头： msdbg

 命名空间： VisualStudio

 程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另请参阅
- [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)
