---
title: VSCodeWindow 对象 |Microsoft Docs
description: 了解代码窗口，这是可以包含一个或多个文本视图（通常为 VsTextView 对象）的专用文档窗口。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77839bf80f30de3177f647795ffb89aa3e103d58
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062416"
---
# <a name="vscodewindow-object"></a>VSCodeWindow 对象
代码窗口是一个专用的文档窗口，它可以包含一个或多个文本视图，通常是 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 对象。

 在体系结构上，代码窗口是窗口框架内的文档窗口。 在功能上，代码窗口只是包含附加功能的文档窗口。 在多文档界面 (MDI) 模式下，代码窗口是 MDI 子框架。 有关详细信息，请参阅 [使用旧版 API 自定义代码窗口](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015)。

 下表包括对象中的接口 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> 。

|方法|说明|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|提供了一种通用访问机制，用于查找全局唯一标识符 (GUID) 标识的服务。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|表示包含一个或多个代码视图 (MDI) 子级的多文档接口。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|填充窗口框架。|

## <a name="see-also"></a>另请参阅
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [编辑图形](https://www.microsoft.com/download/details.aspx?id=55984)