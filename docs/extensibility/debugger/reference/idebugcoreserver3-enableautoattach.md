---
description: 为指定的调试引擎启用自动附加。
title: IDebugCoreServer3：： EnableAutoAttach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e3b78744d67183c368345af8c6c26e57edec8d1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058672"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
为指定的调试引擎启用自动附加。

## <a name="syntax"></a>语法

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>参数
`rgguidSpecificEngines`\
中用于标记为自动附加的每个调试引擎的 Guid 数组。

`celtSpecificEngines`\
中在中指定的引擎数 `rgguidSpecificEngines` 。

`pszStartPageUrl`\
中自动附加时要使用的起始 URL。

`pbstrSessionID`\
弄自动附加的会话的 ID。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。 一个错误代码为 `E_AUTO_ATTACH_NOT_REGISTERED` ，指示尚未注册自动附加类工厂。

## <a name="remarks"></a>备注
 当与指定的 URL 关联的程序启动时，将自动启动并附加指定的调试引擎。

## <a name="see-also"></a>另请参阅
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
