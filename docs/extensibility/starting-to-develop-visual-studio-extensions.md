---
title: "开始开发 Visual Studio 扩展 |Microsoft 文档"
ms.custom: 
ms.date: 09/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7bc03568465efa022981ade059b0de68019a5978
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2018
---
# <a name="starting-to-develop-visual-studio-extensions"></a>开始开发 Visual Studio 扩展
如果您从未编写过 Visual Studio 扩展之前，可能会出现一些问题。 我们已列出了一些最常见的。 如果看不到你正在寻找的信息，请使用反馈按钮 (**是很有帮助的此页面？**在屏幕底部) 以询问有关所需。  
  
## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>需要哪些软件开发 Visual Studio 扩展？  
 你需要在 Visual Studio 中安装 Visual Studio SDK，以便开发 Visual Studio 扩展。 你可以作为正则安装的一部分安装 Visual Studio SDK 或更高版本上安装。 有关安装 Visual Studio SDK 的详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>我可以使用 Visual Studio 扩展做何种操作？  
 Sky 的限制，就应该构想不同 Visual Studio 扩展。 当然，大多数扩展有一些与编写代码，但是，不一定是这种情况。 下面是可以生成的扩展的类型的一些示例：  
  
-   对未包含在 Visual Studio 中，使用语法着色、 IntelliSense、 和编译器和调试支持的语言的支持  
  
-   与其他模板、 代码重构，新对话框或工具窗口的扩展核心的工作效率工具 IDE 体验  
  
-   用于与数据设计或云支持类似的方案的特定于域的设计器  
  
 有关扩展的示例，请查看[Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)。 许多扩展已打开，并且应用商店包括到其 GitHub 存储库的链接。 
  
## <a name="which-visual-studio-features-can-i-extend"></a>可以扩展的 Visual Studio 功能？  
 从理论上讲，你可以扩展 Visual Studio 的几乎任何一部分： 菜单、 工具栏、 命令、 windows、 解决方案、 项目、 编辑器和等等。  
  
 在实践中，我们发现大多数人想要扩展的功能是命令、 菜单和工具栏、 窗口、 IntelliSense、 以及项目。 以下是指向相关章节：  
  
-   [扩展菜单和命令](../extensibility/extending-menus-and-commands.md)： 将你自己的项添加到 Visual Studio 菜单和工具栏。 你可以使用它们启动 Visual Studio 的新功能或外部的帮助器应用程序。 您还可以为你的菜单项提供自定义的快捷方式。  
  
-   [扩展和自定义工具窗口](../extensibility/extending-and-customizing-tool-windows.md)： 扩展现有的工具窗口或创建你自己的工具窗口。 例如，可以添加到新属性**属性**，或者，可以创建一个新的工具窗口，以添加其他功能。  
  
-   [编辑器和语言服务扩展](../extensibility/editor-and-language-service-extensions.md)： 添加你自己的自定义 IntelliSense 提供的 Visual Studio 语言，或创建新的编程语言的支持。 你可以创建新的语句完成、 建议和新的快速信息工具提示。 电灯泡，你可以添加重构的建议和代码修复以支持新的编程语言。  
  
-   [扩展项目](../extensibility/extending-projects.md)  
  
-   [扩展用户设置和选项](../extensibility/extending-user-settings-and-options.md)  
  
-   [扩展属性和属性窗口](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [扩展 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Visual Studio 独立 Shell](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a>项目模板提供的 VSSDK？  
 扩展的两种主要类型是 Vspackage 和 MEF 扩展。 一般情况下，VSPackage 扩展的扩展的使用或扩展命令、 工具窗口和项目使用。 MEF 扩展用于扩展或自定义 Visual Studio 编辑器。  
  
 对于 Visual C# 和 Visual Basic 扩展，VSSDK 提供了空的 VSIX 项目模板，可以与创建菜单命令、 工具窗口和编辑器扩展将新项模板一起使用。 此外可以分发给其他用户使用此模板包项目模板、 代码段和其他项目。  
  
 对于 c + +，VSPackage 向导将提供用于添加菜单命令、 工具窗口和自定义编辑器的代码。  
  
 独立 Shell 模板用于包的版本可以设置外观，还可以将自己作为分发的 Visual Studio shell 中的扩展。 以下主题演示了如何开始使用每个类型的扩展插件：  
  
-   菜单命令：[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   工具窗口：[使用工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   编辑器扩展：[带有编辑器项模板创建扩展](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   基本 Vspackage:[使用 VSPackage 创建扩展](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   VSIX 项目模板： [Getting Started with VSIX 项目模板](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Visual Studio 独立 shell:[演练： 创建基本的独立 Shell 应用程序](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>如何获取我扩展为类似于 Visual Studio？  
 获得很好的诀窍设计你的扩展中的 UI [Visual Studio 用户体验指南](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)。  
  
## <a name="where-can-i-find-examples-of-vssdk-code"></a>在哪里可以找到 VSSDK 代码的示例？  
 每一节中列出的链接具有向你展示如何实现特定功能的分步演练。 你还可以查找开放源代码 github 上的 VSSDK 示例[Visual Studio 示例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)。  
  
## <a name="how-can-i-distribute-my-extension"></a>如何分发我扩展？  
 可以在另一台计算机上安装你的扩展，也可以将其发送到你的好友为.vsix 文件，通过双击该安装。 你可以了解有关在 VSIX 包的详细信息[传送 Visual Studio 扩展](../extensibility/shipping-visual-studio-extensions.md)。  
  
 你还可以发布你在 Visual Studio Marketplace，使其可见到大量的 Visual Studio 客户的扩展。 打包应用商店的扩展的示例，请参阅[演练： 发布 Visual Studio 扩展](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)。 有关需要要做，以在 Marketplace 上发布的内容的详细信息，请参阅[产品和 Visual Studio 的扩展](/vsts/integrate/ide/extensions/overview)。
