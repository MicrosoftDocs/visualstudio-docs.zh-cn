---
title: 如何：以编程方式按名称检索文件夹
description: 了解如何使用 Visual Studio 以编程方式按名称检索文件夹，然后显示该文件夹的内容。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], retrieving by name
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c05f8bc0174807a5336a9d9f79ac3dc81e87476e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953872"
---
# <a name="how-to-programmatically-retrieve-a-folder-by-name"></a>如何：以编程方式按名称检索文件夹
  此示例获取对命名的自定义文件夹的引用，然后显示该文件夹的内容。

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>示例
 [!code-csharp[Trin_OL_GetFolderName#1](../vsto/codesnippet/CSharp/Trin_OL_GetFolderName/thisaddin.cs#1)]

## <a name="compile-the-code"></a>编译代码
 此示例需要：

- 名为 TestFolder 的文件夹。

## <a name="see-also"></a>另请参阅
- [使用文件夹](../vsto/working-with-folders.md)
- [如何：以编程方式在特定文件夹中搜索](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [如何：以编程方式搜索特定联系人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [如何：以编程方式创建自定义文件夹项](../vsto/how-to-programmatically-create-custom-folder-items.md)
