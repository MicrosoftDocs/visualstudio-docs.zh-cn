---
description: 指定地址的种类。
title: ADDRESS_KIND |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca55e3de468ed61a3af32ddfe99873b90013aa16
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085502"
---
# <a name="address_kind"></a>ADDRESS_KIND
指定地址的种类。

## <a name="syntax"></a>语法

```cpp
enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
typedef DWORD ADDRESS_KIND;
```

```csharp
public enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
```

## <a name="fields"></a>字段
`ADDRESS_KIND_NATIVE`\
本机地址，由 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) 结构表示。

`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`\
相对于 `this` Visual Basic) 指针中的 (的非托管地址 `Me` ，并由 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) 结构表示。

`ADDRESS_KIND_UNMANAGED_PHYSICAL`\
非托管的物理地址，由 [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) 结构表示。

`ADDRESS_KIND_METHOD`\
类的一种方法，由 [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) 结构表示。

`ADDRESS_KIND_FIELD`\
类的一个字段，由 [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) 结构表示。

`ADDRESS_KIND_LOCAL`\
该地址用于本地变量，由 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) 结构表示。

`ADDRESS_KIND_PARAM`\
方法或函数参数，由 [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) 结构表示。

`ADDRESS_KIND_ARRAYELEM`\
数组元素，由 [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) 结构表示。

`ADDRESS_KIND_RETVAL`\
一个返回值，由 [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) 结构表示。

## <a name="remarks"></a>备注
[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)方法返回[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)结构，该结构包含[DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)结构的可能结构的联合。 `dwKind`结构的字段 `DEBUG_ADDRESS_UNION` 保留 `ADDRESS_KIND` 值，并说明如何解释联合字段。

## <a name="requirements"></a>要求
标头： sh。h

命名空间： VisualStudio

程序集： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>请参阅
- [枚举](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [获取地址](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
