---
description: 此方法告知调试引擎 JustMyCode 状态信息。
title: IDebugEngine3：： SetJustMyCodeState |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e527dbaeb9c04171bf26ea00e550eac336ac6a8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066114"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
此方法告知调试引擎 JustMyCode 状态信息。

## <a name="syntax"></a>语法

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

## <a name="parameters"></a>参数
`fUpdate`\
中非零 (`TRUE`) 更新当前信息，零 (`FALSE`) 重置所有信息 (忽略之前设置) 的任何信息。

`dwModules`\
中中的信息结构数 `rgJMCSpec.`

`rgJMCSpec`\
中要使用的 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) 结构的数组。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
 JustMyCode 是仅调试属于用户的代码，并忽略所有中间代码（如系统代码）的概念，即使源代码可用于该系统代码也是如此。

## <a name="see-also"></a>另请参阅
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
