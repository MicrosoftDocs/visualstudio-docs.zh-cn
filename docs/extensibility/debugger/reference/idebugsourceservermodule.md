---
description: 表示 PDB 文件中包含的源服务器信息。
title: IDebugSourceServerModule |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b12e93d52fe841b66baae341a6854e0217dcb00
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071163"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
表示 PDB 文件中包含的源服务器信息。

## <a name="syntax"></a>语法

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>实施者注意事项
 此接口由调试器引擎实现并由调试器 UI 使用。

## <a name="methods"></a>方法
 下表显示的方法 `IDebugSourceServerModule` 。

|方法|说明|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|检索源服务器信息的数组。|

## <a name="requirements"></a>要求
 标头： Msdbg

 命名空间： VisualStudio

 程序集： Microsoft.VisualStudio.Debugger.Interop.dll
