---
description: 设置作为参数提供的值类的实例的值类对象的实例值。
title: IDebugManagedObject：： SetFromManagedObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6b4038b4f3560b7cd526261f898c01f384421f42
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165211"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
设置作为参数提供的值类的实例的值类对象的实例值。

## <a name="syntax"></a>语法

```cpp
HRESULT SetFromManagedObject( 
   IUnknown* pManagedObject
);
```

```csharp
int SetFromManagedObject(
   object pManagedObject
);
```

## <a name="parameters"></a>参数
`pManagedObject`\
中表示包含新值的托管对象的接口。

## <a name="return-value"></a>返回值
 如果成功，将返回 S_OK;否则，将返回错误代码。

## <a name="remarks"></a>备注
 此方法用于更改 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) 对象所表示的托管对象。

## <a name="see-also"></a>另请参阅
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
