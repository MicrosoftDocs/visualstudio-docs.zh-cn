---
description: 程序节点使用此接口来指定可调试此程序 (DE) 的所有可能的调试引擎。
title: IDebugProgramEngines2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e0202185d760a1e3334996906807e5922fe61e0a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084215"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
程序节点使用此接口来指定可调试此程序 (DE) 的所有可能的调试引擎。

## <a name="syntax"></a>语法

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>实施者注意事项
 一个 DE 或自定义端口提供程序在实现 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 的同一对象上实现此接口，以便支持建立特定的用于特定程序的 DE。

## <a name="notes-for-callers"></a>调用方说明
 在接口上调用 [QueryInterface](/cpp/atl/queryinterface) `IDebugProgramNode2` 以获取此接口。

## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法
 下表显示的方法 `IDebugProgramEngines2` 。

|方法|说明|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|指示可调试此程序的所有可能的 DEs。|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|选择用于调试此程序的 DE。|

## <a name="remarks"></a>备注
 一旦用户选择了 DE 后，就会调用 [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)，将该选项注册到 "程序" 节点。 所选引擎将成为 [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)返回的引擎。

## <a name="requirements"></a>要求
 标头： msdbg

 命名空间： VisualStudio

 程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另请参阅
- [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
