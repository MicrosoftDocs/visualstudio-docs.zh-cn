---
description: 根据给定的指标名称检索表达式计算器本地对象。
title: IDebugSettingsCallback2：： GetEELocalObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEELocalObject
ms.assetid: e69a3469-a049-420c-b918-c48a1e7b9baf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72ff072cdb6c0431a7b04e644f71186c91763efa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168759"
---
# <a name="idebugsettingscallback2geteelocalobject"></a>IDebugSettingsCallback2::GetEELocalObject
根据给定的指标名称检索表达式计算器本地对象。

## <a name="syntax"></a>语法

```cpp
HRESULT GetEELocalObject(
   REFGUID     guidLang,
   REFGUID     guidVendor,
   LPCWSTR     pszMetric,
   IUnknown ** ppUnk
);
```

```csharp
private int GetEELocalObject(
   ref Guid          guidLang,
   ref Guid          guidVendor,
   string            pszMetric,
   out System.Object ppUnk
);
```

## <a name="parameters"></a>参数
`guidLang`\
中编程语言的唯一标识符。

`guidVendor`\
中供应商的唯一标识符。

`pszMetric`\
中度量值的名称。

`ppUnk`\
弄返回表达式计算器本地对象。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="see-also"></a>另请参阅
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
