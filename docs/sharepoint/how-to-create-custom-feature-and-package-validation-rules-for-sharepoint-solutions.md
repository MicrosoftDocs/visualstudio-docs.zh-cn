---
title: 为 SharePoint 解决方案创建功能和包验证
titleSuffix: ''
description: 创建自定义验证规则以验证 Visual Studio 生成的解决方案包或验证整个功能。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f76abeee6ace851025a29ce6d85b894bf479dfa
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903684"
---
# <a name="create-feature-and-package-validations-for-sharepoint-solutions"></a>为 SharePoint 解决方案创建功能和包验证

  你可以创建自定义验证规则来验证 Visual Studio 生成的解决方案包。 可以通过在 **PackagingExplorer** 的包或功能的上下文菜单中选择 "**验证**"，对整个功能或包执行完全验证。 当你向项目添加新的 SharePoint 项目项或功能以确定包或功能是否处于有效状态时，将执行部分验证。

### <a name="to-create-a-custom-package-validation-rule"></a>创建自定义包验证规则

1. 创建类库项目。

2. 添加对下列程序集的引用：

    - VisualStudio

    - System.ComponentModel.Composition

3. 创建实现以下接口之一的类：

    - 若要创建包验证规则，请实现 <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> 接口。

    - 若要创建功能验证规则，请实现 <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> 接口。

4. 将添加 <xref:System.ComponentModel.Composition.ExportAttribute> 到类。 此属性使 Visual Studio 能够发现和加载验证规则。 将 <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> 或 <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> 类型传递给特性构造函数。

## <a name="example"></a>示例
 下面的代码示例演示如何创建自定义功能验证规则。

 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]

## <a name="compile-the-code"></a>编译代码
 此示例需要引用以下程序集：

- VisualStudio。

- System.componentmodel。

## <a name="deploy-the-extension"></a>部署扩展
 若要部署该扩展，请为 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 该程序集创建一个扩展 (VSIX) 包，并为您要使用该扩展分发的任何其他文件创建该扩展。 有关详细信息，请参阅 [在 Visual Studio 中部署 SharePoint 工具扩展](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。

## <a name="see-also"></a>另请参阅
- [扩展 SharePoint 打包和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
