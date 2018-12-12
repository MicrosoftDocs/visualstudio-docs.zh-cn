---
title: 编辑并继续 （Visual C++） |Microsoft Docs
ms.custom: ''
ms.date: 05/31/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 7e468f75abbadbe46ea973a5c04d2e286fcfaca5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867697"
---
# <a name="edit-and-continue-visual-c"></a> 编辑并继续 (Visual C++)
可以使用 Visual C++ 项目中的“编辑并继续”。 请参阅[(C++)支持的代码更改](../debugger/supported-code-changes-cpp.md)有关限制编辑并继续的信息。
  
有关 Visual Studio 2015 Update 3 的改进的详细信息，请参阅[C++编辑并继续在 Visual Studio 2015 Update 3](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)。  
  
 在 Visual Studio 2013 Update 3 中引入的编译器选项 [/Zo （增强优化调试）](/cpp/build/reference/zo-enhance-optimized-debugging) , 无需[/Od （禁用 （调试））](https://msdn.microsoft.com/library/aafb762y.aspx)选项，将在编译二进制文件时将其他信息添加到 .pdb （符号） 文件。  
  
 **/Zo** 禁用编辑并继续。 请参阅[如何： 调试优化的代码](../debugger/how-to-debug-optimized-code.md)。  
  
##  <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> 启用或禁用“编辑并继续”  
 如果要对代码进行编辑而又不希望在当前调试会话过程中应用这些编辑，则可以禁用自动调用“编辑并继续”。 也可以重新启用“编辑并继续”的自动操作。

> [!IMPORTANT]
> 有关所需的生成设置和功能兼容性的其他信息，请参阅 [使用 Visual Studio 2015 Update 3 编辑并继续 C++] (https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/。
  
1. 如果您在调试会话，停止调试 (**Shift + F5**)。

2. 在 **“工具”** 菜单上，选择 **“选项”**。
  
3. 在**选项**对话框中，选择**调试 > 常规**。

4. 若要启用，请选择**启用编辑并继续**。 若要禁用，请清除该复选框。
  
5. 在 **编辑并继续** 组中，选中或取消选中 **启用本机编辑并继续** 复选框。  
  
   更改此设置将影响工作中的所有项目。 更改此设置后，不必重新生成应用程序。 如果使用命令行或makefile生成应用程序，但在 Visual Studio 环境中调试，如果您设置 **/ZI**选项，仍可以使用编辑并继续。  
  
##  <a name="BKMK_How_to_apply_code_changes_explicitly"></a> 如何显式地应用代码更改

 在 Visual C++ 中，“编辑并继续”可以以两种方法应用代码更改。当使用命令或显式使用 **“应用代码更改”** 命令，代码可以隐式的应用更改。  
  
 当显式应用代码更改时，程序保持在中断模式-不会执行。  
  
-   若要显式应用代码更改，在 **调试** 菜单上，选择 **应用代码更改**。  
  
##  <a name="BKMK_How_to_stop_code_changes"></a> 如何停止代码更改  
 当“编辑并继续”处于应用代码更改的过程中时，您可以停止该操作。  
  
 要停止应用代码更改：  
  
- 在 **调试** 菜单中选择 **停止应用代码更改**。  
  
  该菜单项仅在应用代码更改后才可见。  
  
  如果选择了该选项，就不会进行任何代码更改。  
  
##  <a name="BKMK_How_to_reset_the_point_of_execution"></a> 如何重置执行点  
 在“编辑并继续”应用更改时，一些代码更改会使执行点移动到新的位置。 “编辑并继续”尽可能正确地放置执行点，但是并非所有情况下的结果都正确。  
  
 在 Visual C++ 中，当执行点发生更改时，会显示一个对话框来告知您此情况。 在继续调试之前，应验证位置是否正确。 如果位置不正确，则使用 **“设置下一语句”** 命令。 有关详细信息，请参阅 [设置下一个要执行的语句](https://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute)。  
  
##  <a name="BKMK_How_to_work_with_stale_code"></a> 如何使用陈旧代码  
 在某些情况下，“编辑并继续”无法将代码更改立即应用于可执行文件，但如果您继续调试，则可能会在稍后应用代码更改。 当编辑某个调用当前函数的函数，或将多于 64 个字节的新变量添加到调用堆栈上的函数时，就会发生这种情况。  
  
 在这种情况下，调试器会继续执行原始代码，直至可以应用更改。 陈旧的代码在单独的源窗口中作为临时源文件窗口显示，并带有一个类似 `enc25.tmp`的标题。 编辑过的源继续在原始源窗口中显示。 当您尝试编辑陈旧的代码时，会显示一条警告信息。  
  
## <a name="see-also"></a>请参阅  
 [受支持的代码更改 (C++)](../debugger/supported-code-changes-cpp.md)