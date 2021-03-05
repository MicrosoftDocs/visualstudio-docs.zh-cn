---
description: 为此类的基类创建一个枚举器。
title: IDebugClassField：： EnumBaseClasses |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d5ef86e5f4fea89b376404703000c8bd7e861a0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150713"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
为此类的基类创建一个枚举器。

## <a name="syntax"></a>语法

```cpp
HRESULT EnumBaseClasses( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumBaseClasses(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>参数
`ppEnum`\

弄返回一个 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 对象，该对象表示基类的列表。 如果没有基类，则返回 null 值。

## <a name="return-value"></a>返回值
 如果成功，则返回 S_OK，如果 (没有基类，) 则返回 S_SH_NO_BASE_CLASSES `ppEnum` ; 否则，将返回错误代码。

## <a name="remarks"></a>备注
 枚举器对象中的基类按最直接 (或大多数派生) 基类的顺序指定到大多数远程基类。 例如，对于 c + + 类：

```
class Root { }
class Level1 : Root { }
class Level2 : Level1 { }
class MyClass : Level2 { }
```

 枚举将返回顺序为的基类 `Level2` `Level1` `Root` 。

## <a name="see-also"></a>另请参阅
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
