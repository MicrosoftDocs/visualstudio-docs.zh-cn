---
description: 此接口提供多种方法来访问端口的服务器和通知工具。
title: IDebugDefaultPort2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a5ec637daa197574710978af7cb22195c969f48b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154413"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
此接口提供多种方法来访问端口的服务器和通知工具。

## <a name="syntax"></a>语法

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>实施者注意事项
 Visual Studio 实现此接口，以表示用于访问程序的调试端口。 如果自定义端口供应商处理远程调试，还可以实现此接口。

## <a name="notes-for-callers"></a>调用方说明
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)接口上的方法的参数提供此接口。 在[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)接口上调用[QueryInterface](/cpp/atl/queryinterface)还可以获取此接口。

## <a name="methods-in-vtable-order"></a>Vtable 顺序的方法
 除了在 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)中定义的方法，此接口还实现以下方法：

|方法|说明|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|从此端口获取端口通知接口。|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|获取承载此端口的服务器的接口。|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|确定此端口是否在本地计算机上运行。|

## <a name="remarks"></a>备注
 名称 " `IDebugDefaultPort2` " 是 misnomer 的一个小数位，因为它不表示默认端口。 它可以名为 "IDebugPort3"。

## <a name="requirements"></a>要求
 标头： msdbg

 命名空间： VisualStudio

 程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另请参阅
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
