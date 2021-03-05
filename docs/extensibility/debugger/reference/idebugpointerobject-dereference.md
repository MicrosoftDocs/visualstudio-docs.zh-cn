---
description: 获取指向的对象。
title: IDebugPointerObject：:D ereference |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e4aa96f726ec18e84aceba159fe9be6128456ce0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169686"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
获取指向的对象。

## <a name="syntax"></a>语法

```cpp
HRESULT DeReference( 
   DWORD          dwIndex,
   IDebugObject** ppObject
);
```

```csharp
int Dereference(
   uint             dwIndex,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>参数
`dwIndex`\
中相对于对象的开头的简单字节偏移量。

`ppObject`\
弄返回一个 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 对象，该对象表示指向的对象，加上偏移量（如果有）。

## <a name="return-value"></a>返回值
 如果成功，将返回 S_OK;否则，将返回错误代码。 如果此对象不指向另一个对象，则返回 E_FAIL。

## <a name="remarks"></a>备注
 指向的对象可以是基元类型，也可以是更复杂的类型，例如类或结构。

## <a name="see-also"></a>另请参阅
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
