---
title: IDebugExpressionContext2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 92e2561d28c3d4c7133208c78b9a492bc2614fd3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901661"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
此接口表示表达式计算的上下文

## <a name="syntax"></a>语法

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>实施者注意事项
 调试引擎 (DE) 实现此接口，以表示可以计算表达式的上下文。

## <a name="notes-for-callers"></a>调用方说明
 对 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 的调用返回此接口。 仅当正在调试的程序已暂停且堆栈帧可用时，才能访问此接口。

## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法
 下表显示的方法 `IDebugExpressionContext2` 。

|方法|说明|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|检索计算上下文的名称。|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|分析用于计算的基于文本的表达式。|

## <a name="remarks"></a>备注
 可以将计算上下文视为用于执行表达式计算的作用域。

 当程序停止时，会话调试管理器 (SDM) 通过调用 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)从 DE 获取堆栈帧。 然后，SDM 调用 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 来获取 `IDebugExpressionContext2` 接口。 接下来，调用 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 来创建 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) 接口，该接口表示可进行计算的已分析表达式。

## <a name="requirements"></a>要求
 标头： msdbg

 命名空间： VisualStudio

 程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另请参阅
- [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
