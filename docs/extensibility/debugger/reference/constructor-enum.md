---
title: CONSTRUCTOR_ENUM |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONSTRUCTOR_ENUM
helpviewer_keywords:
- CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3fe47e53b1b95f69c80fd248f59de4cf23bf9c88
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913009"
---
# <a name="constructor_enum"></a>CONSTRUCTOR_ENUM
选择不同类型的构造函数。

## <a name="syntax"></a>语法

```cpp
typedef enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
} CONSTRUCTOR_ENUM;
```

```csharp
public enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
};
```

## <a name="fields"></a>字段
`crAll`\
选择所有构造函数。

`crNonStatic`\
选择非静态构造函数。

`crStatic`\
选择静态构造函数。

## <a name="remarks"></a>备注
作为参数传递给 [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) 方法。

## <a name="requirements"></a>要求
标头： sh。h

命名空间： VisualStudio

程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>请参阅
- [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
