---
description: 创建此类的嵌套枚举器的枚举数。
title: IDebugClassField：： EnumNestedEnums |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b2e0d908c88b82e9ed706ab919050e1f4943df0c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088557"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
创建此类的嵌套枚举器的枚举数。

## <a name="syntax"></a>语法

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>参数
`ppEnum`\
弄返回表示嵌套枚举列表的 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 对象。 如果没有嵌套枚举，则返回 null 值。

## <a name="return-value"></a>返回值
如果成功，则返回 S_OK 或返回 S_FALSE （如果没有嵌套枚举器）。 否则，返回错误代码。

## <a name="remarks"></a>备注
枚举的每个元素都是一个 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) 对象，用于描述嵌套的枚举。

在类中声明的枚举被视为嵌套枚举。 例如，给定：

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

`EnumNestedEnums`方法将返回一个[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)对象，该对象包含一个表示枚举的[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)对象 `NestedEnum` 。

## <a name="see-also"></a>另请参阅
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
