---
title: 调试多个进程 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8be2e91bfc9ed1cf555d24bed08466da69dad9f6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910753"
---
# <a name="debug-multiple-processes"></a>调试多个进程
下面介绍了如何启动调试进程、 进程之间切换、 中断和继续执行、 逐步执行源、 停止调试，并终止进程或与进程分离。  
  
##  <a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a> 配置多个进程的执行行为  
 默认情况下，当多个进程在调试器中运行时，中断、分步和停止调试器命令通常会影响所有进程。 例如，在断点处暂停一个进程时，所有其他进程的执行也会被暂停。 您可以更改此默认行为，以获取对被执行命令目标的更多控制。  
  
1.  单击 **调试 > 选项和设置** 。  
  
2.  在 **调试** ，**常规** 页上，清除 **一个进程中断时则中断所有进程** 复选框。  
  
##  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> 查找源文件和符号 (.pdb) 文件  
 若要浏览进程的源代码，调试器需要访问进程的源文件和符号文件。 请参阅[指定符号 (.pdb) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。  
  
 如果无法访问进程的源文件，可以通过使用反汇编窗口中进行导航。 请参阅[如何： 使用反汇编窗口](../debugger/how-to-use-the-disassembly-window.md)  
  
##  <a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a> 在VS 解决方案中启动多个进程，附加到进程，自动在调试器中启动的进程  
  
-   [在Visual Studio 解决方案中开始调试多个进程](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution)  
  
-   [更改启动项目](#BKMK_Change_the_startup_project)  
  
-   [在解决方案中启动的特定项目](#BKMK_Start_a_specific_project_in_a_solution)  
  
-   [启动解决方案中的多个项目](#BKMK_Start_multiple_projects_in_a_solution)  
  
-   [附加到进程](#BKMK_Attach_to_a_process)  
  
-   [自动在调试器中启动的进程](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
>  调试器不会自动附加到调试进程所启动的子进程中，即使子项目位于同一个解决方案中。 调试子进程：  
> 
> - 在子进程启动后附加到该子进程。  
> 
>   或  
>   -   配置 Windows 以自动启动调试器新实例中的子进程。  
  
###  <a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a> 开始调试 Visual Studio 解决方案中的多个进程  
 如果您在 Visual Studio 解决方案中有多个可独立运行的项目（在独立进程中运行的项目），则可以选择调试器将启动的项目。  
  
 ![更改项目的启动类型](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
####  <a name="BKMK_Change_the_startup_project"></a> 更改启动项目  
 若要更改启动项目的解决方案，在解决方案资源管理器中选择项目，然后从上下文菜单中选择 **设为启动项目** 。  
  
####  <a name="BKMK_Start_a_specific_project_in_a_solution"></a> 在解决方案中启动特定项目  
 若要启动项目的解决方案，无需更改默认启动项目，在解决方案资源管理器中选择项目，然后从上下文菜单中选择 **调试** 。 然后，可以选择**启动新实例**或**单步执行新实例**。  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [启动 VS 解决方案中的多个进程，附加到进程，自动在调试器中启动的进程](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
####  <a name="BKMK_Start_multiple_projects_in_a_solution"></a> 启动解决方案中的多个项目  
  
1. 在解决方案资源管理器中选择该解决方案，然后选择上下文菜单中的 **属性** 。  
  
2. 选择**常见属性**，**启动项目**上**属性**对话框。  
  
3. 对于每个你想要更改的项目，选择**启动**，**启动但不调试**，或**None**。  
  
   ![返回页首](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [启动 VS 解决方案中的多个进程，附加到进程，自动在调试器中启动的进程](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
###  <a name="BKMK_Attach_to_a_process"></a> 附加到进程  
 调试器还可以*附加* 到在 Visual Studio 外部的进程中运行的程序，包括在远程设备运行的程序。 一旦附加到某个程序，就可以使用调试器执行命令、检查程序状态、等等。 检查程序的能力可能会受到某些限制，这取决于程序是否用调试信息生成，是否可以访问程序源代码，以及公共语言运行时 JIT 编译器是否在跟踪调试信息。  
  
 请参阅[附加到正在运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)有关更多信息。  
  
 **附加到在本地计算机中运行的进程**  
  
 单击 **调试 > 附加到进程** 。 在 **附加到进程** 对话框中，从 **可用进程** 列表中选择进程，，然后选择 **附加** 。  
  
 ![附加到进程对话框](../debugger/media/dbg_attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> 自动在调试器中启动的进程  
 有时，你需要调试的程序启动代码，由另一个进程启动的。这样的示例包括服务和自定义安装操作。 在这些情况下，可以让调试器在应用程序启动时启动并自动附加。  
  
1. 启动注册表编辑器 (**regedit.exe**)。  
  
2. 导航到**HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options**文件夹。  
  
3. 选择要在调试器中启动的应用程序的文件夹。  
  
    如果应用的名称未列出作为子文件夹中，选择**Image File Execution Options** ，然后选择**新建**，**密钥**上下文菜单上。 选择新的密钥，然后选择**重命名**上的快捷菜单，然后输入应用的名称。  
  
4. 在应用文件夹的上下文菜单，选择**新建**，**字符串值**。  
  
5. 中的新值的名称更改**新值**到`debugger`。  
  
6. 在调试器项上下文菜单，选择**修改**。  
  
7. 在编辑字符串对话框中，键入`vsjitdebugger.exe`中**数值数据**框。  
  
    ![字符串编辑对话框](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![在 regedit.exe 中的自动调试器启动条目](../debugger/media/dbg_execution_automaticstart_result.png "DBG_Execution_AutomaticStart_Result")  
  
##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> 切换进程，中断并继续执行，逐步执行源  
  
-   [进程之间切换](#BKMK_Switch_between_processes)  
  
-   [中断、 单步执行，并继续命令](#BKMK_Break__step__and_continue_commands)  
  
###  <a name="BKMK_Switch_between_processes"></a> 进程之间切换  
 调试时可以附加到多个进程，但在任何给定时间，调试器中只有一个进程处于活动状态。 可以设置活动或*当前*在调试位置工具栏或在进程**进程**窗口。 若要在两个进程间切换，这两个进程必须处于中断模式。  
  
 **若要设置当前进程**  
  
- 在调试位置工具栏上，选择**进程**若要查看**进程**列表框。 选择要指定为当前进程的进程。  
  
   ![进程间切换](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   如果**调试位置**工具栏不可见，请选择**工具**，**自定义**。 上**工具栏**选项卡上，选择**调试位置**。  
  
- 打开**进程**窗口 (快捷方式**Ctrl + Alt + Z**)，查找想要设置为当前进程的进程，然后双击它。  
  
   ![进程窗口](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")  
  
   当前进程用黄色箭头标记。  
  
  切换到一个项目会将该项目设置为用于调试目的的当前进程。 您查看的所有调试器窗口将显示当前进程的状态，并且所有单步执行命令将仅影响当前进程。  
  
  ![返回页首](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [切换进程，中断并继续执行，逐步执行源](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
###  <a name="BKMK_Break__step__and_continue_commands"></a> 中断、 单步执行，并继续命令  
  
> [!NOTE]
>  默认情况下，中断、继续和分步调试器命令会影响所有正在调试的进程。 若要更改此行为，请参阅[配置多个进程的执行行为](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
|**命令**|**一个进程中断时则中断所有进程**<br /><br /> 已选中（默认值）|**一个进程中断时则中断所有进程**<br /><br /> 清除|  
|-|-|-|  
|**调试**菜单：<br /><br /> -   **全部中断**|所有进程中断。|所有进程中断。|  
|**调试**菜单：<br /><br /> -   **继续**|所有进程继续。|所有挂起的进程继续。|  
|**调试**菜单：<br /><br /> -   **单步执行**<br />-   **逐过程执行**<br />-   **跳出**|在当前进程单步执行时，所有进程将运行。<br /><br /> 然后，所有进程中断。|当前进程单步执行。<br /><br /> 已挂起的进程继续。<br /><br /> 正在运行的进程继续。|  
|**调试**菜单：<br /><br /> -   **单步执行当前进程**<br />-   **逐过程执行当前进程**<br />-   **跳出当前进程**|不可用|当前进程单步执行。<br /><br /> 其他进程保持其现有状态（挂起或运行）。|  
|源窗口<br /><br /> -   **断点**|所有进程中断。|仅源窗口进程中断。|  
|源窗口上下文菜单：<br /><br /> -   **运行到光标处**<br /><br /> 源窗口必须在当前进程中。|当源窗口进程运行到光标处所有进程运行，然后中断。<br /><br /> 然后，所有其他进程中断。|源窗口进程运行到光标处。<br /><br /> 其他进程保持其现有状态（挂起或运行）。|  
|**进程**窗口上下文菜单：<br /><br /> -   **中断进程**|不可用|已选进程中断。<br /><br /> 其他进程保持其现有状态（挂起或运行）。|  
|**进程**窗口上下文菜单：<br /><br /> -   **继续进程**|不可用|已选进程继续。<br /><br /> 其他进程保持其现有状态（挂起或运行）。|  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [切换进程，中断并继续执行，逐步执行源](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
##  <a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a> 停止调试、 终止进程或与进程分离  
  
- [停止、 终止和分离命令](#BKMK_Stop__terminate__and_detach_commands)  
  
  默认情况下，当您选择**调试**，**停止调试**在调试器中打开多个进程时，调试器将终止或与具体取决于该过程如何在打开的所有进程分离调试器：  
  
- 如果在调试器中启动了当前进程，则该进程将终止。  
  
- 如果您已将调试器附加到当前进程，则调试器会与进程分离并使进程保持运行。  
  
  例如，如果您开始调试 Visual Studio 解决方案中的进程，附加到已在运行，另一个进程，然后选择**停止调试**，则在调试会话结束，在 Visual Studio 中启动进程被终止，而您附加的进程将保持运行。 您可以使用以下过程控制停止调试的方法。  
  
> [!NOTE]
>  **一个进程中断时则中断所有进程**选项不影响停止调试或终止进程以及与进程分离。  
  
 **若要更改如何停止调试影响单个进程**  
  
-   打开**进程**窗口 (快捷方式**Ctrl + Alt + Z**)。 选择一个进程，然后选中或清除**调试停止时分离**复选框。  
  
###  <a name="BKMK_Stop__terminate__and_detach_commands"></a> 停止、 终止和分离命令  
  
|**命令**|**说明**|  
|-|-| 
|**调试**菜单：<br /><br /> -   **停止调试**|除非行为被更改，否则**进程**窗口**调试停止时分离**选项：<br /><br /> 1.调试器启动的进程将被终止。<br />2.附加的进程将从调试器分离。|  
|**调试**菜单：<br /><br /> -   **全部终止**|所有进程将终止。|  
|**调试**菜单：<br /><br /> -   **全部分离**|调试器与所有进程分离。|  
|**进程**窗口上下文菜单：<br /><br /> -   **分离进程**|调试器与选定进程分离。<br /><br /> 其他进程保持其现有状态（挂起或运行）。|  
|**进程**窗口上下文菜单：<br /><br /> -   **终止进程**|选定的进程将终止。<br /><br /> 其他进程保持其现有状态（挂起或运行）。|  
|**进程**窗口上下文菜单：<br /><br /> -   **调试停止时分离**|切换的行为**调试**，**停止调试**所选进程：<br /><br /> -Checked： 调试器与进程分离。<br />-清除： 进程将被终止。|  
  
 ![返回页首](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [停止调试、 终止进程或与进程分离](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
## <a name="see-also"></a>请参阅  
 [指定符号 (.pdb) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [将附加到正在运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Navigating through Code with the Debugger](../debugger/navigating-through-code-with-the-debugger.md) （使用调试器浏览代码）  
 [在实时调试](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [调试多线程应用程序](../debugger/debug-multithreaded-applications-in-visual-studio.md)