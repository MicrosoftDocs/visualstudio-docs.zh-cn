---
description: 确定字段是否表示闭合类型。
title: IDebugExtendedField：： IsClosedType |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ba4c55b53ebb1f1e5ad2000f31efc8a37f81eef
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077195"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
确定字段是否表示闭合类型。

## <a name="syntax"></a>语法

```cpp
HRESULT IsClosedType(
   void
);
```

```csharp
int IsClosedType();
```

## <a name="return-value"></a>返回值
 如果该字段为关闭类型，则返回 `S_OK` ; 否则返回 `S_FALSE` 。

## <a name="see-also"></a>另请参阅
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
