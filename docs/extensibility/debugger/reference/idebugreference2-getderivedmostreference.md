---
description: 获取引用的派生程度最高的引用。
title: IDebugReference2：： GetDerivedMostReference |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c482b05620f280b2948aefe7e95eb38682268c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071436"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
获取引用的派生程度最高的引用。 保留供将来使用。

## <a name="syntax"></a>语法

```cpp
HRESULT GetDerivedMostReference( 
   IDebugReference2** ppDerivedMost
);
```

```csharp
int GetDerivedMostReference( 
   out IDebugReference2 ppDerivedMost
);
```

## <a name="parameters"></a>参数
`ppDerivedMost`\
弄返回表示最常派生的属性的 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 对象。

## <a name="return-value"></a>返回值
 始终返回 `E_NOTIMPL`。

## <a name="remarks"></a>备注
 例如，如果此属性描述一个对象，该对象实现， `ClassRoot` 但它实际上是 `ClassDerived` 派生自的实例 `ClassRoot` ，则此方法将返回表示对该对象的引用的 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 对象 `ClassDerived` 。

## <a name="see-also"></a>另请参阅
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
