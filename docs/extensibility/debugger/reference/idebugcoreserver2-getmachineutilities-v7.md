---
description: 此方法获取服务器的计算机实用程序。
title: IDebugCoreServer2：： GetMachineUtilities_V7 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26d2c042c6f4a08acb7efc558bbc86021b16587e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077949"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
此方法获取服务器的计算机实用程序。

> [!NOTE]
> 此方法已过时： [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] `E_NOTIMPL` 如果) 调用此方法，请不要使用 (总是返回。 由于历史原因，将保留它。

## <a name="syntax"></a>语法

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>参数
`ppUtil`\
弄返回 `IDebugMDMUtil2_V7` 表示计算机实用工具信息的接口。

## <a name="return-value"></a>返回值
 始终返回 `E_NOTIMPL` ，指示未实现该方法。

## <a name="remarks"></a>备注
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]`E_NOTIMPL`如果调用此方法，则始终返回。

## <a name="see-also"></a>另请参阅
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
