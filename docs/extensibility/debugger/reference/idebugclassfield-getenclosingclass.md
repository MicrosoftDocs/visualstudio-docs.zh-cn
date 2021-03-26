---
description: 获取包含此类的类。
title: IDebugClassField：： GetEnclosingClass |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c59eb2559634c67b210f4fc3b4ce41743346c8ea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088479"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
获取包含此类的类。

## <a name="syntax"></a>语法

```cpp
HRESULT GetEnclosingClass(
    IDebugClassField** ppClassField
);
```

```csharp
int GetEnclosingClass(
    out IDebugClassField ppClassField
);
```

## <a name="parameters"></a>参数
`ppClassField`\
弄返回表示封闭类的 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 对象。 如果没有封闭类，则返回 null 值。

## <a name="return-value"></a>返回值
如果成功，将返回 S_OK;否则，将返回错误代码。

## <a name="remarks"></a>备注
如果此 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 对象表示的类是嵌套类，则 `ppClassField` 参数将返回 `IDebugClassField` 表示封闭类的对象。 例如，给定此类定义：

```
class RootClass {
    class NestedClass { }
};
```

`GetEnclosingClass`在表示类的对象上调用方法将 `IDebugClassField` `NestedClass` 返回一个 `IDebugClassField` 表示类的对象 `RootClass` 。

## <a name="see-also"></a>另请参阅
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
