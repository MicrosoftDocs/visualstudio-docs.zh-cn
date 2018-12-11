---
title: 调试 DLL 项目 |Microsoft Docs
ms.custom: ''
ms.date: 11/06/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96dc4277bfdc783d969a2e98fb93fcc5975e9ad7
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607622"
---
# <a name="debug-dlls-in-visual-studio"></a>调试 Visual Studio 中的 Dll

DLL （动态链接库） 是一个包含代码和数据的库，可被多个程序使用。 您可以使用 Visual Studio 来创建、 构建、 配置，并调试 Dll。 

## <a name="create-a-dll"></a>创建一个 DLL

以下 Visual Studio 项目模板可以创建 Dll:

- C#或 Visual Basic 类库 
- C#Visual Basic Windows 窗体控件 (WCF) 库或 
- C + + 动态链接库 (DLL)

有关详细信息，请参阅[MFC 调试技术](../debugger/mfc-debugging-techniques.md)。

调试 WCF 库类似于调试类库。 有关详细信息，请参阅[Windows 窗体控件](/dotnet/framework/winforms/controls/index)。  

通常从另一个项目中调用 DLL。 调试时调用项目，取决于 DLL 配置，可以单步跟踪和调试 DLL 代码。 

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> DLL 的调试配置

当你使用 Visual Studio 项目模板创建一个应用程序、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]自动为调试和发布生成配置创建所需的设置。 如有必要，您可以更改这些设置。 有关详细信息，请参阅以下文章：

