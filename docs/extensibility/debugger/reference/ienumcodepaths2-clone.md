---
description: 以单独的对象的形式返回当前代码路径枚举的副本。
title: IEnumCodePaths2：： Clone |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Clone
helpviewer_keywords:
- IEnumCodePaths2::Clone
ms.assetid: 9d5c6bc6-7e72-4f1b-801c-7192458f3ba8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b45c31a8271da7a42ed8b254dd89b732c825f29e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086698"
---
# <a name="ienumcodepaths2clone"></a>IEnumCodePaths2::Clone
以单独的对象的形式返回当前枚举的副本。

## <a name="syntax"></a>语法

```cpp
HRESULT Clone(
   IEnumCodePaths2** ppEnum
);
```

```csharp
int Clone(
   out IEnumCodePaths2 ppEnum
);
```

## <a name="parameters"></a>参数
`ppEnum`\
弄以单独的对象的形式返回此枚举的副本。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
 调用此方法时，该枚举的副本具有与原始的相同的状态。 但是，副本的和原始状态是独立的，可以单独更改。

## <a name="see-also"></a>另请参阅
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
