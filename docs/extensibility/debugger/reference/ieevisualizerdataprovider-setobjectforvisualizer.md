---
description: 此方法更改可视化工具表示的对象。
title: IEEVisualizerDataProvider：： SetObjectForVisualizer |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e0a59c10293d5d8cc13d46b625a7b43136cb71b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091794"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
此方法更改可视化工具表示的对象。

## <a name="syntax"></a>语法

```cpp
HRESULT SetObjectForVisualizer(
   IDebugObject*  pNewObject,
   BSTR*          error,
   IDebugObject** pException
);
```

```csharp
int SetObjectForVisualizer(
   IDebugObject     pNewObject,
   out string       error,
   out IDebugObject pException
);
```

## <a name="parameters"></a>参数
`pNewObject`\
中要设置的对象。

`error`\
弄如果设置对象时出现错误，则此字符串将保存错误消息。

`pException`\
弄如果出现错误，则此对象将保存异常信息。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
 由实施者决定如何返回错误信息。 但是，某些调用方可能仅查看是否返回了异常对象以知道是否有错误，因此，如果出现错误，此方法应始终返回异常对象。 如果调用方想要使用错误字符串，则还应提供它。

## <a name="see-also"></a>另请参阅
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
