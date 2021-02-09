---
title: IDebugProgramNode2：： GetProgramName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2b8c84f90373743fb94fa0fe7115656642e0384a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898514"
---
# <a name="idebugprogramnode2getprogramname"></a>IDebugProgramNode2::GetProgramName
获取程序的名称。

## <a name="syntax"></a>语法

```cpp
HRESULT GetProgramName (
    BSTR* pbstrProgramName
);
```

```csharp
int GetProgramName (
    out string pbstrProgramName
);
```

## <a name="parameters"></a>parameters
`pbstrProgramName`\
弄返回程序的名称。

## <a name="return-value"></a>返回值
如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
程序的名称与程序的路径并不相同，但程序的名称可能是这样的路径的一部分。

## <a name="example"></a>示例
下面的示例演示如何对 `CProgram` 实现 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 接口的简单对象实现此方法。 `MakeBstr`函数将指定字符串的副本分配为 BSTR。

```cpp
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {
    if (!pbstrProgramName)
        return E_INVALIDARG;

    // Assign the member program name to the passed program name.
    *pbstrProgramName = MakeBstr(m_pszProgramName);
    return NOERROR;
}
```

## <a name="see-also"></a>另请参阅
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
