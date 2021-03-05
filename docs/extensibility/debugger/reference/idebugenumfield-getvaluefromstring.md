---
description: 此方法返回与枚举常量的名称关联的值。
title: IDebugEnumField：： GetValueFromString |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6a4ab2950667ba9268335f2e0dbca1c0ce5183bc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153295"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
此方法返回与枚举常量的名称关联的值。

## <a name="syntax"></a>语法

```cpp
HRESULT GetValueFromString(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromString(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>参数
`pszValue`\
中一个字符串，指定要获取其值的名称。 请注意，对于 c + +，这是宽字符字符串。

`pValue`\
弄返回关联的数值。

## <a name="return-value"></a>返回值
 如果成功，则返回 `S_OK` ; 否则， `S_FALSE` 如果该名称不是枚举的一部分，则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
 此方法区分大小写。 如果需要使用不区分大小写的搜索 (例如，在名称不区分大小) 写的语言 Visual Basic 中，请使用 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)。

## <a name="see-also"></a>另请参阅
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
