---
description: 检索此线程的堆栈帧的列表。
title: IDebugThread2：： EnumFrameInfo |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7a47371bf9af89ef3f185698ca25a9df99cad4c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053069"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
检索此线程的堆栈帧的列表。

## <a name="syntax"></a>语法

```cpp
HRESULT EnumFrameInfo ( 
   FRAMEINFO_FLAGS        dwFieldSpec,
   UINT                   nRadix,
   IEnumDebugFrameInfo2** ppEnum
);
```

```csharp
int EnumFrameInfo ( 
   enum_FRAMEINFO_FLAGS     dwFieldSpec,
   uint                     nRadix,
   out IEnumDebugFrameInfo2 ppEnum
);
```

## <a name="parameters"></a>参数
`dwFieldSpec`\
中 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) 枚举中的标志的组合，用于指定要填写 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 结构的哪些字段。指定 `FIF_FUNCNAME_FORMAT` 用于将函数名称设置为单个字符串的标志。

`nRadix`\
中格式化枚举器中的数值信息时使用的基数。

`ppEnum`\
弄返回一个 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 对象，该对象包含描述堆栈帧的 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 结构的列表。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
 线程的帧按顺序枚举，当前帧首先枚举，最后枚举最早的帧。

## <a name="see-also"></a>另请参阅
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
