---
description: 此接口使表达式计算器 (EE) 对值类实例调用属性或方法 (例如，System.object) 并设置其值，而无需对正在调试的程序调用计算。
title: IDebugManagedObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7cb90893ab39a95dd3bd8046d8ba61a32064ccf7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165212"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> 在 Visual Studio 2015 中，不推荐使用这种实现表达式计算器的方式。 有关实现 CLR 表达式计算器的信息，请参阅 [Clr 表达式计算器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 和 [托管表达式计算器示例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此接口使表达式计算器 (EE) 对值类实例调用属性或方法 (例如， `System.Decimal`) 并设置它们的值，而无需对正在调试的程序调用 [计算](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) 。

## <a name="syntax"></a>语法

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>实施者注意事项
 表达式计算器实现此接口来表示托管代码对象（如变量）。

## <a name="notes-for-callers"></a>调用方说明
 若要获取此接口，请对表示值类的实例的[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)调用[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) 。

## <a name="methods-in-vtable-order"></a>Vtable 顺序中的方法
 除了从 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)继承的方法之外，接口还 `IDebugManagedObject` 公开以下方法。

|方法|说明|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|返回一个接口，该接口表示托管代码对象，可以从该对象获取任何适当的托管代码接口。|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|将此对象的值设置为指定的托管代码对象的值。|

## <a name="remarks"></a>备注
 表达式计算器使用此接口将托管代码对象存储在分析树中。

## <a name="requirements"></a>要求
 标头： ee。h

 命名空间： VisualStudio

 程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另请参阅
- [表达式计算接口](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [评估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
