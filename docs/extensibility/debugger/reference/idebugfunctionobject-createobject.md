---
title: IDebugFunctionObject：： CreateObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e6085e974f58346eba7b38e76e5588b34fc3ff2c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929976"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
使用构造函数创建对象。

## <a name="syntax"></a>语法

```cpp
HRESULT CreateObject( 
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject(
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   out IDebugObject     ppObject
);
```

## <a name="parameters"></a>parameters
`pConstructor`\
中一个 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 对象，表示要创建的对象的构造函数。

`dwArgs`\
中数组中参数的数目 `pArg` 。 表示传递给构造函数的参数的数目。

`pArg`\
中 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 对象的数组，这些对象表示传递给构造函数的参数。

`ppObject`\
弄返回一个， `IDebugObject` 它表示新创建的对象。

## <a name="return-value"></a>返回值
 如果成功，将返回 S_OK;否则，将返回错误代码。

## <a name="remarks"></a>备注
 调用此方法可创建一个对象，该对象表示类 (或其他复杂类型的实例，该实例需要构造函数) 该构造函数由 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 接口表示。

 如果对象参数不需要构造函数，请调用 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) 方法。

## <a name="see-also"></a>另请参阅
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
