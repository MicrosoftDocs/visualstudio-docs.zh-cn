---
title: 如何：显示外接程序用户界面错误
description: 了解如何使用 Visual Studio 以编程方式在 Microsoft Office 应用程序中显示 VTSO 外接程序用户界面错误。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e74d60fe6386575417114fe1ad4823704cf09d46
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528132"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>如何：显示外接程序用户界面错误
  默认情况下，如果 VSTO 外接程序尝试操作 Microsoft Office 用户界面 (UI) 并失败，则不会显示错误消息。 但是，你可以配置 Microsoft Office 应用程序以显示与 UI 相关的错误的消息。 您可以使用这些消息来帮助确定自定义功能区未出现的原因，或出现功能区但不显示控件的原因。

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="to-show-vsto-add-in-user-interface-errors"></a>显示 VSTO 外接程序用户界面错误

1. 启动应用程序。

2. 单击 **“文件”** 选项卡。

3. 单击“选项”。

4. 在类别窗格中，单击“高级” 。

5. 在细节窗格中，选择“显示 VSTO 外接程序用户界面错误” ，然后单击“确定” 。

    > [!NOTE]
    > 对于 Outlook，“显示 VSTO 外接程序用户界面错误”  复选框位于细节窗格的“开发工具”  部分。 对于其他应用程序，该复选框位于细节窗格的“常规”  部分。

## <a name="see-also"></a>另请参阅
- [Office UI 自定义](../vsto/office-ui-customization.md)
- [创建 Outlook 窗体区域](../vsto/creating-outlook-form-regions.md)
- [功能区概述](../vsto/ribbon-overview.md)
- [操作窗格概述](../vsto/actions-pane-overview.md)
