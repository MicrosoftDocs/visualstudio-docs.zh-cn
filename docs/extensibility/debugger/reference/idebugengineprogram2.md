---
description: 此接口提供多线程调试支持。
title: IDebugEngineProgram2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e52ae6477b49325d4b8a4d81192fe2ecf736163
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092652"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
此接口提供多线程调试支持。

## <a name="syntax"></a>语法

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>实施者注意事项
 调试引擎实现此接口以支持同时调试多个线程。 在实现 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 接口的同一对象上实现此接口。

## <a name="notes-for-callers"></a>调用方说明
 使用 [QueryInterface](/cpp/atl/queryinterface) 从接口获取此接口 `IDebugProgram2` 。

## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法
 下表显示的方法 `IDebugEngineProgram2` 。

|方法|说明|
|------------|-----------------|
|[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|停止在此程序中运行的所有线程。|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|监视执行 (或停止监视执行) 在给定线程上发生。|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|允许 (或不允许) 表达式计算在给定线程上发生，即使程序已停止也是如此。|

## <a name="remarks"></a>备注
 Visual Studio 将调用此接口以响应 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 事件，并设置 "监视线程步骤" 和 "在线程上监视表达式计算" 状态。 每当程序停止时调用[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md);此方法为程序提供了终止所有线程的机会。

## <a name="requirements"></a>要求
 标头： msdbg

 命名空间： VisualStudio

 程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另请参阅
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
