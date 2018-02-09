---
title: "远程调试 C# 或 Visual Studio 中的 VB 项目 |Microsoft 文档"
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords: remote debugging, setup
ms.assetid: a9753fbb-e7f4-47f0-9dbe-9de90c6c8457
caps.latest.revision: "65"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 6546e58139b4c427f6bbc4343faf64bdd655b63e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2018
---
# <a name="remote-debugging-a-c-or-visual-basic-project-in-visual-studio"></a>远程调试 Visual Studio 中的 C# 或 Visual Basic 项目
若要调试的 Visual Studio 应用程序已部署在另一台计算机，安装和其中部署您的应用程序的计算机上运行远程工具，你将项目配置为从 Visual Studio 中，连接到远程计算机，然后运行你的应用程序。

![远程调试器组件](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")
  
有关远程调试通用 Windows 应用 (UWP) 的信息，请参阅[调试安装的应用程序包](debug-installed-app-package.md)。

## <a name="requirements"></a>需要

远程调试器都支持 Windows 7 和更高版本 (不 phone) 和从 Windows Server 2008 Service Pack 2 的 Windows Server 版本。 有关要求的完整列表，请参阅[要求](../debugger/remote-debugging.md#requirements_msvsmon)。

> [!NOTE]
> 不支持调试通过代理连接的两台计算机之间。 国家/地区中调试通过高延迟或低带宽连接，如拨号 Internet，或通过 Internet 不建议和可能失败也是非常慢。
  
## <a name="download-and-install-the-remote-tools"></a>下载并安装远程工具

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> 在某些情况下，它可以从文件共享运行远程调试器方式效率最高。 有关详细信息，请参阅[从文件共享运行远程调试器](../debugger/remote-debugging.md#fileshare_msvsmon)。
  
## <a name="BKMK_setup"></a>设置远程调试器

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 如果你需要添加其他用户的权限更改身份验证模式中，或者远程调试器端口号，请参阅[配置远程调试器](../debugger/remote-debugging.md#configure_msvsmon)。
  
## <a name="remote_csharp"></a>远程调试项目
调试器不能将 Visual C# 或 Visual Basic 桌面应用程序部署到远程计算机，但你仍然可以按如下所示方法远程调试它们。 以下过程假设你想要在名为的计算机上进行调试它**MJO DL**，如在下图中所示。
  
1.  创建一个名为的 WPF 项目**MyWpf**。  
  
2.  在代码中的某个容易到达的地方设置断点。  
  
     例如，可在按钮处理程序中设置断点。 若要执行此操作，打开 MainWindow.xaml，和从工具箱中，添加一个按钮控件，然后双击该按钮以打开它的处理程序。
  
3.  在解决方案资源管理器，右键单击该项目并选择**属性**。  
  
4.  上**属性**页上，选择**调试**选项卡。  
  
     ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5.  请确保**工作目录**文本框为空。  
  
6.  选择**使用远程计算机**，和类型**MJO-DL:4022**在文本框中。 （4022 是远程调试器窗口中显示的端口号。 端口号递增每个版本的 Visual Studio 中的 2）。
  
7.  请确保**启用本机代码调试**未选中。  
  
8.  生成项目。  
  
9. 是相同的路径在远程计算机上创建一个文件夹**调试**Visual Studio 计算机上的文件夹： **\<源路径 > \MyWPF\MyWPF\bin\Debug**。  
  
10. 将你刚才从 Visual Studio 计算机生成的可执行文件复制到远程计算机上新创建的文件夹。
  
    > [!CAUTION]
    >  对代码或重新生成不会进行任何更改 （或你必须重复此步骤）。 复制到远程计算机的可执行文件必须与你的本地源和符号完全匹配。

    你可以手动复制项目、 使用 Xcopy、 Robocopy、 Powershell 或其他选项。
  
11. 请确保在目标计算机上运行远程调试器 (如果不是，搜索**远程调试器**中**启动**菜单)。 远程调试器窗口如下所示。  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. 在 Visual Studio 中，启动调试 (**调试 > 启动调试**，或**F5**)。  
  
13. 如果出现提示，输入用于连接到远程计算机的网络凭据。  
  
     所需的凭据会有所不同，具体取决于你的网络安全配置。 例如，在域计算机上，可以输入你的域用户名和密码。 在非域计算机上，你可以输入计算机名和有效的用户帐户名称，如 **MJO-DL\name@something.com** ，以及正确的密码。

     你应看到 WPF 应用程序的主窗口处于打开远程计算机上。
  
14. 如有必要，请采取措施以命中该断点。 你应看到该断点处于活动状态。 不是这样，如果尚未加载应用程序的符号。 重试，并且如果这不起作用，获取有关加载符号的信息和如何解决在[了解符号文件和 Visual Studio 的符号设置](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx)。
  
15. 在 Visual Studio 机器上，你应看到执行在断点处停止。
  
 如果具有需要由应用程序使用的非代码文件，则需要将其包含在 Visual Studio 项目中。 创建为其他文件的项目文件夹 (在**解决方案资源管理器**，单击**添加 > 新文件夹**)。 然后将文件添加到的文件夹 (在**解决方案资源管理器**，单击**添加 > 现有项**，然后选择的文件)。 上**属性**对于每个文件页上，设置**复制到输出目录**到**始终复制**。

## <a name="set-up-debugging-with-remote-symbols"></a>使用远程符号设置调试 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]  
  
## <a name="see-also"></a>请参阅  
 [在 Visual Studio 中进行调试](../debugger/index.md)  
 [调试器功能简介](../debugger/debugger-feature-tour.md)   
 [配置 Windows 防火墙以允许远程调试](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [远程调试器端口分配](../debugger/remote-debugger-port-assignments.md)   
 [远程调试远程 IIS 计算机上的 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [远程调试错误和疑难解答](../debugger/remote-debugging-errors-and-troubleshooting.md)