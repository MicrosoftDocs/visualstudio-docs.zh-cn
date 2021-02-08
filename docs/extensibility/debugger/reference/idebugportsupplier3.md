---
title: IDebugPortSupplier3 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d45d8d93f26ef01fb184811a87b4f4fcc4483340
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840231"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
通过此接口，调用方可以确定端口供应商是否可以通过将端口写入) 在调试器调用之间 (保留端口，然后获取这些保留端口的列表。

## <a name="syntax"></a>语法

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>实施者注意事项
 自定义端口供应商实现此接口，以支持将端口信息保存到磁盘或将其保存到磁盘。 此接口必须在与 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) 接口相同的对象上实现。

## <a name="notes-for-callers"></a>调用方说明
 在接口上调用 [QueryInterface](/cpp/atl/queryinterface) `IDebugPortSupplier2` 以获取此接口。

## <a name="methods-in-vtable-order"></a>Vtable 顺序的方法
 除了继承自 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) 接口的方法之外，此接口还支持以下各项：

|方法|说明|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|返回端口供应商是否可以通过将端口写入) 在调试器调用之间 (来持久保存端口。|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|返回一个对象，该对象可用于枚举此端口提供程序写入磁盘的所有端口。|

## <a name="remarks"></a>备注
 如果端口供应商可以在各个调用之间保持端口，则它应实现此接口。 在实例化端口供应商时应加载端口，并在销毁端口供应商时将其写入磁盘。

 调试引擎通常不与端口供应商交互，并且不会使用此接口。

## <a name="requirements"></a>要求
 标头： msdbg

 命名空间： VisualStudio

 程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另请参阅
- [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
