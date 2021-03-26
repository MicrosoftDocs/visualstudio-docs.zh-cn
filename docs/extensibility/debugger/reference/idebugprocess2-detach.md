---
description: 通过分离进程中的所有程序，将调试器与此进程分离。
title: IDebugProcess2：:D etach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4d75f9dd58e2a26f6d465fc93988fa3d3785a0d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071657"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
通过分离进程中的所有程序，将调试器与此进程分离。

## <a name="syntax"></a>语法

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
 所有程序和进程都将继续运行，但不再是调试会话的一部分。 分离操作完成后，不会再发送此进程 (的调试事件，) 将发送其程序。

## <a name="see-also"></a>另请参阅
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
