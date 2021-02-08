---
title: '&lt;&gt; (ClickOnce 部署) 的 assembly 元素 |Microsoft Docs'
description: Assembly 元素是根元素，在 ClickOnce 部署中是必需的。 其第一个包含的元素必须是 assemblyIdentity 元素。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b7838e0a212bbc1e743783255106bb44561fbe62
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837757"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;&gt; (ClickOnce 部署的 assembly 元素) 
部署清单的顶级元素。

## <a name="syntax"></a>语法

```xml

      <assembly  
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>元素和属性
 `assembly`元素为根元素，并且是必需的。 它包含的第一个元素必须是 `assemblyIdentity` 元素。 清单元素必须位于以下命名空间中： `urn:schemas-microsoft-com:asm.v1` 、 `urn:schemas-microsoft-com:asm.v2` 和 `http://www.w3.org/2000/09/xmldsig#` 。 程序集的子元素也必须在这些命名空间中通过继承或标记。

 `assembly` 元素具有以下属性。

|Attribute|说明|
|---------------|-----------------|
|`manifestVersion`|必需。 此特性必须设置为 `1.0` 。|

## <a name="example"></a>示例
 下面的代码示例演示 `assembly` 使用部署的应用程序的部署清单中的元素 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 。 此代码示例是为 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md) 主题提供的更大示例的一部分。

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
```

## <a name="see-also"></a>另请参阅
- [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)
- [\<assembly> 元素](../deployment/assembly-element-clickonce-application.md)