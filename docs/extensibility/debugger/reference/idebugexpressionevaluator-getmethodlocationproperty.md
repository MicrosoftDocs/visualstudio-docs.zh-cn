---
description: 此方法将方法位置和偏移量转换为内存地址。
title: IDebugExpressionEvaluator：： GetMethodLocationProperty |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ddc9c17b90be6d65786d58ff2bf585461c4fc69f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092184"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
此方法将方法位置和偏移量转换为内存地址。

## <a name="syntax"></a>语法

```cpp
HRESULT GetMethodLocationProperty( 
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodLocationProperty(
   string               upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>参数
`upstrFullyQualifiedMethodPlusOffset`\
中表示为字符串的方法位置和偏移量。

`pSymbolProvider`\
中表示为 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 对象的符号提供程序。

`pAddress`\
中方法中的一个地址，以 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 对象的形式表示。

`pBinder`\
中表示为 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 对象的联编程序。

`ppProperty`\
弄返回表示内存地址的 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 接口。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
 返回的地址可用于设置断点，例如。

 不管名称 `upstrFullyQualifiedMethodPlusOffset` 如何，都可以向此参数传递部分限定的方法名称。 在这种情况下，所选方法是括起来的方法 `pAddress` 。 如何解释此参数取决于表达式计算器的实现以及它所支持的语言。

## <a name="see-also"></a>另请参阅
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
