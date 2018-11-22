---
title: 通过Visual Studio 调试器单步调试 |Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f4091b929c20258d1a491082fcb7e50c24d0bbc6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933763"
---
# <a name="navigate-code-with-the-visual-studio-debugger"></a>通过Visual Studio 调试器单步调试

Visual Studio调试器可以帮助你通过单步调试检查一个应用的状态和执行流程。可以通过快捷键、调试命令、 断点、和其它功能快速的校对需要检验的代码。熟悉调试器导航命令和快捷键可以让你更快的发现和解决应用程序遇到的问题。如果现在是你第一次尝试调试代码，你可能需要在继续读本篇文章之前去阅读[使用Visual Studio写出最好的C#代码](../debugger/write-better-code-with-visual-studio.md)和[调试零基础入门](../debugger/debugging-absolute-beginners.md)。
  
## 调试基础

按 **F5**， 选择 **调试** > **启动调试**, 或者选择Visual Studio工具栏中的绿色箭头，启动后调试器将附加到你的应用。
  
 ![DBG&#95;Basics&#95;Start&#95;Debugging](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")  

在进行调试时，下一步将执行的代码会黄色高亮。
  
 ![DBG&#95;Basics&#95;Break&#95;Mode](../debugger/media/dbg_basics_break_mode.png "DBG_Basics_Break_Mode")  

调试器的绝大多数窗口，像 **模块** 和 **监视** 窗口，只在调试器运行时可用。某些调试器功能，比如在**局部变量**窗口显示变量值或者在**监视**窗口中计算表达式, 只有调试器在某个断点暂停后可用（也被叫做*中断模式*）。

在中断模式中，当应用程序执行状态被挂起时函数、变量和对象驻留在内存中。你可以通过检查元素的位置和状态来寻找访问破坏和bug。对于某些类型的项目，你可以在中断模式下对应用程序进行调整。如果需要展示这些功能的视频, 请看 [调试器入门](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).

如果你在没有源代码和符号文件被加载(*.pdb*)的情况下中断，调试器会显示 **未找到源文件** 或者 **未找到符号文件** 页面来帮你找到和加载这些文件。请看 [指定符号(.pdb)和源代码文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。如果你没有加载需要的符号和源代码文件，你仍然可以在**反汇编**窗口中调试汇编指令。 

你不需要每次启动调试都重新打开应用程序。你也可以按**F11**[逐语句](#BKMK_Step_into__over__or_out_of_the_code), 按 **F10** [逐过程](#BKMK_Step_over_Step_out), 或者[运行到指定位置或者函数](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All).    

##  逐步执行代码


调试器步骤命令帮助你检查你的应用程序状态，或者发现更多关于它的执行流程。 

如果你需要找到应用程序的入口点, 按**F10**或者**F11**启动。  

### <a name="BKMK_Step_into__over__or_out_of_the_code"></a> 在每行代码中逐语句跟踪 

在调试时使用**调试** > **步入**，或者按**F11**，将在每一行代码或者语句上停止时。  

调试器逐语句执行代码段， 而不是实际行。下例中`if`子语句写在单独一行：
  
  ```csharp  
  int x = 42;  
  string s = "Not answered";  
  if( int x == 42) s = "Answered!";  
  ```  
  
  ```vb  
  Dim x As Integer = 42  
  Dim s As String = "Not answered"  
  If x = 42 Then s = "Answered!"  
  ```  


然而，当你步入这行代码时, 调试器将判断条件做为一步，结果做为另一步。在本例中， 判断条件结果为true.  
  
在一个内嵌的函数调用中, **逐语句** 在一个最深处嵌套函数中进行逐语句调试。For example，如果你正在调用像 `Func1(Func2())` 函数时使用 **逐语句**，调试器将步入`Func2`函数。 

> [!TIP]
>在执行每行代码时，你可以悬停在变量，以查看它们的值，或者可以使用[局部变量](../debugger/autos-and-locals-windows.md) 和 [监视](watch-and-quickwatch-windows.md) 窗口查看变量的变化。你可以逐语句跟踪函数的可视化调用堆栈。请参阅 [当调试时在调用堆栈上映射方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md). 
  
##  <a name="BKMK_Step_over_Step_out"></a> 忽略某些函数进行单步调调试

 当在调试器中运行代码，通常您会意识到不需要查看特定函数中会发生什么情况 (不关心或知道其工作方式，类似于经过全面测试的库代码)。 使用以下命令以跳过代码 （函数仍可以执行，当然，但调试器跳过它们）。  
  
|键盘命令|菜单命令|描述|  
|----------------------|------------------|-----------------|  
|**F10**|**逐过程**|如果当前行包含函数调用中，**单步跳过**运行的代码则被调用的函数返回后，在第一行代码处挂起执行。|  
|**Shift+F11**|**跳出**|**单步跳出**会继续运行代码，当前函数返回 （通过当前函数调试器跳） 时挂起执行。|  
  
> [!TIP]
>  如果你需要在应用中查找的入口点，请先使用**F10**或**F11**。 检查应用程序状态或尝试找出有关其执行流的详细信息时，这些命令很有帮助。  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> 运行到特定位置或函数  
 调试代码的首选的方法，这些方法时通常很有用知道具体的代码你想要检查，或至少知道你想要开始调试。  
  
-   **在代码中设置断点**  
  
     若要在代码中设置简单断点，请打开 Visual Studio 编辑器中的源文件。 你想要暂停执行、，然后右键单击代码窗口以查看上下文菜单选择中的代码行上设置光标**断点 > 插入断点**(或按**F9**)。 调试器挂起执行权限才能执行行。  
  
     ![设置断点](../debugger/media/dbg_basics_setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Visual Studio 中的断点提供了一组丰富的附加功能，例如条件断点和跟踪点。 请参阅[使用断点](../debugger/using-breakpoints.md)。  
  
-   **运行到光标处**  
  
     若要运行到光标位置，请将光标放在源窗口中可执行的代码行上。 在编辑器的上下文菜单 （在编辑器中右键单击），选择**运行到光标处**。 这就像设置临时断点。

-   **运行时单击** 

    若要运行到在调试器中暂停时在代码中的点，请选择**执行运行到此处**绿色箭头图标 （你将看到一行代码将鼠标悬停时图标）。 这消除了需要设置临时断点。

    ![调试器的运行时单击](../debugger/media/dbg-run-to-click.png "DbgRunToClick") 

    > [!NOTE]
    > **运行时单击**中的新[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。
  
-   **手动中断代码**  
  
     若要在正在执行的应用程序上，中断下一个可用的代码行，请选择 **“调试”**、 **“全部中断”** （键盘： **Ctrl+Alt+Break**）。 
  
     如果中断正在执行的代码，而没有响应的源或符号 (.pdb) 文件，调试器将显示“未找到源文件”  或“未找到符号”  页面，帮助你找到相应的文件。 请参阅[指定符号 (.pdb) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。 如果你无法访问支持文件，仍可以在“反汇编”窗口中调试汇编指令。  
  
-   **在调用堆栈上运行到函数**  
  
     在中**调用堆栈**窗口 （调试时可用），选择函数，右键单击并选择**运行到光标处**。 若要直观地跟踪调用堆栈，请参阅[调试时映射调用堆栈上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。  
  
-   **运行到通过名称指定的函数**  
  
     可以让调试器在运行你的应用程序，直至到达指定的函数。 你可以通过名称指定函数，也可以从调用堆栈中选择函数。  
  
     若要通过名称指定函数，请选择 **“调试”**、 **“新建断点”**、 **“在函数处中断”**，然后输入函数名称和其他标识信息。  
  
     ![新建断点对话框](../debugger/media/dbg_execution_newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     如果是重载函数，或者函数在多个命名空间，你可以在 **“选择断点”** 对话框中选择想要的函数。  
  
     ![选择断点对话框](../debugger/media/dbg_execution_overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> 移动指针以更改执行流  
 调试器暂停时，您可以移动指令指针来设置要执行的代码的下一个语句。 源窗口或“反汇编”窗口的空白区域中的黄色箭头标记要执行的下一条语句的位置。 通过移动此箭头，可以跳过部分代码或返回到以前执行过的行。 在某些情况下可以使用此方法，例如，跳过包含已知 bug 的代码段。  
  
 ![将指针移](../debugger/media/dbg_basics_example3.gif "DBG_Basics_Example3")
  
 要设置下一条要执行的语句，请使用以下过程之一：  
  
-   在源窗口中，将黄色箭头拖动希望执行下一语句的位置，该位置应在同一源文件。  
  
-   在源窗口中，将光标放置在你想要执行的下，右键单击并选择的行**设置下一语句**。  
  
-   在反汇编窗口中，将光标放置在你想要执行的下，右键单击程序集指令上并选择**设置下一语句**。  
  
> [!CAUTION]
>  设置下一条语句将导致程序计数器直接跳到新位置。 使用此命令时要小心：  
> 
> - 不执行旧执行点和新执行点之间的指令。  
>   -   如果向后移动执行点，则不撤消插入的指令。  
>   -   将下一条语句移动到另一个函数或范围通常会导致调用堆栈损坏，导致一个运行时错误或异常。 如果尝试将下一条语句移动到另一个范围，则调试器将打开一个含有警告的对话框，并提供一个取消该操作的机会。 在 Visual Basic 中，不能将下一条语句移动到另一个范围或函数。  
>   -   在本机 C++ 中，如果已启用运行时检查，设置下一条语句会导致执行到达方法的结尾时引发异常。  
>   -   当启用“编辑并继续”时，如果你进行了“编辑并继续”无法立即重新映射的编辑，那么 **“设置下一语句”** 将失败。 例如，如果你编辑了 catch 块中的代码，将发生这种情况。 在此情况下，您将看到错误消息，告诉你操作不受支持。  
> 
> [!NOTE]
>  在托管代码中，在以下情况下不能移动下一条语句：  
> 
> - 下一条语句与当前语句不在同一个方法中。  
>   -   使用实时调试启动调试。  
>   -   正在展开一个调用堆栈。  
>   -   已引发一个 System.StackOverflowException 或 System.Threading.ThreadAbortException 异常。  
  
 应用程序处于活动运行状态时不能设置下一条语句。 要设置下一语句，调试器必须处于中断模式。  
  
## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>单步执行非用户代码  
 默认情况下，调试器尝试显示只有你应用的代码在调试时，该域由调试器设置调用*仅我的代码*。 (请参阅[仅我的代码](../debugger/just-my-code.md)若要查看这对不同项目类型和语言的工作方式以及可以如何自定义行为。)但是，有时调试时，你可能想要查看框架代码、 第三方库代码中或调用到操作系统 （系统调用）。  
  
 您可以关闭仅我的代码通过转到**工具** > **选项** > **调试**并清除**启用 '仅我的代码'** 复选框。  
  
 当禁用仅我的代码时，调试器可以单步执行非用户代码，在调试器窗口中显示非用户代码。  
  
> [!NOTE]
>  设备项目不支持“仅我的代码”。  
  
 **单步执行系统调用**  
  
 如果你已加载系统代码的调试符号，并且未启用仅我的代码，您可以单步执行系统调用中，正如其他任何调用。  
  
 若要访问 Microsoft 符号文件，请参阅[使用符号服务器查找不在本地计算机上的符号文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine)中[指定符号 (.pdb) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)主题。  
  
 在调试时加载特定系统组件的符号：  
  
1.  打开模块窗口 (键盘： **Ctrl + Alt + U**)。  
  
2.  选择要加载符号的模块。  
  
     查看 **“符号状态”** 列可以了解哪些模块加载了符号。  
  
3.  在上下文菜单中选择 **“加载符号”** 。  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> 在托管代码中逐语句跟踪属性和运算符  

 默认情况下，调试器将逐过程执行托管代码中的属性和运算符。 在多数情况下，这会提供较好的调试体验。 若要启用逐语句跟踪属性或运算符，请选择**调试** > **选项**。 在 **“调试”** > **“常规”** 页面上，清除 **“逐过程执行属性和运算符(仅限托管)”** 复选框。

 ## 请参阅
 [什么是调试？](../debugger/what-is-debugging.md)  
 [使用Visual Studio写出最好的C#代码](../debugger/write-better-code-with-visual-studio.md)  
 [第一次了解调试](../debugger/debugger-feature-tour.md) 