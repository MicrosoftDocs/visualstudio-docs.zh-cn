---
description: 此方法检索允许枚举持久端口列表的对象。
title: IDebugPortSupplier3：： EnumPersistedPorts |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4fe55898f6dbc7713db6e013868b1c7f22a5faf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071956"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
此方法检索允许枚举持久端口列表的对象。

## <a name="syntax"></a>语法

```cpp
HRESULT EnumPersistedPorts(
   BSTR_ARRAY         PortNames,
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPersistedPorts(
   BSTR_ARRAY           PortNames,
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>参数
`PortNames`\
中一个 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) 结构，它包含要在持久端口中查找和返回的端口名称的列表。 仅返回具有这些名称的已保留端口。

`ppEnum`\
弄实现 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) 接口的对象。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
 在实例化端口供应商时加载持久化端口，并在销毁端口供应商时保存。

## <a name="see-also"></a>另请参阅
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)
