---
description: IDebugFunctionObject：：计算调用函数并将生成的值作为对象返回。
title: IDebugFunctionObject：：求值 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d15cdb09de32edcdf6159567db12e05cffd06e7e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160103"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
调用函数并将生成的值作为对象返回。

## <a name="syntax"></a>语法

```cpp
HRESULT Evaluate( 
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate(
   IDebugObject[]   ppParams,
   IntPtr           dwParams,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>参数
`ppParams`\
中表示输入参数的 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 对象的数组。 其中每个参数都是用 `Create` [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 接口中的一个方法创建的。

`dwParams`\
中数组中参数的数目 `ppParams` 。

`dwTimeout`\
中指定从此方法返回之前要等待的最长时间（以毫秒为单位）。 使用 `INFINITE` 无限期等待。

`ppResult`\
弄返回一个 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ，它表示函数的值作为对象。

## <a name="return-value"></a>返回值
 如果成功，将返回 S_OK;否则，将返回错误代码。

## <a name="remarks"></a>备注
 此方法设置并执行对 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 对象所表示的函数的调用。

## <a name="see-also"></a>另请参阅
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
