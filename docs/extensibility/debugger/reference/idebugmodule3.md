---
description: 此接口表示支持符号和 JustMyCode 状态的备用位置的模块。
title: IDebugModule3 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0ccac9c260619b21079c6a277d842d322750cbc1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065484"
---
# <a name="idebugmodule3"></a>IDebugModule3
此接口表示支持符号和 JustMyCode 状态的备用位置的模块。

## <a name="syntax"></a>语法

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>实施者注意事项
 调试引擎 (DE) 实现此接口以支持符号的备用位置，并使用 JustMyCode 状态 (请参阅 [Visual Studio 调试器术语表](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) 中的 "JustMyCode" ) 定义。

## <a name="notes-for-callers"></a>调用方说明
 对 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) 的调用返回此接口。 DE 使用[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)方法将[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)接口发送到会话调试管理器 (SDM) 。 此外，对[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)接口上的[QueryInterface](/cpp/atl/queryinterface)的调用返回此接口。

## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法
 除了 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 接口上的方法，此接口还实现以下方法：

|方法|说明|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|返回搜索符号的路径列表，以及搜索每个路径的结果。|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|为当前模块加载和初始化符号。|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|返回指定模块是否表示用户代码的标志。|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|指定是否应将模块视为用户代码。|

## <a name="remarks"></a>备注
 Visual Studio 是此接口的典型使用者。

## <a name="requirements"></a>要求
 标头： msdbg

 命名空间： VisualStudio

 程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另请参阅
- [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
