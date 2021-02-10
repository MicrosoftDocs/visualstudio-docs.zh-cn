---
title: marker_importance 枚举 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_importance
helpviewer_keywords:
- Concurrency, diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1559dc6c5aa24c54465aee6d29f0745be6c897c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917821"
---
# <a name="marker_importance-enumeration"></a>marker_importance 枚举
表示并发可视化工具标记的重要性级别。

## <a name="syntax"></a>语法

```cpp
enum marker_importance;
```

## <a name="members"></a>成员

### <a name="values"></a>值

|“属性”|描述|
|----------|-----------------|
|`critical_importance`|指定该标记具有关键重要性。|
|`high_importance`|指定该标记具有高重要性。|
|`low_importance`|指定该标记具有低重要性。|
|`normal_importance`|指定该标记具有普通重要性。|

## <a name="requirements"></a>要求
 **Header:** *cvmarkersobj.h*

 **命名空间：** Concurrency::diagnostic

## <a name="see-also"></a>请参阅
- [diagnostic 命名空间](../profiling/diagnostic-namespace.md)