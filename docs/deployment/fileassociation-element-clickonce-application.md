---
title: '&lt;&gt; (ClickOnce 应用程序) 的 fileAssociation 元素 |Microsoft Docs'
description: FileAssociation 元素标识要与应用程序关联的文件扩展名。 FileAssociation 元素是可选的。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1908b4f63edcf90643c28523c0c6ed0d0e11a97
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382723"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;&gt; (ClickOnce 应用程序的 fileAssociation 元素) 
标识与应用程序关联的文件扩展名。

## <a name="syntax"></a>语法

```xml
<fileAssociation
    xmlns="urn:schemas-microsoft-com:clickonce.v1"
    extension
    description
    progid
    defaultIcon
/>
```

## <a name="elements-and-attributes"></a>元素和属性
 `fileAssociation` 元素是可选的。 元素具有以下属性。

|属性|说明|
|---------------|-----------------|
|`extension`|必需。 要与应用程序关联的文件扩展名。|
|`description`|必需。 Shell 使用的文件类型的说明。|
|`progid`|必需。 唯一标识文件类型的名称。|
|`defaultIcon`|必需。 指定用于具有此扩展的文件的图标。 必须在包含此元素的[ \<assembly> 元素](../deployment/assembly-element-clickonce-application.md)内使用[ \<file> 元素](../deployment/file-element-clickonce-application.md)指定图标文件。|

## <a name="remarks"></a>注解
 此元素必须包含对 "urn：架构-microsoft com： clickonce. v1" 的 XML 命名空间引用。 如果 `<fileAssociation>` 使用了元素，则它必须位于 `<application>` 其父[ \<assembly> 元素](../deployment/assembly-element-clickonce-application.md)中的元素之后。

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 不会覆盖现有文件关联。 但是，ClickOnce 应用程序只能重写当前用户的文件扩展名。 卸载 ClickOnce 应用程序之后，ClickOnce 将删除该用户的文件关联，并再次激活每台计算机的关联。

## <a name="example"></a>示例
 下面的代码示例说明了 `fileAssociation` 使用部署的文本编辑器应用程序的应用程序清单中的元素 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 此代码示例还包括属性所需的[ \<file> 元素](../deployment/file-element-clickonce-application.md) `defaultIcon` 。

```xml
<file name="text.ico" size="4286">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>
  </hash>
</file>
<file name="writing.ico" size="9662">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>
  </hash>
</file>
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />
```

## <a name="see-also"></a>请参阅
- [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)