---
title: '&lt;postActionData &gt; 元素 (Office 开发) '
description: Vstav3 命名空间的 postActionData 元素指定与任何部署后操作关联的数据，这些操作在 Office 解决方案安装后运行。
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a75f61c6d1f80a127f49d96c4e3f4910c66dd8aa
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470061"
---
# <a name="ltpostactiondatagt-element-office-development"></a>&lt;postActionData &gt; 元素 (Office 开发) 
  `postActionData` 命名空间的 `vstav3` 元素指定与任何部署后操作关联的数据，这些操作在 Office 解决方案安装后运行。

## <a name="syntax"></a>语法

```xml
<postActionData>
</postActionData>
```

## <a name="elements-and-attributes"></a>元素和属性
 `postActionData` 元素是可选的且位于 `vstav3` 命名空间中。 每个部署后操作的应用程序清单中只定义了一个 `postActionData` 元素。

 `postActions` 元素没有属性。

 `postActions` 无子元素。

## <a name="post-deployment-action-example"></a>部署后操作示例

### <a name="description"></a>说明
 下面的代码示例演示 Office 解决方案的应用程序清单中的 `postAction` 元素，该解决方案是使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]部署的。 此代码示例是 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)中提供的一个更大示例的一部分。

### <a name="code"></a>代码

```xml
<vstav3:postActionData>
  data in any format
</vstav3:postActionData>
```

## <a name="see-also"></a>请参阅

- [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)
- [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)
