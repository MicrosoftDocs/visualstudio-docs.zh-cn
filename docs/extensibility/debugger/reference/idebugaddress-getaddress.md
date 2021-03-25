---
description: 返回一个结构，该结构描述对象及其在其作用域或容器中的位置。
title: IDebugAddress：： GetAddress |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92e616ded029c22b16b81ccd5f25086b11be6ff4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094389"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
返回一个结构，该结构描述对象及其在其作用域或容器中的位置。

## <a name="syntax"></a>语法

```cpp
HRESULT GetAddress (
   DEBUG_ADDRESS * pAddress
);
```

```csharp
int GetAddress(
   DEBUG_ADDRESS[] pAddress
);
```

## <a name="parameters"></a>参数
`pAddress`\
[in，out]此方法填充的 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 结构。

## <a name="return-value"></a>返回值
 如果成功，将返回 S_OK;否则，将返回错误代码。

## <a name="remarks"></a>备注
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)结构传递到此方法，然后用适当的信息填充该结构。 如何解释此信息取决于返回的信息类型以及符号处理程序本身。 有关更多详细信息，请参阅 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 。

## <a name="see-also"></a>另请参阅
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
