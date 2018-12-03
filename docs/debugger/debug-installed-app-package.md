---
title: 调试已安装的 UWP 应用包 |Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 11/07/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 331fd642001f1e6217736185d4b3bbbd7f56923e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784411"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>调试 Visual Studio 中已安装的 UWP 应用包

Visual Studio 可以调试在 Windows 10 计算机、 Xbox、 HoloLens 和 IoT 设备上的已安装通用 Windows 平台 (UWP) 应用程序包。 

>[!NOTE]
>在手机上不支持的 visual Studio 调试已安装的 UWP 应用的。
   
有关调试 UWP 应用的详细信息，请参阅博客文章上[调试已安装的应用包](https://blogs.msdn.microsoft.com/devops/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/)并[构建通用 Windows 应用 (UWP)](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/)。

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>调试本地计算机上已安装的 UWP 应用

1. 在 Visual Studio 中，选择**调试** > **其他调试目标** > **调试安装的应用程序包**。
   
1. 在**调试安装的应用程序包**对话框中的 **连接类型** 下面，选择**本地计算机**。
   
1. 在**安装的应用程序包** 下面，选择想要调试的应用或搜索框中键入其名称。 **未在运行** 下方会显示未运行的已安装应用包，正在运行的应用会显示在 **运行** 下方。 
   
   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")
   
1. 如有必要，更改**调试此代码类型** 下面的代码类型，并选择其他选项。 
   - 选择**不启动，但在启动时调试我的代码** ，当该应用程序启动时启动调试。 当应用启动时启动调试是调试来自 [不同的启动方法](/windows/uwp/xbox-apps/automate-launching-uwp-apps) 控制路径的有效方法，如使用自定义参数激活协议。
   
1. 选择**启动**，或如果应用正在运行，选择**附加**。

> [!NOTE]
> 在Visual Studio 中选择 **调试** > **附加到进程** ，附加到任何正在运行的 UWP 或其他应用程序的进程。 附到正在运行进程时，不需要原始的 Visual Studio 项目，调试不含的原始代码的进程时，加载应用程序的符号将起到显著作用。 请参阅[在调试器中指定符号和源文件](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。
  
## <a name="remote"></a> 调试远程计算机或设备上已安装的 UWP 应用

 在Windows 10 设备或远程 post 的创建者的更新 Windows 10 计算机上，Visual Studio 第一次调试已安装的 UWP 应用时，它在目标设备上安装远程调试工具。 

1. Visual Studio 计算机、远程设备或计算机上[启用开发人员模式](/windows/uwp/get-started/enable-your-device-for-development)。
   
1. 如果要连接到运行创建者更新预览版的 Windows 10 远程计算机，在远程计算机上[手动安装并启动远程调试器](../debugger/remote-debugging.md)。
   
1. 在 Visual Studio 计算机上，选择**调试** > **其他调试目标** > **调试安装的应用程序包**。
   
1. 在中**调试安装的应用程序包**对话框，**连接类型**中，选择**远程计算机**或者**设备**。
   
   如果选择**设备**，计算机必须以物理方式连接到 Windows 10 设备。
   
   对于远程计算机，如果计算机地址没有旁边出现**地址**，选择**更改**。 
      
   1. 在中**远程连接**对话框旁边**地址**，键入名称或你想要连接到计算机的 IP 地址。
      
      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")
      
      如果调试器无法连接到远程计算机使用的计算机名称，请改为使用的 IP 地址。 用于 Xbox、 HoloLens 或 IoT 设备的 IP 地址。
   1. 选择一个身份验证选项旁边**身份验证模式**。
      
      对于大多数应用中，保留默认值**通用 （未加密的协议）**。
   1. 选择**选择**。 

1. **安装的应用程序包**中，选择想要调试的应用或搜索框中键入其名称。 **未在运行**中会显示未运行的已安装的应用包，**运行** 中会显示正在运行的应用。 
   
1. 如有必要，**调试此代码类型**中更改下面的代码类型，并选择其他选项。 
   - 选择**不启动，但在启动时调试我的代码**启动应用程序时启动调试。 启动应用程序时启动调试，是调试来自[不同的启动方法](/windows/uwp/xbox-apps/automate-launching-uwp-apps)有效控制路径，如使用自定义参数激活协议。
   
1. 选择**启动**，如果应用正在运行，选择**附加**。

当开始第一次调试连接 Xbox、 HoloLens 或 IoT 设备上安装的应用包时，Visual Studio 给目标设备安装远程调试器的正确版本。 安装远程调试器可能需要一些时间和消息，在这种状况下显示**正在启动远程调试器**。

>[!NOTE]
>目前，Xbox 或 HoloLens 设备附加调试器时，如果已运行则重启应用。

对于UWP 应用远程部署的更多信息，请参阅[部署和调试 UWP 应用](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)并[远程计算机上的调试 UWP 应用](run-windows-store-apps-on-a-remote-machine.md)。 
  
## <a name="see-also"></a>请参阅  
 [在 Visual Studio 中进行调试](../debugger/index.md)  
 [调试器功能简介](../debugger/debugger-feature-tour.md)  
 [远程调试](../debugger/remote-debugging.md)  
 [配置 Windows 防火墙以便进行远程调试](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [远程调试器端口分配](../debugger/remote-debugger-port-assignments.md)  
 [远程调试错误和疑难解答](../debugger/remote-debugging-errors-and-troubleshooting.md)