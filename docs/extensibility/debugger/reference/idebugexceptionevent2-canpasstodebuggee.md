---
description: 确定调试引擎 (DE) 是否支持将此异常传递给执行恢复时正在调试的程序的选项。
title: IDebugExceptionEvent2：： CanPassToDebuggee |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b56996a5fa7cbf3c08842b783aa2d5dfc1131b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152879"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
确定调试引擎 (DE) 是否支持将此异常传递给执行恢复时正在调试的程序的选项。

## <a name="syntax"></a>语法

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>返回值
 返回 `S_OK` (可以将异常传递给程序) 或 `S_FALSE` (无法在) 上传递异常。

## <a name="remarks"></a>备注
 DE 必须具有用于传递到调试对象的默认操作。 IDE 可能会收到 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) 事件并调用 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) 方法，而不调用 `CanPassToDebuggee` 方法。 因此，DE 应具有在上传递异常的默认情况。

## <a name="see-also"></a>另请参阅
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [继续](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
