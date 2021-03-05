---
description: 确定对象是否表示用户数据。
title: IDebugObject2：： IsUserData |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b9264ed546a4f1c9abcf42b1376e0b21b0f27940
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169984"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
确定对象是否表示用户数据。

## <a name="syntax"></a>语法

```cpp
HRESULT IsUserData(
   BOOL* pfUser
);
```

```csharp
int IsUserData(
   out int pfUser
);
```

## <a name="parameters"></a>参数
`pfUser`\
弄 `TRUE` 如果对象表示用户数据，则返回非零 () ; 否则，返回零 (`FALSE`) 。

## <a name="return-value"></a>返回值
 如果成功，将返回 S_OK;否则，将返回错误代码。

## <a name="remarks"></a>备注
 用户数据是指定为 JustMyCode 的模块的一部分的任何对象 (用户可配置的选项，该选项将模块标记为用户代码，因此) 的堆栈跟踪中可见。

## <a name="see-also"></a>另请参阅
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
