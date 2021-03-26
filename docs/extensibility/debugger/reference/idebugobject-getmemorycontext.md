---
description: 获取表示对象的值地址的内存上下文。
title: IDebugObject：： GetMemoryContext |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54df34a989d56ac9c1a962943eeda172c90e5554
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081849"
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
获取表示对象的值地址的内存上下文。

## <a name="syntax"></a>语法

```cpp
HRESULT GetMemoryContext( 
   IDebugMemoryContext2** pContext
);
```

```csharp
int GetMemoryContext(
   ref IDebugMemoryContext2 pContext
);
```

## <a name="parameters"></a>参数
`pContext`\
弄返回一个 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) 对象，该对象表示对象的值的地址。

## <a name="return-value"></a>返回值
 如果成功，将返回 S_OK;否则，将返回错误代码。

## <a name="remarks"></a>备注
 返回的内存上下文指定此 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 对象所表示的值的地址。

## <a name="see-also"></a>另请参阅
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
