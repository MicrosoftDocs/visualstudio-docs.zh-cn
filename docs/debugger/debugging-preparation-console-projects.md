---
title: 调试准备：控制台项目 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 516b2a6191cc76c3380875fda4679048e255f394
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902071"
---
# <a name="debugging-preparation-console-projects"></a>调试准备：控制台项目
准备调试控制台项目类似于准备调试 Windows 项目，但是有一些额外的注意事项。 有关详细信息，请参阅[Windows 窗体应用程序](../debugger/debugging-preparation-windows-forms-applications.md)，并[调试准备： Windows 窗体应用程序 (.NET)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100))。 由于所有控制台应用程序的相似性，本主题介绍以下项目类型：  
  
- C# 控制台应用程序  
  
- Visual Basic 控制台应用程序  
  
- C++ 控制台应用程序 (.NET)  
  
- C++ 控制台应用程序 (Win32)  
  
  可能必须为控制台应用程序指定命令行自变量。 有关详细信息，请参阅[c + + 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)， [Visual Basic 调试配置的项目设置](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)，或[的 C# 调试配置项目设置](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
  同所有项目属性一样，这些自变量将在调试会话之间和 Visual Studio 会话之间保留。 因此，如果以前调试过的其中一个控制台应用程序，请记住可能是从以前的会话中输入的参数 **\<项目> 属性页** 对话框。  
  
  控制台应用程序使用**控制台**窗口接受输入以及显示输出消息。 要写入到**控制台**窗口中，你的应用程序必须使用**控制台**对象而不是 Debug 对象。 要写入到**Visual Studio 输出**窗口中，像往常一样使用 Debug 对象。 确保知道应用程序正在写入的位置，否则可能在错误的位置中查找消息。 有关详细信息，请参阅[Console 类](/dotnet/api/system.console)，[调试类](/dotnet/api/system.diagnostics.debug)，并[输出窗口](../ide/reference/output-window.md)。  
  
## <a name="starting-the-application"></a>启动应用程序  
 某些控制台应用程序在启动后将运行完成，然后退出。 此行为可能不会为您提供足够的时间来中断执行并调试。 若要能够调试应用程序，请使用下列过程之一来启动应用程序：  
  
- 应用程序开始运行，直至到达该断点。  
  
- 应用程序将启动并立即在源代码的第一行处中断。  
  
- 在源代码窗口中，右击某行并选择**运行到光标处**。  
  
   应用程序将启动并运行到选定的行或运行到某个断点（如果在该行之前命中此断点）。  
  
  调试控制台应用程序时，您可能希望从命令提示符处而不是从 Visual Studio 中启动该应用程序。 在这种情况下，可以从命令提示处启动应用程序并将 Visual Studio 调试器附加到该应用程序。 有关详细信息，请参阅[附加到正在运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
  从 Visual Studio 中，启动控制台应用程序时**控制台**窗口有时会出现在 Visual Studio 窗口的后面。 如果尝试从 Visual Studio 中启动控制台应用程序但似乎未产生任何结果，请尝试移动 Visual Studio 窗口。  
  
## <a name="see-also"></a>请参阅  
 [调试本机代码](../debugger/debugging-native-code.md)   
 [Debugging Managed Code](../debugger/debugging-managed-code.md) （调试托管代码）  
 [Visual C++ 项目类型](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#、F#、和 Visual Basic 项目类型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C + + 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [调试器安全](../debugger/debugger-security.md)