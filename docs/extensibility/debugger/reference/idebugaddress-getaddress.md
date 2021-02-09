---
title: IDebugAddress：： GetAddress |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df4eb1278a0fe436899c1da989c4c63cfa98cac3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853007"
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

## <a name="parameters"></a>parameters
`pAddress`\
[in，out]此方法填充的 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 结构。

## <a name="return-value"></a>返回值
 如果成功，将返回 S_OK;否则，将返回错误代码。

## <a name="remarks"></a>备注
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)结构传递到此方法，然后用适当的信息填充该结构。 如何解释此信息取决于返回的信息类型以及符号处理程序本身。 有关更多详细信息，请参阅 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 。

## <a name="see-also"></a>另请参阅
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
