---
title: IDebugModule3：： IsUserCode |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c8b313ecdbc1168238bad517f34350a420fb30ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929766"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
检索有关该模块是否表示用户代码的信息。

## <a name="syntax"></a>语法

```cpp
HRESULT IsUserCode(
   BOOL* pfUser
);
```

```csharp
int IsUserCode(
   out int pfUser
);
```

## <a name="parameters"></a>parameters
`pfUser`\
弄 `TRUE` 如果 module 表示用户代码，则为非零 ()  () ，则为零 `FALSE` 。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="see-also"></a>另请参阅
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
