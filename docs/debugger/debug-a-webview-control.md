---
title: 调试 WebView 控件 (UWP) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 4576cfa5724869aba86842c5debb4df685559879
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465455"
---
# <a name="debug-a-webview-control-in-a-uwp-app"></a>在UWP 应用中调试 WebView 控件 
  
 若要检查并调试 Windows 运行时应用中的 `WebView` 控件，你可以在启动应用时配置 Visual Studio 附加脚本调试器。 可通过两种方式来与交互`WebView`控制使用调试器：  
  
-   打开[DOM 资源管理器](../debugger/quickstart-debug-html-and-css.md)为`WebView`实例，并检查 DOM 元素、 调查 CSS 样式问题并测试动态呈现的样式更改。  
  
-   选择显示的网页或`iFrame`中显示`WebView`实例中的目标作为[JavaScript 控制台](../debugger/javascript-console-commands.md)窗口中，然后使用控制台命令的网页与进行交互。 控制台提供对当前脚本执行上下文的访问。  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>附加调试器（C#、Visual Basic、C++）  
  
1.  在 Visual Studio 中，向 Windows 运行时应用添加 `WebView` 控件。  
  
2.  在解决方案资源管理器中打开项目的属性，通过选择**属性**从项目的快捷菜单。  
  
3.  选择**调试**。 在**应用程序进程**列表中，选择**脚本**。  
  
     ![附加脚本调试器](../debugger/media/js_dom_webview_script_debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4.  （可选）对于非 Express 版本的 Visual Studio，禁用实时 (JIT) 调试通过选择**工具 > 选项 > 调试 > 中实时**，然后禁用 JIT 调试脚本。  
  
    > [!NOTE]
    >  对于某些网页上发生的无法处理的异常，你可以通过禁用 JIT 调试来隐藏对话框。 在 Visual Studio Express 中，JIT 调试始终处于禁用状态。  
  
5.  按 F5 开始调试。  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>使用 DOM 资源管理器以检查并调试 WebView 控件  
  
1.  （C#、Visual Basic、C++）向你的应用附加脚本调试器。 请参见第一部分以获取说明。  
  
2.  若没有 `WebView` 控件，请向应用添加该控件并按 F5 启动调试。  
  
3.  导航到包含 `Webview` 控件的页面。  
  
4.  打开 DOM 资源管理器窗口`WebView`通过选择的控件**调试**， **Windows**， **DOM 资源管理器**，然后选择的 URL`WebView`你想要检查。  
  
     ![打开 DOM 资源管理器](../debugger/media/js_dom_webview.png "JS_DOM_WebView")  
  
     与 `WebView` 关联的 DOM 资源管理器将在 Visual Studio 中显示为新选项卡。  
  
5.  查看和修改实时 DOM 元素和 CSS 样式中所述[使用 DOM 资源管理器调试 CSS 样式](../debugger/debug-css-styles-using-dom-explorer.md)。  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>使用 JavaScript 控制台窗口以检查并调试 WebView 控件  
  
1.  （C#、Visual Basic、C++）向你的应用附加脚本调试器。 请参见第一部分以获取说明。  
  
2.  若没有 `WebView` 控件，请向应用添加该控件并按 F5 启动调试。  
  
3.  打开 JavaScript 控制台窗口`WebView`通过选择的控件**调试**， **Windows**， **JavaScript 控制台**。  
  
     将显示“JavaScript 控制台”窗口。  
  
4.  导航到包含 `Webview` 控件的页面。  
  
5.  在控制台窗口中，选择显示的网页或`iFrame`显示`WebView`中控制**目标**列表。  
  
     ![面向 JavaScript 控制台窗口中的选择](../debugger/media/js_console_target.png "JS_Console_Target")  
  
    > [!NOTE]
    >  通过使用控制台，可以与单个 `WebView`、`iFrame` 交互，每次还可以共享协定或 Web Worker。 每个元素都需要单独的 Web 平台主机 (WWAHost.exe) 的实例。 一次可与一个主机交互。  
  
6.  查看并修改应用中的变量或使用控制台命令，如中所述[快速入门： 调试 JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)和[JavaScript 控制台命令](../debugger/javascript-console-commands.md)。  
  
## <a name="see-also"></a>请参阅  
 [快速入门：调试 HTML 和 CSS](../debugger/quickstart-debug-html-and-css.md)