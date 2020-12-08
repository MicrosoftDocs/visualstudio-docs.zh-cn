---
title: '&lt;&gt;Visual Studio 中的 d 元素 (Office 开发) '
description: 了解 d 元素如何指示此解决方案不是独立应用程序。
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e8327c6e154f051f5ce79d41ceaa696e330c794f
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848126"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;&gt;Visual Studio 中的 d 元素 (Office 开发) 
  `customHostSpecified`元素指示此解决方案不是独立应用程序。 Office 解决方案包含 Microsoft Office 应用程序内部承载的组件。

## <a name="syntax"></a>语法

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>元素和属性
 `customHostSpecified`元素是 Office 解决方案所必需的。 此元素位于 `co.v1` 命名空间中，并指定此部署包含将在自定义主机内部署的组件，而不是独立应用程序。

 此元素是 `<entrypoint>` 应用程序清单中第一个元素的子元素。 此元素中不能有任何其他子元素， `<entrypoint>` 或者在 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 安装过程中将引发验证错误。

 此元素没有属性和子元素。

## <a name="example"></a>示例
 下面的代码示例演示 `customHostSpecified` Office 解决方案的应用程序清单中的元素。 此代码示例是 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)中提供的一个更大示例的一部分。

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>请参阅

- [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)
- [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)