---
description: 此方法获取包含符号当前值的内存上下文或对象。
title: IDebugBinder：： Bind |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 859ee8d474b25533d990c92e4c4f038d2a62f987
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067423"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
此方法获取包含符号当前值的内存上下文或对象。

## <a name="syntax"></a>语法

```cpp
HRESULT Bind( 
   IDebugObject*  pContainer,
   IDebugField*   pField,
   IDebugObject** ppObject
);
```

```csharp
int Bind(
   IDebugObject     pContainer,
   IDebugField      pField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>参数
`pContainer`\
中包含由引用的子级的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) `pField` 。

`pField`\
中表示符号的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 。

`ppObject`\
弄返回 `IDebugObject` 表示符号实例的。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="see-also"></a>另请参阅
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
