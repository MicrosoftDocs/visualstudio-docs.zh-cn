---
description: 此接口使会话调试管理器 (SDM) 控制端口上运行的程序和进程。
title: IDebugPortEx2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e26fec4b47a301bfb266f40b41fd88216ccf671f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072424"
---
# <a name="idebugportex2"></a>IDebugPortEx2
此接口使会话调试管理器 (SDM) 控制端口上运行的程序和进程。

## <a name="syntax"></a>语法

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>实施者注意事项
 自定义端口提供程序在实现 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)的同一对象上实现此接口。

## <a name="notes-for-callers"></a>调用方说明
 SDM 在接口[](/cpp/atl/queryinterface)上调用 QueryInterface `IDebugPort2` 以获取此接口。

## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法
 下表显示的方法 `IDebugPortEx2` 。

|方法|说明|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|启动可执行文件。|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|继续执行进程。|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|确定进程是否可以终止。|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|终止进程。|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|获取端口本身的进程 ID。|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|获取与程序节点关联的程序。|

## <a name="remarks"></a>备注
 此接口通常在 SDM 和自定义端口提供商之间是专用的。

 如果需要，调试引擎 (DE) 可以在传递到[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)的[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)接口上查找此接口，并使用[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)启动程序。 但这并不是必需的，并且 DE 可以执行启动请求程序所需的任何操作。

## <a name="requirements"></a>要求
 标头： portpriv

 命名空间： VisualStudio

 程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另请参阅
- [核心接口](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
