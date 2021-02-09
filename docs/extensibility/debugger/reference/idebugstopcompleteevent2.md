---
title: IDebugStopCompleteEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bee46a1f097d1bee98354acb792f75ea9431f301
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897206"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

当程序停止时，调试引擎 (DE) 可以将此可选事件发送到会话调试管理器 (SDM) 。

## <a name="syntax"></a>语法

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>实施者注意事项

此接口是随 Visual Studio 2005 一起引入的。 以前的版本不支持异步停止。

- 在多进程或多程序方案中，由 SDM 调用[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)。 当一个程序向 SDM 发送停止事件时，SDM 还请求其他程序停止。

Stop 用于异步通知 SDM 程序已停止。 通知 SDM 对于解释器调试引擎非常有用，在这种情况下，调试程序中有时不会运行任何代码，因此无法同步完成 [停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 。 如果调试引擎要使用此异步通知，则它必须 `S_ASYNC_STOP` 从 [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)返回。

## <a name="requirements"></a>要求

标头： msdbg

命名空间： VisualStudio

程序集： Microsoft.VisualStudio.Debugger.Interop.dll
