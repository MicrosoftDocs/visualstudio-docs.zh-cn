---
title: Visual Studio 中的 UWP 应用部署 |Microsoft Docs
ms.custom: ''
ms.date: 01/16/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 81d29324f0888655e729f347d1ae22e12d777be4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818414"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>从 Visual Studio 部署 UWP 应用
  
 Visual Studio部署功能构建并注册在目标设备上使用Visual Studio创建的UWP应用程序。 应用的实际注册方法取决于目标设备是本地还是远程：  
  
- 如果目标是本地 Visual Studio 计算机，Visual Studio 将从其生成文件夹注册应用。  
  
- 如果目标是远程设备，Visual Studio 会将所需的文件复制到远程计算机，并在该设备上注册应用。  
  
  当使用 Visual Studio 调试您的应用程序时，使用 **开始调试** 选项 (键盘： F5) 或**启动但不调试**选项 (键盘： CTRL + F5) 自动部署。 你也可以手动部署应用。 手动部署在以下情况中非常有用：  
  
- 本地或远程计算机上的特别测试。  
  
- 部署的应用，将启动要调试的另一个应用。  
  
- 部署的应用，将启动要调试的另一个应用或方法。
  
##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> 如何部署 UWP 应用  
 手动部署应用是一个非常简单的过程：  
  
1.  如果你要部署到远程设备，请在应用的启动项目的属性项目页中指定设备的名称或 IP 地址。 （执行此操作的步骤在本主题靠后的位置列出)。  
  
2.  在调试器的 Visual Studio 工具栏上，从下拉列表旁的 **“启动调试”** 按钮选择部署目标。  
  
     ![本地计算机上运行](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
3.  在 **“生成”** 菜单上，选择 **“部署”**  
  
##  <a name="BKMK_How_to_specify_a_remote_device"></a> 如何指定远程设备  

**系统必备**  
  
在 Windows 10 的远程设备，必须启用[开发人员模式](/windows/uwp/get-started/enable-your-device-for-development)。 在运行创意者更新的 Windows 10 设备上或更高版本，远程工具部署应用时自动安装。 有关详细信息，请参阅[调试安装的应用包](../debugger/debug-installed-app-package.md)。

> [!NOTE]
> 在之前的创建者的更新版本的 Windows 10，必须在远程设备上安装适用于 Visual Studio 的远程工具和必须运行远程调试器。
  
部署使用远程调试器网络渠道将应用文件发送到远程设备。  
  
#### <a name="to-specify-a-remote-device"></a>指定远程设备  
  
1. 在启动项目的“调试”属性页上，指定远程部署目标的名称或 IP 地址。  
  
2. 要打开“调试”属性页，请在解决方案资源管理器中选择项目，然后从快捷菜单中选择 **“属性”** 。  
  
3. 然后，在属性页窗口上选择 **“调试”** 节点。

4. **目标设备** 中，选择**远程计算机**。

5. **远程计算机** 下面，单击**查找**。
  
6. 您可以键入远程设备的名称或 IP 地址，也可以从**远程连接**对话框选择设备。  
  
    ![选择远程调试器连接对话框](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
    **远程连接**对话框中显示本地网络子网上的设备，和通过以太网电缆直接连接到 Visual Studio 计算机的任何设备。  
  
   **在 JavaScript 或 Visual C++ 项目页中指定远程设备**  
  
   ![C&#43; &#43;项目属性以便进行远程调试](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")  
  
7. 从 **“远程调试器”** 列表中选择 **“要启动的调试器”** 。  
  
8. 在 **“计算机名称”** 框中输入远程设备的网络名称。 或者，你可以选择框中的下拉箭头，从“选择远程调试器连接”对话框中选择该设备。  
  
   **在 Visual C# 和 Visual Basic 项目页中指定远程设备**  
  
   ![管理项目属性以便进行远程调试](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
9. 从 **“目标设备”** 列表中选择 **“远程计算机”** 。  
  
10. 在 **“远程计算机”** 框中输入远程设备的网络名称，或单击 **“查找”** ，从 **“选择远程调试器连接”** 对话框中选择该设备。  
  
##  <a name="BKMK_Deployment_options"></a> 部署选项  
 你可以在启动项目的“调试”属性页上设置以下部署选项。  
  
 **允许网络环回**  
 出于安全原因，UWP 或[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]以标准方式安装应用程序不允许进行网络调用安装的设备。 默认情况下，Visual Studio 部署功能为所部署的应用程序创建此规则的例外。 通过此例外，在一台计算机上即可测试通信过程。 向 [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]提交应用之前，应在没有例外的情况下测试应用。  
  
 若要从应用中移除网络环回例外，请执行以下操作：  
  
- 在 C# 和 VB 调试属性页上，清除 **“允许网络环回”** 复选框。  
  
- 在 JavaScript 和调试属性页上，将 **“允许网络环回”** 值设置为 **“否”**。  
  
  **不启动，但在启动时调试代码（C# 和 VB）/启动应用程序（JavaScript 和 C++）时调试我的代码**  
  配置部署以在应用启动时自动启动调试会话：  
  
- 在 C# 和 VB 调试属性页上，选中 **“不启动，但在启动时调试代码”** 复选框。  
  
- 在 JavaScript 和调试属性页上，将 **“启动应用程序”** 值设置为 **“是”**。  
  
## <a name="see-also"></a>请参阅  
 [高级远程部署选项](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)  
 [调试安装的应用包](../debugger/debug-installed-app-package.md)   
 [从 Visual Studio 运行应用](../debugger/run-store-apps-from-visual-studio.md)