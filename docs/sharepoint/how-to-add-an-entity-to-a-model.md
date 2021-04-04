---
title: 如何：向模型添加实体 |Microsoft Docs
description: 通过将实体控件从 Visual Studio 工具箱添加到业务数据连接 (BDC) 设计器，将实体添加到模型。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 94d34e6a623438cd0e2d63d74ee2321841a0582a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216769"
---
# <a name="how-to-add-an-entity-to-a-model"></a>如何：向模型添加实体
  若要创建实体，请将 Visual Studio **工具箱** 中的实体控件添加到业务数据连接 (BDC) 设计器中。

### <a name="to-add-an-entity-to-the-model"></a>向模型添加实体

1. 创建 BDC 项目，或打开现有的 BDC 项目。 有关详细信息，请参阅[创建业务数据连接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。

2. 在 " **工具箱**" 的 " **BusinessDataCatalog** " 组中，将 " **实体** " 控件添加到设计器上。

     新实体将显示在设计器上。 Visual Studio 将一个 `<Entity>` 元素添加到项目中 BDC 模型文件的 XML 中。 有关实体元素特性的详细信息，请参阅 [entity](/previous-versions/office/developer/sharepoint-2010/ee558325(v=office.14))。

3. 在设计器中，打开实体的快捷菜单，选择 " **添加**"，然后选择 " **标识符**"。

     实体上将显示一个新的标识符。

    > [!NOTE]
    > 您可以在 " **属性** " 窗口中更改实体的名称和标识符。

4. 在类中定义实体的字段。 您可以将新类添加到项目中，也可以使用通过使用其他工具（如对象关系设计器 (O/R 设计器) 创建的现有类）。 下面的示例演示一个名为 Contact 的实体类。

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs" id="Snippet1":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb" id="Snippet1":::

## <a name="see-also"></a>另请参阅
- [如何：添加 Creator 方法](../sharepoint/how-to-add-a-creator-method.md)
- [如何：添加删除器方法](../sharepoint/how-to-add-a-deleter-method.md)
- [如何：添加更新程序方法](../sharepoint/how-to-add-an-updater-method.md)
- [如何：添加 Finder 方法](../sharepoint/how-to-add-a-finder-method.md)
- [如何：添加特定的 Finder 方法](../sharepoint/how-to-add-a-specific-finder-method.md)
