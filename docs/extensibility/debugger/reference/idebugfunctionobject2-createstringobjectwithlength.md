---
title: IDebugFunctionObject2：： CreateStringObjectWithLength |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6dd46d7cc2d142b3c62ab7b1b2b9eb65b92d6754
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921038"
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
创建一个具有指定长度的字符串对象。

## <a name="syntax"></a>语法

```cpp
HRESULT CreateStringObjectWithLength (
   LPCOLESTR      pcstrString,
   UINT           uiLength,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObjectWithLength (
   string           pcstrString,
   uint             uiLength,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>parameters
`pcstrString`\
中字符串对象的字符串值。

`uiLength`\
中字符串的长度（以字节为单位）。

`ppObject`\
弄返回一个 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 对象，该对象表示新创建的字符串对象。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="see-also"></a>另请参阅
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
