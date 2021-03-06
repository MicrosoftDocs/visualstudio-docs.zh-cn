---
description: 获取有关在调试过程中将自动插入的 Office 相关应用程序的信息。
title: GetAutoInsertExtensions 方法
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c4a49942f50a79db604d2363cf2d85762c5ddce5
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223428"
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions 方法
  获取有关在调试过程中将自动插入的 Office 相关应用程序的信息。

 此方法保留供将来使用。

## <a name="syntax"></a>语法

```csharp
HRESULT GetAutoInsertExtensions(
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames
);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*psaExtensionNames*|适用于 Office 的应用程序的扩展名称。|

## <a name="return-value"></a>返回值
 HRESULT 值，指示方法是否已成功完成。

## <a name="remarks"></a>备注
 要插入的每个 Office 应用都作为 Office 应用程序扩展名称返回，这与 **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer** 下的值相对应。 宿主必须在注册表中查找这些值，然后自动插入扩展。
