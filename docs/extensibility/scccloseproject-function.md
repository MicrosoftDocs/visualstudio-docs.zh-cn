---
description: 此函数关闭项目，并标记特定会话的结束。
title: SccCloseProject 函数 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 859b1ddea99e74cc1c1dec999611e50216c3c98a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904690"
---
# <a name="scccloseproject-function"></a>SccCloseProject 函数
此函数关闭项目，并标记特定会话的结束。

## <a name="syntax"></a>语法

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>参数
 pvContext 源代码管理插件上下文结构。

## <a name="return-value"></a>返回值
 此函数的源代码管理插件实现应返回以下值之一：

|值|描述|
|-----------|-----------------|
|SCC_OK|项目已成功关闭。|
|SCC_E_PROJNOTOPEN|当前未打开任何项目。|
|SCC_E_NOTAUTHORIZED|不允许用户执行此操作。|
|SCC_E_NONSPECIFICERROR|非特定故障。|

## <a name="remarks"></a>备注
 始终在此函数之前调用 [SccOpenProject](../extensibility/sccopenproject-function.md) 。 然后，对此函数的调用随后将调用 `SccOpenProject` 函数或 [SccUninitialize](../extensibility/sccuninitialize-function.md)，这会完全结束与源代码管理系统的连接。

## <a name="see-also"></a>另请参阅
- [源代码管理插件 API 函数](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
