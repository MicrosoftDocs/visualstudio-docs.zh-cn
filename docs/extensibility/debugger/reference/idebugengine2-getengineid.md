---
description: 获取调试引擎 (DE) 的 GUID。
title: IDebugEngine2：： GetEngineID |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bf785c906303bab677adadfd081ae6af276a754c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153971"
---
# <a name="idebugengine2getengineid"></a>IDebugEngine2::GetEngineID
获取调试引擎 (DE) 的 GUID。

## <a name="syntax"></a>语法

```cpp
HRESULT GetEngineID(
    GUID* pguidEngine
);
```

```csharp
int GetEngineID(
    out Guid pguidEngine
);
```

## <a name="parameters"></a>参数
`pguidEngine`\
弄返回已取消的的 GUID。

## <a name="return-value"></a>返回值
如果成功， `S_OK` 则返回; 否则返回错误代码。

## <a name="remarks"></a>备注
典型 Guid 的一些示例包括 `guidScriptEng` 、 `guidNativeEng` 或 `guidSQLEng` 。 新的调试引擎将创建自己的用于标识的 GUID。

## <a name="example"></a>示例
下面的示例演示如何对 `CEngine` 实现 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 接口的简单对象实现此方法。

```cpp
HRESULT CEngine::GetEngineId(GUID *pguidEngine) {
    if (pguidEngine) {
        // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.
        // Other languages would require their own guidDifferentEngine to be
        //defined in the Batdbg.idl file.
        *pguidEngine = guidBatEng;
        return NOERROR; // This is typically S_OK.
    } else {
        return E_INVALIDARG;
    }
}
```

## <a name="see-also"></a>另请参阅
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
