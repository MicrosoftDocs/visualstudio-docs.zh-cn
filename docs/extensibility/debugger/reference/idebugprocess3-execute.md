---
description: 继续从停止状态运行此进程。 任何以前的执行状态 (例如步骤) 会被清除，该进程将再次开始执行。
title: IDebugProcess3：： Execute |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e81efa2bec718899dba01181ccc691040cd4cf2b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081589"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
继续从停止状态运行此进程。 任何以前的执行状态 (例如步骤) 会被清除，该进程将再次开始执行。

> [!NOTE]
> 应使用此方法，而不是 [执行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)。

## <a name="syntax"></a>语法

```cpp
HRESULT Execute(
   IDebugThread2* pThread
);
```

```csharp
int Execute(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>参数
`pThread`\
中表示要执行的线程的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 对象。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
 当用户在某个其他进程的线程中从停止状态开始执行时，将在此过程中调用此方法。 当用户从 IDE 的 "**调试**" 菜单中选择 "**启动**" 命令时，也会调用此方法。 此方法的实现可能与在进程的当前线程上调用 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) 方法一样简单。

> [!WARNING]
> 处理此调用时，不要将停止事件或立即 (同步) 事件发送到 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ;否则，调试器可能会停止响应。

## <a name="see-also"></a>另请参阅
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [恢复](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
