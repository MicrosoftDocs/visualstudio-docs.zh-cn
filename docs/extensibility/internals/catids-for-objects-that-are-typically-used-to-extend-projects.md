---
title: 通常用于扩展项目的对象的 Catid
description: '了解用于扩展 Visual Basic、Visual c # 和 Visual C++ 项目的项目和项目项自动化对象的对象的 Catid。'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 276e7f146858c2de166c0ba20063a0bf4d8b88a0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086087"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>通常用于扩展项目的对象的 Catid
下表列出了用于扩展 `Project` `ProjectItem` [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 、 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 和项目的和自动化对象的 catid [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 。 这些 Catid 在 *VSLangProj* 中定义。

## <a name="listing-of-catids"></a>Catid 列表

|名称|GUID|
|----------|----------|
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614-D0D5-11D2-8599-006097C68E81}|
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615-D0D5-11D2-8599-006097C68E81}|

## <a name="visual-basic-catids"></a>Visual Basic Catid
 下表列出了用于扩展浏览对象的 Catid [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 。 它们都是在 *VSLangProj. .olb* 中定义的。

|名称|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FDC879-C32A-4751-4835-0B3824BD575F}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11-14EB-489b-87F0-F01C52AF3870}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D-3C72-40A5-95A0-28A2773311CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932DC619-2EAA-4192-B7E6-3D15AD31DF49}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812-8191-4e81-B7B3-174045AB0CB5}|

## <a name="visual-c-catids"></a>Visual c # Catid
 以下 Catid 可用于扩展 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 浏览对象。 它们都是在 *VSLangProj. .olb* 中定义的。

|名称|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003-DE95-4d60-96B0-212979F2A857}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12CE10A-227F-4963-ADB6-3A43388513CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF-ED4E-48B0-8C7B-C74EF0735451}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278-054A-45DB-BF9E-5F22484CC84C}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27}|

## <a name="c-catids"></a>C + + Catid
 以下 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 项目系统 catid 在 .net 2003 的类型库中未公开 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，每当需要扩展这些项目对象时，必须将其包含在代码中。 这些 Catid 将包含在更高版本的类型库中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

|名称|GUID|
|----------|----------|
|`CVCProjectNode`|{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFolderNode`|{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFileNode`|{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|

 下面的代码示例演示如何在代码中对这些 Catid 进行编程。

```
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
```

 以下 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 项目系统 catid 也不会在 .net 2003 的类型库中公开 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，每当需要扩展这些项目对象时，必须将其包含在代码中。 这些 Catid 仅在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .net 2003 中提供，并且在的更高版本中将不可用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

|名称|GUID|
|----------|----------|
|`CVCAssemblyReferenceNode`|{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCProjectReferenceNode`|{593DCFCE-20A7-48e4-ACA1-49ADE9049887}|
|`CVCActiveXReferenceNode`|{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}|
|`CVCReferences`|{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|

 下面的代码示例演示如何在代码中对这些 Catid 进行编程：

```
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
```

 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 下表显示了和项目类型的 guid。

| 项目类型 | GUID |
| - | - |
| [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] | {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} |
| [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] | {F184B08F-C81C-45F6-A57F-5ABD9991F28F} |

## <a name="see-also"></a>另请参阅
- [添加项目和项目项模板](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [注册项目和项模板](../../extensibility/internals/registering-project-and-item-templates.md)
