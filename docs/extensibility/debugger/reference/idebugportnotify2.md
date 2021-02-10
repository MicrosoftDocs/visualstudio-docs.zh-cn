---
title: IDebugPortNotify2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 74b9e62b2e442bbab01942f155647f16eae29b09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941653"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
此接口可注册或取消注册可使用运行该程序的端口进行调试的程序。

## <a name="syntax"></a>语法

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>实施者注意事项
 自定义端口供应商实现此接口，以支持从端口添加和删除程序。 它通常在实现 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 接口的同一对象上实现。

## <a name="notes-for-callers"></a>调用方说明
 对接口的 [QueryInterface](/cpp/atl/queryinterface) 的调用 `IDebugPort2` 返回此接口。 此外，对 [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) 的调用返回此接口。 调试引擎可以将此接口查看为 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)的参数。

## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法
 下表显示的方法 `IDebugPortNotify2` 。

|方法|说明|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|注册一个程序，该程序可以使用其运行所在的端口进行调试。|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|取消注册可从运行该程序的端口进行调试的程序。|

## <a name="remarks"></a>备注
 除非调试端口有办法知道加载或卸载程序的时间，否则自定义端口提供程序必须实现此接口。 使用此接口跟踪为通过特定端口进行调试而加载的所有程序。

## <a name="requirements"></a>要求
 标头： msdbg

 命名空间： VisualStudio

 程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另请参阅
- [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
