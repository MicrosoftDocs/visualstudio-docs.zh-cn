---
description: 获取系统线程标识符。
title: IDebugThread2：： GetThreadId |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 95dd724310b3aae6e2266d9d18a3846bc9efccf7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164547"
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
获取系统线程标识符。

## <a name="syntax"></a>语法

```cpp
HRESULT GetThreadId (
    DWORD* pdwThreadId
);
```

```csharp
int GetThreadId (
    out uint pdwThreadId
);
```

## <a name="parameters"></a>参数
`pdwThreadId`\
弄返回系统线程标识符。

## <a name="return-value"></a>返回值
如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
线程 ID 用于标识进程中的所有其他线程中的线程。

## <a name="example"></a>示例
下面的示例演示如何对 `CProgram` 实现 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 接口的简单对象实现此方法。

```cpp
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {
    *pdwThreadId = GetCurrentThreadId();
    return NOERROR;
}
```

## <a name="see-also"></a>另请参阅
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
