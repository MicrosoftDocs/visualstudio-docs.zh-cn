---
title: IDebugProviderProgramNode2：： UnmarshalDebuggeeInterface |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1449141885a51b3557f8c626b309fcc64c7fb268
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909838"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
跨进程边界获取指定接口。

## <a name="syntax"></a>语法

```cpp
HRESULT UnmarshalDebuggeeInterface(
   REFIID riid,
   void** ppvObject
);
```

```csharp
int UnmarshalDebuggeeInterface(
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>parameters
`riid`\
中要获取的接口的 GUID。

`ppvObject`\
弄返回实现所需接口的对象。 [C + +] 这可以直接强制转换为所需的接口类型。 [C #] 使用 <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> 方法获取所需的接口。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
 当调试引擎正在 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 进程空间中运行并且正在调试的程序在其自己的进程空间中运行时，将使用此方法。

## <a name="see-also"></a>另请参阅
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
