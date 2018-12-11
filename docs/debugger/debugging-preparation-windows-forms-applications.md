---
title: 调试准备： Windows 窗体应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c4dc7cb560e6ae652474d16e003eafb352643ea
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951062"
---
# <a name="debugging-preparation-windows-forms-applications"></a>调试准备：Windows 窗体应用程序
Windows 窗体项目模板创建 Windows 窗体应用程序。 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中调试此类应用程序非常简单。 有关详细信息，请参阅[创建一个 Windows 应用程序项目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100))。  
  
 用项目模板创建 Windows 窗体项目时，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 将自动为调试和发布配置创建所需的设置。 必要时，可更改这些设置。 可以更改这些设置在 **\<项目名称 > 属性页**对话框的 (在 Visual Basic  **我的项目** 中)。  
  
 有关详细信息，请参阅[建议的属性设置](../debugger/managed-debugging-recommended-property-settings.md)。  
  
 下表显示一个附加的建议属性设置。  
  
### <a name="configuration-properties-in-debug-tab"></a>“调试”选项卡中的“配置属性”  
  
|**属性名称**|**设置**|  
|-----------------------|-----------------|  
|**启动操作**|-很多时候，设置为**启动项目**。 设置为**启动外部程序**如果你想要开始另一个可执行文件启动调试 （通常用于调试 Dll）。|  
  
 可以从 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内部或者通过附加到已经运行的应用程序来调试 Windows 窗体应用程序。 有关附加的详细信息，请参阅[将附加到正在运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>调试 C#、F# 或 Visual Basic Windows 窗体应用程序  
  
1. 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中打开项目。  
  
2. 根据需要创建断点。  
  
    由于 Windows 窗体应用程序是事件驱动的，您的断点将进入事件处理程序代码，或进入由事件处理程序代码调用的方法。 要在其中设置断点的典型事件包括：  
  
   1. 与控件关联的事件，如 Click、Enter 等  
  
   2. 与应用程序启动和关闭关联的事件，如 Load、Activated 等  
  
   3. 焦点和验证事件。  
  
      有关详细信息，请参阅[在 Windows 窗体中创建事件处理程序](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms)。  
  
3. 在 **调试** 菜单上，单击**启动**。  
  
4. 使用 [调试器基础知识](../debugger/getting-started-with-the-debugger.md) 中讨论的技术进行调试。  
  
## <a name="see-also"></a>请参阅  
 [调试托管代码](../debugger/debugging-managed-code.md) （调试托管代码）  
 [C#、F#、和 Visual Basic 项目类型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [如何： 设置调试和发布配置](../debugger/how-to-set-debug-and-release-configurations.md)   
 [C# 调试配置的项目设置](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 调试配置的项目设置](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [附加到正在运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows 窗体](/dotnet/framework/winforms/index)