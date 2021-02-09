---
title: IEnumDebugAddresses |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f9b4b95d805833ffd8b8041292cd18e5db8df9b3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875791"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
此接口表示实现 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 接口的对象的集合。

## <a name="syntax"></a>语法

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>实施者注意事项
 此接口由符号提供程序实现，用于提供实现 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 接口的对象集。 请注意，这不是标准的 COM 枚举，因为存在 [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) 方法。

## <a name="notes-for-callers"></a>调用方说明
 此接口由 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) 和 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)返回。

## <a name="methods-in-vtable-order"></a>Vtable 顺序的方法
 此接口实现以下方法。

|方法|说明|
|------------|-----------------|
|[下一页](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|从枚举中检索下一组 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 对象。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|跳过指定数量的条目。|
|[重置](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|将枚举重置为第一个条目。|
|[克隆](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|检索当前枚举的副本。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|检索枚举中的项数。|

## <a name="remarks"></a>备注
 此接口通常由调试引擎用来帮助确定要为表达式计算器指定的适当地址。

## <a name="requirements"></a>要求
 标头： sh。h

 命名空间： VisualStudio

 程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另请参阅
- [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
