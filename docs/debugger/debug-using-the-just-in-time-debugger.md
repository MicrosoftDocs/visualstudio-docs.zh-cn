---
title: 使用实时调试器进行调试 |Microsoft Docs
ms.custom: ''
ms.date: 09/24/18
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: ee4d79a5-a1d2-4418-a93f-dd57a53e1836
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f66d3fdcd400be9356776647b0ead118e83d7108
ms.sourcegitcommit: c5e72875206b8c5737c29d5b1ec7b86eec747303
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/17/2018
ms.locfileid: "49382737"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>在 Visual Studio 中使用实时调试器进行调试

应用运行在 Visual Studio 之外，发生错误或崩溃时，实时调试可自动启动 Visual Studio。 在实时调试时，可以测试在 Visual Studio 外部的应用程序，当出现问题打开 Visual Studio 开始调试。

在实时调试适用于 Windows 桌面应用。 它并不适用于通用 Windows 应用，也不适用于托管在本机应用程序(如可视化器)中的托管代码。

> [!TIP]
> 如果只想停止出现实时调试器对话框，但不安装 Visual Studio，请参阅[禁用实时调试器](../debugger/just-in-time-debugging-in-visual-studio.md)。 如果已安装 Visual Studio，您可能需要[禁用在实时调试从 Windows 注册表](#disable-just-in-time-debugging-from-the-windows-registry)。 

##  <a name="BKMK_Enabling"></a> 在 Visual Studio 中启用或禁用实时调试

>[!NOTE]
>若要启用或禁用实时调试，必须 以管理员身份运行 Visual Studio 。启用或禁用实时调试会设置一个注册表项，可能需要管理员权限来更改注册表项。此时以管理员身份打开 Visual Studio ，右键单击 Visual Studio 应用程序，然后选择**以管理员身份运行**。 

可以使用 Visual Studio 配置实时调试 **工具** > **选项**(或**调试** > **选项**)对话框。 

**启用或禁用实时调试：**

1. 在**工具**或**调试**菜单中，选择**选项** > **调试** >  **在实时**。

   ![启用或禁用 JIT 调试](../debugger/media/dbg-jit-enable-or-disable.png "启用或禁用 JIT 调试")

1. 在**启用实时调试对这些类型的代码**框中，选择要进行实时调试的代码的类型：**托管**，**本机**，和/或**脚本**。
   
1. 选择“确定”。

如果启动了实时调试器，但应用程序崩溃或错误时，它没有自动打开，请参阅[进行故障排除实时调试](#jit_errors)。

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>从 Windows 注册表禁用实时调试

即便在你的计算机中不再安装 Visual Studio，仍可启动实时调试。 如果不再安装 Visual Studio，通过编辑 Windows 注册表禁用实时调试。

**若要通过编辑注册表禁用实时调试：**

1.  从 Windows**开始**菜单中，运行**注册表编辑器**(*regedit.exe*)。

2.  在中**注册表编辑器**窗口中，找到并删除以下注册表项：

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\。NETFramework\DbgManagedDebugger**

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![JIT 注册表项](../debugger/media/dbg-jit-registry.png "JIT 注册表项")

3.  如果您的计算机正在运行 64 位操作系统，也删除以下注册表项：

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\。NETFramework\DbgManagedDebugger**

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    请确保不能删除或更改任何其他注册表项。

5.  关闭**注册表编辑器**窗口。

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>启动Windows Form的实时调试 

默认情况下，Windows Form应用程序有一个顶级异常处理程序，可让应用能够恢复时保持运行。 如果 Windows Form应用程序引发未处理的异常，则会显示以下对话框：

![Windows Form未经处理的异常](../debugger/media/windowsformsunhandledexception.png "Windows Form未经处理的异常")

若要启用实时调试代替标准 Windows Form错误处理，请添加这些设置：

-  在`system.windows.forms`的 *machine.config* 或 *\<应用名称 >。 exe.config* 文件中，将`jitDebugging`值设为`true`:
    
    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```
    
-  在 c + + Windows Form 应用程序中，*.config* 文件或代码中设置 `DebuggableAttribute` 为 `true` 。 如果使用编译[/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format)且无[/Og](/cpp/build/reference/og-global-optimizations)，编译器会为您设置此属性。如果你想要调试非优化发布版本，但是，你必须在应用中 *AssemblyInfo.cpp* 文件，如下设置 `DebuggableAttribute` ：

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```
   
   有关详细信息，请参阅 <xref:System.Diagnostics.DebuggableAttribute> 。

## <a name="BKMK_Using_JIT"></a>使用在实时调试
 此示例将指导你完成在实时调试时，应用程序引发错误。

 - 您必须具有 Visual Studio 安装，请遵循以下步骤。 如果未安装 Visual Studio，则可以下载免费[Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)。
   
 - 请确保在实时调试[启用](#BKMK_Enabling)中**工具** > **选项** > **调试** > **中实时**。

对于此示例中，你将使C#控制台应用，在 Visual Studio 中，将引发[NullReferenceException](/dotnet/api/system.nullreferenceexception)。

1. 在 Visual Studio 中，创建C#控制台应用程序 (**文件** > **新建** > **项目** > **Visual C#**   > **控制台应用程序**) 名为*ThrowsNullException*。 在 Visual Studio 中创建项目的详细信息，请参阅[演练： 创建简单应用程序](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)。
   
1. 当在 Visual Studio 中打开项目时，打开*Program.cs*文件。 将打印到控制台的行，然后引发 NullReferenceException 的以下代码替换为 main （） 方法：
   
   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```
   
1. 若要生成解决方案，选择**调试**（默认值） 或**发行**配置，并选择**生成** > **重新生成解决方案**. 
   
   >[!NOTE]
   >- 选择**调试**配置完整的调试体验。 
   >- 如果选择[发行](../debugger/how-to-set-debug-and-release-configurations.md)配置，必须先关闭[仅我的代码](../debugger/just-my-code.md)若要运行此过程。 下**工具** > **选项** > **调试**，取消选择**启用 ' 仅我的代码**。
   有关生成配置的详细信息，请参阅[了解生成配置](../ide/understanding-build-configurations.md)。
   
1. 打开生成的应用*ThrowsNullException.exe*中将C#项目文件夹 (*...\ThrowsNullException\ThrowsNullException\bin\Debug*或 *...\ThrowsNullException\ThrowsNullException\bin\Release*)。 
   
   应会看到下面的命令窗口：
   
   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")
   
1. **选择实时调试器**对话框随即打开。
   
   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")
   
   下**可用调试器**，选择**的新实例\<你首选 Visual Studio 版本 >**，如果未处于选中状态。 
   
1. 选择“确定”。
   
   ThrowsNullException 项目可打开 Visual Studio 的新实例中引发异常的代码行处停止执行：
   
   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

你可以开始调试在这里。 如果调试真正的应用程序，您需要找出原因代码抛出异常。

> [!CAUTION]
> 如果您的应用程序包含不受信任的代码，则会出现安全警告对话框中，使您决定是否要继续进行调试。 继续调试之前，确定是否信任相应代码。 代码是你自己编写的吗？ 如果该应用程序正在远程计算机上运行，你是否认识进程的名称？ 如果在本地运行应用程序，请考虑在您的计算机上运行的恶意代码的可能性。 如果您决定是否值得信任的代码，选择**确定**。 否则，选择“取消”。

## <a name="jit_errors"></a> 排查在实时调试 

如果在实时调试不时启动应用程序崩溃，即使它在 Visual Studio 中启用：

- Windows 错误报告无法接管的错误处理您的计算机上。 
  
  若要解决此问题，请使用注册表编辑器中添加**DWORD 值**的**禁用**，与**值数据**的**1**，对以下注册表项：
  
  

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows 错误报告**
    
  - （适用于 64 位计算机）： **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows 错误报告**
  
  有关详细信息，请参阅[。WER 设置](https://docs.microsoft.com/windows/desktop/wer/wer-settings)。
  
- 已知的 Windows 问题可能导致实时中调试程序失败。 
  
  解决方法是添加**DWORD 值**的**自动**，与**值数据**的**1**，对以下注册表项：
  
  
  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**
    
  - （适用于 64 位计算机）： **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

您可能会看到以下错误消息过程中实时调试：

- **无法附加到崩溃进程。指定的程序不是 Windows 或 MS-DOS 程序。**

    调试器尝试附加到另一个用户下运行的进程。

    若要解决此问题，请在 Visual Studio 中，打开**调试** > **附加到进程**，并找到你想要在调试的进程**可用进程**列表。 如果不知道进程名称，查找中的进程 ID **Visual Studio 实时调试器**对话框。 选择中的过程**可用进程**列表，然后选择**附加**。 选择**否**关闭实时中调试器的对话框。

- **无法启动调试器，因为没有用户登录。**

    没有用户登录到控制台，因此没有用户会话来显示实时中调试对话框。

    要解决此问题，请登录到计算机。

- **未注册的类。**

    调试器尝试创建未注册，可能由于安装问题的 COM 类。

    若要解决此问题，请使用 Visual Studio 安装程序重新安装或修复 Visual Studio 安装。

## <a name="see-also"></a>请参阅
- [调试器安全](../debugger/debugger-security.md)
- [调试器基础知识](../debugger/getting-started-with-the-debugger.md)
- [选项，调试，在实时对话框](../debugger/just-in-time-debugging-options-dialog-box.md)
- [安全警告：附加到不受信任的用户所拥有的进程可能很危险。如果以下信息看上去可疑或者你无法确定，请勿附加到此进程](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
