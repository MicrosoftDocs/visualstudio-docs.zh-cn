---
description: 请求此调试引擎正在调试的所有程序 (取消) ，以便在下一个线程尝试运行时停止执行。
title: IDebugEngine2：： CauseBreak |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a320cbe9f2414de754b5844aa645bffb857568
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093894"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
请求此调试引擎正在调试的所有程序 (取消) ，以便在下一个线程尝试运行时停止执行。

## <a name="syntax"></a>语法

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
 此方法是异步的：调用此方法后，当程序下一次尝试执行时，将发送 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) 事件。

## <a name="see-also"></a>另请参阅
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
