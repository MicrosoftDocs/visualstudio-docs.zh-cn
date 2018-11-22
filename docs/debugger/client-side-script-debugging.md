---
title: 客户端脚本调试 |Microsoft Docs
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
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a42ee63b863393c3cc2bad789d14404def8d1f5d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894984"
---
# <a name="client-side-script-debugging"></a>客户端脚本调试
Visual Studio 调试器提供了一个全面的调试环境，以便查找和更正 ASP.NET 页上客户端脚本中的错误。  
  
## <a name="opening-script-documents"></a>打开脚本文档  
可以在**解决方案资源管理器**中查看服务器端和客户端脚本文档的列表。 可以从 **“解决方案资源管理器”** 中打开任何脚本文档。 有关详细信息，请参阅 [How to: View Script Documents](../debugger/how-to-view-script-documents.md)。  
  
## <a name="breakpoint-mapping"></a>断点映射  
 在 Visual Studio 中，不能直接调试服务器端代码，但可以在服务器端文件中设置断点。 Visual Studio 会自动将断点映射到客户端文件中的对应位置，并在客户端代码中创建映射的断点。  
  
## <a name="manually-or-automatically-attaching-to-script"></a>手动或自动附加到脚本  
 若要开始在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中调试脚本，必须将调试器附加到要调试的脚本中。 这可以手动实现，也可以自动实现。  
  
 可以通过使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 调试器界面选择要将调试器附加到的正在运行的脚本进程来手动进行附加。 有关详细信息，请参阅 [How to: Attach to Script](../debugger/how-to-attach-to-script.md)。  
  
 当出现下列情况之一时，调试器会自动附加到脚本中：  
  
- 您命中了脚本中设置的断点。  
  
- 您命中了脚本代码中的 VBScript `Stop` 语句或 JScript `debugger` 语句。  
  
- 浏览器或服务器在脚本中遇到语法或运行时错误。 出现此情况时，将显示一个对话框，其中将提供开始调试的选项。  
  
  手动附加到脚本时，脚本进程将继续运行，直至用某种方式将其暂停。 可以通过选择 **“调试”** 菜单上的 **“中断”** 来暂停脚本进程。  
  
  自动附加调试器时，脚本将在出现断点、 `Stop` 语句或 `debugger` 语句或错误的行上或是您在 Internet Explorer 中选择开始调试的位置暂停执行。  
  
  在该位置，可以使用常规调试器功能开始调试。 例如，可以使用 **“单步执行”** 命令继续逐行执行代码。 可以使用 **“调用堆栈”** 窗口查看并控制脚本流。 可以使用变量窗口或 **“即时”** 窗口查看或更改变量和属性。  
  
## <a name="enhanced-error-messages-for-script-debugging"></a>增强的脚本调试错误消息  
 Visual Studio 为常见脚本调试问题提供了增强的错误消息。 只有将这些消息手动附加到 Internet Explorer，才会显示它们。 如果您在 Internet Explorer 自动打开时遇到错误情况，请尝试通过手动附加来查看错误消息。  
  
## <a name="debugging-ajax-script-applications"></a>调试 AJAX 脚本应用程序  
 支持 AJAX 的 Web 应用程序大量使用脚本代码，从而给调试带来特别大的难度。 有关 AJAX 调试技术的信息，请参见  
  
 [Debugging and Tracing Ajax Applications Overview](https://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375)中打开任何脚本文档。  
  
## <a name="see-also"></a>请参阅  
 [调试 ASP.NET 和 AJAX 应用程序](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [脚本调试的限制](../debugger/limitations-on-script-debugging.md)   
 [变量的 Windows](../debugger/debugger-windows.md)   
 [即时窗口](../ide/reference/immediate-window.md)   
 [Debugging and Tracing Ajax Applications Overview](https://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375)
