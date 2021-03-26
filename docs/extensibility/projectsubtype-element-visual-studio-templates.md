---
title: " (Visual Studio 模板) 的 ProjectSubType 元素 |Microsoft Docs"
description: 了解 ProjectSubType 元素以及它如何将模板分类为 ProjectType 元素中指定的值的子类别。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 02dd5573de12e4626c267fa014f6c7fc8f243b72
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068669"
---
# <a name="projectsubtype-element-visual-studio-templates"></a> (Visual Studio 模板的 ProjectSubType 元素) 
将模板分类为元素中指定的值的子类别 `ProjectType` 。

 \<VSTemplate> \<TemplateData>
 \<ProjectSubType>

## <a name="syntax"></a>语法

```xml
<ProjectSubType> SubType </ProjectSubType>
```

## <a name="attributes-and-elements"></a>特性和元素
 以下各部分描述了特性、子元素和父元素。

### <a name="attributes"></a>特性
 无。

### <a name="child-elements"></a>子元素
 无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必需的元素。<br /><br /> 将此模板分类并定义此模板在 **“新建项目”** 或 **“添加新项”** 对话框中的显示方式。|

## <a name="text-value"></a>文本值
 需要一个文本值。

 此值指定模板的子类别。

## <a name="remarks"></a>备注
 `ProjectSubType` 是 `TemplateData` 的可选子元素。

 `ProjectSubType`元素为[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)元素提供子类别。 此值可以包括：

- `SmartDevice-NETCFv1`：指定模板面向 [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] 版本1.0。

- `SmartDevice-NETCFv2`：指定模板面向 [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] 版本2.0。

  如果模板包含值为 `ProjectType` 的元素 `Web` ，则 `ProjectSubType` 元素指定模板的编程语言。 此元素可具有以下值：

- `CSharp`：指定模板创建 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Web 项目或项。

- `VisualBasic`：指定模板创建 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Web 项目或项。

## <a name="example"></a>示例
 下面的示例显示针对 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 版本2.0 的设备应用程序的项目模板的元数据 [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] 。

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic device template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>请参阅
- [Visual Studio 模板架构参考](../extensibility/visual-studio-template-schema-reference.md)
- [创建项目和项模板](../ide/creating-project-and-item-templates.md)
- [ (Visual Studio 模板的 ProjectType 元素) ](../extensibility/projecttype-element-visual-studio-templates.md)
