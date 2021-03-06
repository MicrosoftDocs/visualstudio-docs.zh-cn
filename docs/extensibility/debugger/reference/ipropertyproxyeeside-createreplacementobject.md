---
description: 创建特定于表达式计算器 (EE) 的数据对象的副本。
title: IPropertyProxyEESide：： CreateReplacementObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 341ca3d00a433c4bb36bc22ab2d598d7b454842a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225703"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
创建特定于表达式计算器 (EE) 的数据对象的副本。

## <a name="syntax"></a>语法

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>参数
`dataIn`\
中包含要复制的数据的 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 对象。

`dataOut`\
弄返回一个新的 `IEEDataStorage` 对象。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
 此方法的 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 对象表示字节数组。 此传入数据对象通常不是由 EE 实现的。 但是，此方法返回的对象始终由 EE 实现，这使 EE 可以 `IEEDataStorage` 在所需的任何类上实现接口。

 请注意，传入对象提供的数据 `IEEDataStorage` 在传出对象中必须是相同的数据 `IEEDataStorage` 。

## <a name="see-also"></a>请参阅
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
