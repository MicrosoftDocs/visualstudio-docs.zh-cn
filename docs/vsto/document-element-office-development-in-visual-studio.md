---
description: Vstov4 命名空间的 document 元素存储文档级自定义项的特定于自定义项的信息。
title: '&lt;&gt;Visual Studio 中的文档元素 (Office 开发) '
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3563169bd9b567cd974248bf4185cb9bc8a7b022
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221036"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;&gt;Visual Studio 中的文档元素 (Office 开发) 
  `document`命名空间的元素 `vstov4` 存储文档级自定义项的特定于自定义项的信息。

## <a name="syntax"></a>语法

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>元素和属性
 仅对文档级自定义项是必需的。 `document` 元素位于 `vstov4` 命名空间中。 `document` 元素具有以下属性。

|属性|描述|
|---------------|-----------------|
|`solutionId`|必需。 Visual Studio Tools for Office 运行时用于唯一标识文档级解决方案的 GUID。 此值存储为 _AssemblyLocation 自定义文档属性。 有关详细信息，请参阅 [自定义文档属性概述](../vsto/custom-document-properties-overview.md)。|

 `document` 无子元素。

## <a name="document-level-customization-example"></a>文档级自定义项示例

### <a name="description"></a>描述
 下面的代码示例演示 `document` 使用部署的文档级 Office 解决方案中的元素 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 。 此代码示例是 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)中提供的一个更大示例的一部分。

### <a name="code"></a>代码

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>请参阅

- [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)
- [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)
