---
title:  将Visual Studio调试器附加到正在运行的进程 |Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 06/20/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af44fcfe553cd720461de3a4e16986d573785c2f
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257337"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>将Visual Studio调试器附加到正在运行的进程
你可将 Visual Studio 调试器附加到正在本地或远程计算机上运行中的进程。 进程运行后，在Visual Studio 中选择**调试** > **附加到进程**或按**Ctrl**+**Alt** +**P** ，并使用**附加到进程**对话框，可以将调试器附加到进程。

可以在本地或远程计算机上使用**附加到进程**调试运行中的应用程序。调试器附加后可同时调试多个进程、 非 Visual Studio 中创建的应用或任何未从 Visual Studio 中启动的应用程序。 例如，如果您正在运行不带调试器的应用，并触发异常，可以将调试器附加到进程中运行应用程序，并开始调试。

有关在 Visual Studio 基本调试的信息，请参阅[调试器入门](../debugger/getting-started-with-the-debugger.md)。

> [!TIP]
> 不确定是否使用**附加到进程**为调试方案？ 请参阅[常见调试方案](#BKMK_Scenarios)。 

##  <a name="BKMK_Attach_to_a_running_process"></a> 附加到在本地计算机上正在运行的进程 

若要快速重新附加到以前附加到进程，请参阅[重新附加到进程](#BKMK_reattach)。 

若要调试远程计算机上的进程，请参阅[附加到远程计算机上的进程](#BKMK_Attach_to_a_process_on_a_remote_computer)。

**若要附加到本地计算机上的进程：**  

1. 在 Visual Studio 中，选择**调试** > **附加到进程**(或按**Ctrl**+**Alt** + **P**) 以打开**附加到进程**对话框。
  
   **连接类型**应设置为**默认**。 **连接目标**应该是本地计算机名称。 
  
   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process") 
  
2. 在中**可用进程**列表，查找并选择想要附加的进程。  

   - 若要快速选择一个进程，请在**筛选进程**框键入其名称或中的第一个字母。 
  
   - 如果不知道进程名称，浏览列表中，或请参阅[常见调试方案](#BKMK_Scenarios)的一些常见的进程名称。 
  
   >[!TIP]
   >在**附加到进程**对话框处于打开状态时，进程在后台可能已启动或停止，因此运行进程列表可能不是最新内容。 若要查看当前列表可以选择**刷新**。 
  
3. 在中**将附加到**字段中，请确保你打算调试的代码类型已经列出。 调试器对大多数应用类型进行工作时默认启动**自动**设置。 
  
   若要手动选择代码类型：
   1. 单击 **“选择”**。 
   1. 在中**选择代码类型**对话框中，选择**调试这些代码类型**。
   1. 选择你想要调试的代码类型。
   1. 选择**确定**。
  
4. 选择**附加**。
  
>[!NOTE]
>你可以附加到多个应用程序进行调试，但在调试器中同时只能有一个应用是处于活动状态。可在 Visual Studio **调试位置**工具栏或**进程**窗口中设置活动的应用程序。

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> 附加到远程计算机上的进程  

您还可以在远程计算机中选择**附加到进程**对话框，查看该计算机上运行的可用进程的列表，并将附加到一个或多个进程以进行调试。 远程调试器 (*msvsmon.exe*) 必须在远程计算机上运行。 有关详细信息，请参阅[远程调试](../debugger/remote-debugging.md)。 

用于调试已部署到 IIS 的 ASP.NET 应用程序的更完整说明，请参阅[远程调试远程 IIS 计算机上的 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。

**若要将附加到远程计算机上正在运行的进程：**  

1. 在 Visual Studio 中，选择**调试** > **附加到进程**(或按**Ctrl**+**Alt** + **P**) 以打开**附加到进程**对话框。
  
2. **连接类型**在大多数情况应为**默认**。 在**连接目标**框中，选择远程计算机，使用以下方法之一：

   - 选择下拉箭头旁边**连接目标**，并从下拉列表中选择计算机名称。  
   - 在**连接目标**框中键入中的计算机名称。
      
     > [!NOTE]
     > 如果您不能使用远程计算机名称进行连接，请尝试使用 IP 和端口地址 (例如， `123.45.678.9:4022`)。 Visual Studio 2017 x64 远程调试器的默认端口 4022。 有关其他远程调试器端口分配，请参阅[远程调试器端口分配](remote-debugger-port-assignments.md)。  
      
   - 选择**查找**按钮旁边**连接目标**框，以打开**远程连接**对话框。 **远程连接**对话框会列出本地子网上，或直接连接到您的计算机的所有设备。 你可能需要[打开 UDP 端口 3702](../debugger/remote-debugger-port-assignments.md)服务器以发现远程设备上。 选择的计算机或所需的设备，然后单击**选择**。 
  
   > [!NOTE]
   > 在调试会话之间设置**连接类型**为保持。 **连接目标**设置成功的调试连接出现与此目标的情况下，只有在调试会话之间保持。

3. 单击**刷新**来填充**可用进程**列表。
     
    >[!TIP]
    >在**附加到进程**对话框处于打开状态时，进程可以在后台启动和停止，因此运行进程的列表可能不是最新内容。 在任何时候，若要查看当前进程列表，可以选择**刷新**。 
     
4. 在中**可用进程**列表，查找并选择想要附加的进程 

   - 若要快速选择一个进程，请在**筛选进程**框键入其名称或第一个字母。  
  
   - 如果不知道浏览列表中的进程名称，或请参阅[常见调试方案](#BKMK_Scenarios)的一些常见的进程名称。 
  
   - 若要查找的所有用户帐户下运行的进程，请选择**显示所有用户的进程**复选框。
      
     >[!NOTE]
     >如果尝试附加不受信任的用户帐户拥有的进程，则会出现安全警告对话框确认。 有关详细信息请参阅[安全警告： 附加到不受信任的用户所拥有的进程可能很危险。以下信息看上去可疑或者你不确定，如果未附加到此进程](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)。  
      
5. 在中**将附加到**字段中，请确保你打算调试的代码类型已经列出。 默认使用**自动**设置。 
  
   若要手动选择代码类型：
   1. 单击 **“选择”**。 
   1. 在中**选择代码类型**对话框中，选择**调试这些代码类型**。
   1. 选择你想要调试的代码类型。
   1. 选择**确定**。
  
6. 选择**附加**。
  
>[!NOTE]
>你可以附加到多个应用程序以进行调试，但一次只能有一个应用是在调试器中处于活动状态。 可以在 Visual Studio **调试位置**工具栏或**进程**窗口中设置活动的应用程序。  

在某些情况下，在远程桌面 (Terminal Services) 会话中，调调试时**可用进程**列表不会显示所有可用进程。 如果以具有有限的用户帐户的用户身份运行 Visual Studio时，**可用进程**列表将不显示在会话 0 用于服务和其他服务器进程，包括运行的进程*w3wp.exe*。 你可以通过以下方法解决该问题：使用管理员帐户运行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 或从服务器控制台而不是“终端服务”会话运行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 

如果可能都不奏效，第三个选项是从 Windows 命令行运行`vsjitdebugger.exe -p <ProcessId>`附加到进程。 您可以确定进程 id 使用*tlist.exe*。 若要获取*tlist.exe*，在 Windows 中下载并安装调试工具的，位于[WDK 和 WinDbg 下载](/windows-hardware/drivers/download-the-wdk)。

## <a name="BKMK_reattach"></a> 重新附加到进程

您可以快速重新附加到先前已通过选择附加到的进程**调试** > **重新附加到进程**(**Shift** +**Alt**+**P**)。 当选择此命令时，调试器会立即尝试附加到匹配最后一个进程 ID 的进程，然而，如果该操作失败，通过与上一个进程名称相匹配。 如果找不到任何匹配项，或如果找到具有相同名称的多个进程，**附加到进程**对话框将打开，这样您就可以选择了正确的进程。

> [!NOTE]
> **重新附加到进程**命令是 Visual Studio 2017 中的新增功能。

## <a name="BKMK_Scenarios"></a> 常见的调试方案

若要帮助您确定是否使用**附加到进程**，以及要附加到哪些进程, 下表显示了一些常见的调试方案，其中包含指向尽可能详细的说明 。 （列表并不详尽无遗。）

对于某些应用类型，例如通用 Windows 应用 (UWP) 应用不直接连接到进程名称，但在 Visual Studio 中代替使用**调试安装的应用程序包**菜单选项解决（请参见表）。

为使调试器附加到用 C++ 编写的代码，该代码需要发出 `DebuggableAttribute`。 可通过链接 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) 链接器选项将它自动添加到代码中。

为客户端脚本调试，脚本调试必须启用浏览器中。 对于调试在 Chrome 上的客户端脚本，请选择**Webkit**作为代码类型，并根据你的应用类型，可能需要关闭所有 Chrome 实例并在调试模式下启动浏览器 (类型`chrome.exe --remote-debugging-port=9222`从命令行)。

若要快速选择正在运行的进程来将附加到，在 Visual Studio 中，键入**Ctrl**+**Alt**+**P**，然后键入的第一个字母进程名称。

|方案|调试方法|进程名|说明和链接|
|-|-|-|-|
|远程调试 ASP.NET 4 或 4.5 上 IIS 服务器|使用远程工具和**附加到进程**|*w3wp.exe*|请参阅[远程调试远程 IIS 计算机上的 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|IIS 服务器上的远程调试 ASP.NET Core|使用远程工具和**附加到进程**|*dotnet.exe*|有关应用程序部署，请参阅[发布到 IIS](https://docs.asp.net/en/latest/publishing/iis.html)。 有关调试，请参阅[远程调试远程 IIS 计算机上的 ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|调试本地 IIS 服务器 （仅适用于受支持的应用类型） 上的客户端脚本|使用**附加到进程**|*chrome.exe*， *MicrosoftEdgeCP.exe*，或*iexplore.exe*|必须启用脚本调试。 对于 Chrome 中，也必须在调试模式下，选择运行 Chrome **Webkit 代码**中**附加到**字段。|
|调试本地计算机上的 C#、 Visual Basic 或 c + + 应用程序|可以使用两种[标准调试](../debugger/getting-started-with-the-debugger.md)或**附加到进程**|*\<应用程序名 >.exe*|在大多数情况下，使用标准调试并不**附加到进程**。|
|远程调试 Windows 桌面应用程序|远程工具|不可用| 请参阅[远程调试 C# 或 Visual Basic 应用程序](../debugger/remote-debugging-csharp.md)或[远程调试 c + + 应用程序](../debugger/remote-debugging-cpp.md)|
|在开始使用不带调试器的应用后调试在本地计算机上的 ASP.NET 应用|使用**附加到进程**|*iiexpress.exe*|这可能会有所帮助使应用程序加载速度更快，如 （例如） 进行分析时。 |
|调试服务器进程上的其他受支持的应用类型|（如果服务器是远程的），请使用远程工具和**附加到进程**|*chrome.exe*， *iexplore.exe*，或其他进程|如有必要，使用资源监视器来帮助标识该进程。 请参阅[远程调试](../debugger/remote-debugging.md)。|
|远程调试的通用 Windows 应用 (UWP)、 OneCore、 HoloLens 或 IoT 应用|调试已安装的应用包|不可用|请参阅[调试安装的应用包](debug-installed-app-package.md)而不是使用**附加到进程**|
|调试未从 Visual Studio 启动的通用 Windows 应用 (UWP)、 OneCore、 HoloLens 或 IoT 应用|调试已安装的应用包|不可用|请参阅[调试安装的应用包](debug-installed-app-package.md)而不是使用**附加到进程**|  
  
## <a name="use-debugger-features"></a>使用调试器的功能

若要使用 Visual Studio 调试器 （如命中断点） 的全部功能的本地源和符号时附加到进程，该应用程序必须完全匹配 (也就是说，调试器必须能够加载正确[符号 (.pbd) 文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). 默认情况下，这需要调试版本。

远程调试的情况下，必须具有的源代码 （或对源代码的副本），它已经在 Visual Studio 中打开。 在远程计算机上的已编译的应用二进制文件必须和本地计算机来自同一个生成源文件。

某些本地调试的情况下，您可以在 Visual Studio 中调试源没有源文件，但是有正确符号文件的应用程序 （默认情况下，需要调试版本）。 有关详细信息，请参阅[指定符号和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。
  
##  <a name="BKMK_Troubleshoot_attach_errors"></a> 进行故障排除附加错误  
 当调试器附加到一个正在运行的进程时，该进程可能包含一种或多种类型的代码。 可在 **“选择代码类型”** 对话框中显示并选择可将调试器附加到的代码类型。  
  
 有时，调试器能够成功附加到一种代码类型，但不能附加到另一种代码类型。 这种情况可能发生在你尝试附加到远程计算机上运行的进程时。 原因是远程计算机上可能安装了一些代码类型的远程调试组件，但没有安装另一些代码类型的远程调试组件。 这种情况还可能发生在你尝试为直接数据库调试附加到两个或多个进程时。 SQL 调试仅支持附加到单个进程。  
  
 如果调试器无法附加到一些，但并非所有代码类型，您将看到消息，指明哪些类型附加操作失败。  
  
 如果调试器成功地附加到至少一种代码类型，你就可以继续调试进程。 你只能调试那些已被成功附加的代码类型。 仍将运行中进程的未附加的代码，但您将无法再以设置断点、 查看数据，或执行其他调试操作对该代码。  
  
 如果想了解有关调试器未能附加到某种代码类型的详细原因，可以尝试仅重新附加到该代码类型。  
  
 **若要获取有关某种代码类型未能附加的原因的特定信息：**  
  
1.  从进程中分离。 上**调试**菜单中，选择**全部分离**。  
  
1.  重新附加到进程，仅选择代码类型未能附加。  
  
    1.  在中**附加到进程**对话框框中，选择中的过程**可用进程**列表。  
  
    2.  选择**选择**。  
  
    3.  在 **“选择代码类型”** 对话框中，选择 **“调试以下代码类型”** 和未能附加的代码类型。 取消选择其他代码类型。  
  
    4.  选择“确定”。  
  
    5.  在中**附加到进程**对话框中，选择**附加**。  
  
    此时，附加将彻底失败，并且你将收到一条特定的错误消息。  
  
## <a name="see-also"></a>请参阅  
 [调试多个进程](../debugger/debug-multiple-processes.md)   
 [在实时调试](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [远程调试](../debugger/remote-debugging.md)
 