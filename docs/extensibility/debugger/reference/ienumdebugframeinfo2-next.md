---
description: 返回 FRAMEINFO 枚举中的下一组元素。
title: IEnumDebugFrameInfo2：： Next |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2::Next
helpviewer_keywords:
- IEnumDebugFrameInfo2::Next
ms.assetid: 64a64eeb-5dea-4119-8a22-03771015d1e5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7013d014710423e77e128264b99340cb5b516420
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075453"
---
# <a name="ienumdebugframeinfo2next"></a>IEnumDebugFrameInfo2::Next
返回枚举中的下一个元素集。

## <a name="syntax"></a>语法

```cpp
HRESULT Next(
   ULONG       celt,
   FRAMEINFO** rgelt,
   ULONG*      pceltFetched
);
```

```csharp
int Next(
   uint        celt,
   FRAMEINFO[] rgelt,
   ref uint    pceltFetched
);
```

## <a name="parameters"></a>参数
`celt`\
中要检索的元素的数目。 还指定数组的最大大小 `rgelt` 。

`rgelt`\
[in，out]要填充的 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 元素的数组。

`pceltFetched`\
弄返回中实际返回的元素数 `rgelt` 。

## <a name="return-value"></a>返回值
 如果成功，则返回 `S_OK`。 `S_FALSE`如果返回的元素数少于所请求的数目，则返回; 否则返回错误代码。

## <a name="see-also"></a>另请参阅
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
