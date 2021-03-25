---
description: 此方法将文档上下文映射到一个调试地址数组。
title: IDebugSymbolProvider：： GetAddressesFromContext |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e9748e2e2cf7f82724398afe25624f2d1762363c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087127"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
此方法将文档上下文映射到一个调试地址数组。

## <a name="syntax"></a>语法

```cpp
HRESULT GetAddressesFromContext( 
   IDebugDocumentContext2* pDocContext,
   BOOL                    fStatmentOnly,
   IEnumDebugAddresses**   ppEnumBegAddresses,
   IEnumDebugAddresses**   ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromContext(
   IDebugDocumentContext2  pDocContext,
   bool                    fStatmentOnly,
   out IEnumDebugAddresses ppEnumBegAddresses,
   out IEnumDebugAddresses ppEnumEndAddresses
);
```

## <a name="parameters"></a>参数
`pDocContext`\
中文档上下文。

`fStatmentOnly`\
中如果为 TRUE，则将调试地址限制为单个语句。

`ppEnumBegAddresses`\
弄返回与此语句或行关联的起始调试地址的枚举数。

`ppEnumEndAddresses`\
弄返回与此语句或行相关联的结束调试地址的 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) 枚举器。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
 文档上下文通常指示源行的范围。 此方法提供与这些行关联的开始和结束调试地址。 某些语言允许跨多行的语句或包含多个语句的行。 此方法提供用于将调试地址限制为单个语句的标志。

 单个语句可以有多个调试地址，就像在模板中一样。

## <a name="see-also"></a>另请参阅
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
