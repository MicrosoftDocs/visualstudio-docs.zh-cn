---
description: 获取物理上包含引用值的内存字节数。
title: IDebugReference2：： GetMemoryBytes |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetMemoryBytes
helpviewer_keywords:
- IDebugReference2::GetMemoryBytes
ms.assetid: 2006cb2b-1dfa-4a2d-8e3e-db2ce0302e0d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f8d5e12b5c26bb5216fdba173dcc4cbb284f27d7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151358"
---
# <a name="idebugreference2getmemorybytes"></a>IDebugReference2::GetMemoryBytes
获取物理上包含引用值的内存字节数。 留待将来使用。

## <a name="syntax"></a>语法

```cpp
HRESULT GetMemoryBytes ( 
   IDebugMemoryBytes2** ppMemoryBytes
);
```

```csharp
int GetMemoryBytes ( 
   out IDebugMemoryBytes2 ppMemoryBytes
);
```

## <a name="parameters"></a>参数
`ppMemoryBytes`\
弄返回一个 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) 对象，该对象可用于检索包含引用值的内存。

## <a name="return-value"></a>返回值
 始终返回 `E_NOTIMPL`。

## <a name="see-also"></a>另请参阅
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
