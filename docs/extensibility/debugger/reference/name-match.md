---
description: 选择匹配名称的 case 选项。
title: NAME_MATCH |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NAME_MATCH
helpviewer_keywords:
- NAME_MATCH enumeration
ms.assetid: 3842c417-a3c9-4259-a05f-52b64b829ef6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c093c49745d7fa1b754db020c85a538992de9555
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086477"
---
# <a name="name_match"></a>NAME_MATCH
选择匹配名称的 case 选项。

## <a name="syntax"></a>语法

```cpp
typedef enum { 
   nmNone            = 0,
   nmCaseSensitive   = 1,
   nmCaseInsensitive = 2
} NAME_MATCH;
```

```csharp
public enum NameMatchOptions { 
   nmNone            = 0,
   nmCaseSensitive   = 1,
   nmCaseInsensitive = 2
}
```

## <a name="fields"></a>字段
 `nmNone`\
 未指定任何选项。

 `nmCaseSensitive`\
 指示要匹配的名称是区分大小写的。

 `nmCaseInsensitive`\
 指示要匹配的名称不区分大小写。

## <a name="remarks"></a>备注
 作为参数传递给以下方法：

- [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)

- [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)

- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)

- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)

## <a name="requirements"></a>要求
 标头： sh。h

 命名空间： VisualStudio

 程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>请参阅
- [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)
- [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