- [C++ 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [C#调试配置的项目设置](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic 调试配置的项目设置](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [如何： 设置调试和发布配置](../debugger/how-to-set-debug-and-release-configurations.md)  
  
### <a name="set-c-debuggableattribute"></a>设置 c + + DebuggableAttribute

为了使调试器附加到 c + + DLL，c + + 代码必须发出`DebuggableAttribute`。 

**若要设置`DebuggableAttribute`:**

1. 选择中的 c + + DLL 项目**解决方案资源管理器**，然后选择**属性**图标，或右键单击该项目并选择**属性**。 
   
1. 在**属性**窗格下**链接器** > **调试**，选择**是 (/ ASSEMBLYDEBUG)** 为**可调试的程序集**。 

有关详细信息，请参阅[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)。  

### <a name="vxtskdebuggingdllprojectsexternal"></a> 设置 C/c + + DLL 文件位置 

若要调试外部 DLL，调用项目必须能够找到 DLL、其[.pdb 文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)、和 DLL 要求的任何其他文件。 可以创建自定义生成任务将这些文件复制到您 *\<项目文件夹 > \Debug* 输出文件夹中，也可以手动复制文件。

对于 C/C++ 项目，可以在项目属性页中设置标头和 LIB 文件位置，而不必将其复制到输出文件夹。 

**若要设置 C/C++ 标头和 LIB 文件位置：**

1. 选择 C/C++ DLL 项目中的**解决方案资源管理器**，然后选择**属性**图标，或右键单击该项目并选择**属性**。 
   
1. 在顶部**属性**窗格下**配置**，选择**所有配置**。
   
1. 在 **C/C++** > **常规** > **附加包含目录** 中，指定具有标头文件的文件夹。
   
1. 在 **链接器** > **常规** > **附加库目录** 中，指定具有 LIB 文件的文件夹。 
   
1. 在 **链接器** > **输入** > **附加依赖项** 中，指定完整路径和 LIB 文件的文件名。

1. 选择 **确定** 。

有关C++项目设置的详细信息，请参阅[属性页 （Visual C++）](/cpp/ide/property-pages-visual-cpp)。
  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> 生成调试版本  

请确保在开始调试之前生成的 dll 的调试版本。 若要调试 DLL，调用应用程序必须能够找到其要求的[.pdb 文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)和 DLL 以及任何其他文件。 

可以创建自定义生成任务复制 DLL 文件到您*\<调用项目文件夹 > \Debug*输出文件夹中，也可以手动复制文件存在。

请确保在正确的位置中调用该 DLL。 这似乎很明显，但如果调用应用找到并加载 DLL 的不同副本时，调试器将永远不会命中您设置的断点。 

##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> 调试 DLL  

不能直接运行 DLL。 它必须由调用应用程序，通常 *.exe*文件。 有关详细信息，请参阅[创建和管理 Visual C++ 项目](/cpp/ide/creating-and-managing-visual-cpp-projects)。 

若要调试 DLL，你可以[从调用应用开始调试](#vxtskdebuggingdllprojectsthecallingapplication)，或通过指定调用其的应用[从DLL 项目开始调试](how-to-debug-from-a-dll-project.md)。 此外可以使用调试器[即时窗口](#vxtskdebuggingdllprojectstheimmediatewindow)要在设计时计算的 DLL 函数或方法，而无需使用调用应用。

有关详细信息，请参阅[开始使用调试器](getting-started-with-the-debugger.md)。

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> 从调用应用程序开始调试

调用 DLL 的应用可以是：  
  
- 从DLL相同或不同解决方案 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目的应用程序。  
- 一个在测试或生产计算机上，已部署且正在运行中的应用程序。  
- 在 web 中通过 URL 访问。  
- 使用嵌入 DLL 中的 web 应用。  
  

从调用应用程序调试 DLL，你可以：  
  
- 打开调用应用程序项目，并开始通过选择调试**调试** > **开始调试**或按**F5**。  

  或  

- 附加到测试或生产计算机上已部署且正在运行的应用。 在网站或在 web 应用中，使用此 Dll 中的方法。 有关详细信息，请参阅[如何： 附加到正在运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
在开始调试调用应用程序之前，请在 DLL 中设置断点。 请参阅[使用断点](../debugger/using-breakpoints.md)。 DLL 断点命中时，可以单步跟踪代码，观察每个行的操作。 有关详细信息，请参阅[在调试器中浏览代码](../debugger/navigating-through-code-with-the-debugger.md)。
  
在调试期间，可以使用 **模块** 窗口在应用加载时验证 Dll 和 *.exe* 文件。 若要在调试时，打开 **模块** 窗口，选择**调试** > **窗口** > **模块**。 有关详细信息，请参阅[如何： 使用模块窗口](../debugger/how-to-use-the-modules-window.md)。 

###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> 使用即时窗口  

可以使用**即时**窗口，以在设计时计算 DLL中 函数或方法。 **即时**窗口充当的角色调用的应用。 

>[!NOTE]
>可以大多数项目类型设计时使用 **即时** 窗口。 它目前不支持.NET Core、 SQL 或 web 项目。

例如，若要在 `Class1 ` 类中测试名为 `Test` 的方法:

1. 打开 DLL 项目， 通过选择**调试** > **窗口** > **即时**或按**Ctrl**+**Alt**+**I** 打开 **即时** 窗口。  
   
1. 在 **即时** 窗口中键入以下C#代码，实例化`Class1`类型对象，然后按**Enter**。 此托管的代码也适用于C#和 Visual Basic，使用合适的语法更改：  
   
   ```csharp
   Class1 obj = new Class1();  
   ```  
  
   在 C# 中，所有名称必须是全限定名称。语言服务尝试计算表达式的值时，所有使用的方法或变量必须在当前作用域和上下文中。  
   
1. 假设 `Test` 带有一个 `int` 参数，使用 **即时** 窗口计算 `Test` ：  
   
   ```csharp
   ?obj.Test(10);  
   ```  
   
   在 **即时** 窗口中打印结果。  
   
1. 你可以放置一个断点在 `Test` 方法内继续调试，然后再次计算函数。  
   
   命中断点后，可以单步跟踪`Test`。 当执行离开后`Test`，调试器将在设计模式下返回。

##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> 混合模式调试  

可以为托管或本机代码中的 DLL 编写调用应用。 如果本机应用调用托管 DLL，并且你想要调试两者，则可以在项目属性中同时启用托管和本机调试器。 确切流程取决于是否想要从 DLL 项目或调用应用程序项目开始调试。 有关详细信息，请参阅[如何： 在混合模式下调试](../debugger/how-to-debug-in-mixed-mode.md)。 

此外可以调试托管的调用项目中的本机 DLL。 有关详细信息，请参阅[如何调试托管和本机代码](how-to-debug-managed-and-native-code.md)。 

## <a name="see-also"></a>请参阅  
 [调试托管的代码](../debugger/debugging-managed-code.md)   
 [Visual c + + 项目类型](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#F#，和 Visual Basic 项目类型](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C + + 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [项目设置为C#调试配置](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 调试配置的项目设置](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [调试器安全](../debugger/debugger-security.md)
