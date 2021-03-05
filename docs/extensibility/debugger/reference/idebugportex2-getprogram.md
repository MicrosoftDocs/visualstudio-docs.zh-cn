---
description: 获取与程序节点关联的程序。
title: IDebugPortEx2：： GetProgram |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetProgram
helpviewer_keywords:
- IDebugPortEx2::GetProgram
ms.assetid: cd83a111-bfd5-4eae-b576-526466c6b6ec
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5bb169ecdbd0dcea188054c96af06da609edf3f7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142799"
---
# <a name="idebugportex2getprogram"></a>IDebugPortEx2::GetProgram
获取与程序节点关联的程序。

## <a name="syntax"></a>语法

```cpp
HRESULT GetProgram( 
   IDebugProgramNode2* pProgramNode,
   IDebugProgram2**    ppProgram
);
```

```csharp
int GetProgram( 
   IDebugProgramNode2 pProgramNode,
   out IDebugProgram2 ppProgram
);
```

## <a name="parameters"></a>参数
`pProgramNode` 中表示程序节点的 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 对象。

`ppProgram` 弄返回一个 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 对象，该对象表示与程序节点关联的程序。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="see-also"></a>另请参阅
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
