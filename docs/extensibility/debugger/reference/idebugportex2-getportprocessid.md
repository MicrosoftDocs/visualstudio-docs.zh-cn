---
title: IDebugPortEx2：： GetPortProcessId |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a5648fa4b251e96327a35ecf29c2684a312fa99
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929649"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
获取端口本身的进程 ID。

## <a name="syntax"></a>语法

```cpp
HRESULT GetPortProcessId ( 
   DWORD* pdwProcessId
);
```

```csharp
int GetPortProcessId ( 
   out uint pdwProcessId
);
```

## <a name="parameters"></a>parameters
`pdwProcessId`\
弄返回端口本身的物理进程 ID。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
 例如，在 Win32 运行时中，此方法通常会调用 Win32 函数 `GetCurrentProcessId` 以获取物理进程 ID。

## <a name="see-also"></a>另请参阅
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
