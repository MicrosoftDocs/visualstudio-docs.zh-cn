---
description: 此接口告诉会话调试管理器 (SDM) 挂起的断点未能绑定到加载的程序，原因是出现警告或错误。
title: IDebugBreakpointErrorEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a7ebfa6b5d1cc2a0fe1a03c9e70952c5cec1a74e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054524"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
此接口告诉会话调试管理器 (SDM) 挂起的断点未能绑定到加载的程序，原因是出现警告或错误。

## <a name="syntax"></a>语法

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>实施者注意事项
 DE 实现此接口作为其对断点的支持的一部分。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)接口必须在与此接口相同的对象上实现 (SDM 使用[QueryInterface](/cpp/atl/queryinterface)访问 `IDebugEvent2` 接口) 。

## <a name="notes-for-callers"></a>调用方说明
 当挂起的断点无法绑定到正在调试的程序时，将创建并发送此事件对象。 使用 SDM 在附加到正在调试的程序时提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数发送事件。

## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法
 下表显示的方法 `IDebugBreakpointErrorEvent2` 。

|方法|说明|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|获取描述警告或错误的 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 接口。|

## <a name="remarks"></a>备注
 每当绑定断点时，都会向 SDM 发送事件。 如果无法绑定断点， `IDebugBreakpointErrorEvent2` 则发送; 否则，将发送 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 。

 例如，当与挂起断点关联的条件未能分析或计算时，将发送一条警告，指出此时无法绑定挂起的断点。 如果尚未加载断点的代码，则可能会发生这种情况。

## <a name="requirements"></a>要求
 标头： msdbg

 命名空间： VisualStudio

 程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另请参阅
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
