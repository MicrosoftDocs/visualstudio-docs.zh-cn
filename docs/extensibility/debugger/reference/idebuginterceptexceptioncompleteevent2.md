---
title: IDebugInterceptExceptionCompleteEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d98f8653d851eb338a96f969d73a2514b555f400
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890274"
---
# <a name="idebuginterceptexceptioncompleteevent2"></a>IDebugInterceptExceptionCompleteEvent2
当 DE 完成对截获事件的处理时，调试引擎会将此接口 (DE) 发送到会话调试管理器 (SDM) 。

## <a name="syntax"></a>语法

```
IDebugInterceptExceptionCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>实施者注意事项
 DE 实现此接口，报告已完成截获异常的处理。 必须在与此接口相同的对象上实现 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 接口。 SDM 使用 [QueryInterface](/cpp/atl/queryinterface) 访问 `IDebugEvent2` 接口。

## <a name="notes-for-callers"></a>调用方说明
 DE 创建并发送此事件对象，以报告截获的异常的完成。 使用 SDM 在附加到正在调试的程序时提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回调函数发送事件。

## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法
 `IDebugInterceptExceptionCompleteEvent2`接口实现以下方法。

|方法|说明|
|------------|-----------------|
|[GetInterceptCookie](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2-getinterceptcookie.md)|返回与已处理的异常关联的唯一值。|

## <a name="remarks"></a>备注
 当该方法已成功处理截获的异常时， [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) 将发送此事件。

## <a name="requirements"></a>要求
 标头： msdbg

 命名空间： VisualStudio

 程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另请参阅
- [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
