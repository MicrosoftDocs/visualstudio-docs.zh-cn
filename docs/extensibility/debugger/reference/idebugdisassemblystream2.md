---
title: IDebugDisassemblyStream2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d561c8eaa9f7b4fc08f71c241fd052fd366ca80d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944636"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
此接口表示指令流。

## <a name="syntax"></a>语法

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>实施者注意事项
 调试引擎实现此接口以支持对程序代码的反汇编。

## <a name="notes-for-callers"></a>调用方说明
 对 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) 方法的调用返回此接口。

## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法
 下表显示的方法 `IDebugDisassemblyStream2` 。

|方法|说明|
|------------|-----------------|
|[读取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|从反汇编流中的当前位置开始读取指令。|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|相对于指定位置，将给定数量的指令移动到反汇编流中的读取指针。|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|返回特定代码上下文的代码位置标识符。|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|返回对应于指定代码位置标识符的代码上下文对象。|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|返回表示当前代码位置的代码位置标识符。|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|获取与此反汇编流关联的源文档。|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|获取此反汇编流的范围。|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|获取此反汇编流的大小。|

## <a name="remarks"></a>备注
 可以创建反汇编流来表示整个地址空间，或者只表示空间中的一个函数或模块。 每个指令都由对[Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)方法的调用返回的[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)结构表示。

## <a name="requirements"></a>要求
 标头： msdbg

 命名空间： VisualStudio

 程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另请参阅
- [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
