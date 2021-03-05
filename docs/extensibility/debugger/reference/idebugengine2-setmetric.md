---
description: 此方法设置名为指标的注册表值。
title: IDebugEngine2：： SetMetric |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 129067ab94c433b7c4b09e29c65d75df98ce6b68
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153880"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
此方法设置名为指标的注册表值。

## <a name="syntax"></a>语法

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

## <a name="parameters"></a>参数
`pszMetric`\
中指标名称。

`varValue`\
中指定指标值。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
 指标是用于更改调试引擎的行为或公布支持的功能的注册表值。 此方法可以将调用转发到 [用于调试函数的 SDK 帮助](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 器的适当形式 `SetMetric` 。

## <a name="see-also"></a>另请参阅
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [用于调试的 SDK 帮助程序](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
