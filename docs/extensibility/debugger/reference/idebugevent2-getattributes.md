---
description: 获取此调试事件的特性。
title: IDebugEvent2：： GetAttributes |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b41e3f50b73c16c9acb28a809b8c33b535370c47
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065848"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
获取此调试事件的特性。

## <a name="syntax"></a>语法

```cpp
HRESULT GetAttribute( 
   DWORD* pdwAttrib
);
```

```csharp
int GetAttribute( 
   out uint pdwAttrib
);
```

## <a name="parameters"></a>参数
`pdwAttrib`\
弄 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) 枚举中的标志的组合。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)接口对所有事件都是通用的。 此方法描述事件的类型;例如，事件是同步的还是异步的，并且是停止事件。

## <a name="see-also"></a>另请参阅
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
