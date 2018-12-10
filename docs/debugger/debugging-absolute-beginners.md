---
title: 调试零基础入门
description: 如果你第一次开始调试，请学习几个原则，来帮助你在 Visual Studio 的调试模式下运行您的应用程序
ms.custom: ''
ms.date: 07/06/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c10032bf12060c8c5e42f93f6596fe576adfccf
ms.sourcegitcommit: 7bb0225e1fd45999ce09e0b49c2cfae515c27e11
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2018
ms.locfileid: "45612670"
---
# <a name="how-to-debug-for-absolute-beginners"></a>调试如何零基础入门

毫无疑问，我们软件开发人员编写的代码，不会总是如我们所愿执行。 有时它会做一些完全不同的事情！遇到此情况, 下一件事就是找出原因，尽管我们冒着盯着代码看几小时的风险，但它可以更轻松、更高效地使用调试工具、或调试器。

对于调试器，遗憾的是，在我们的代码中，不是所有的问题和 "bug" 都如被施魔法般不可思议地揭开。 *调试* 意味着可在调试工具，比如 Visual Studio ，一步一步跟踪代码的运行，以找出编程错误的确切点。 然后搞清楚代码中需做出的更改，调试工具通常允许您在调试时临时更改代码，然后继续运行程序。

高效地使用调试器，是需要时间和练习来学习的技能，但从根本上说这是每个软件开发人员必备的一项基本技能。 在本文中，我们将介绍调试的核心原理，并提供提示帮你入门。

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>通过向自己提出正确的问题，来理清问题

它有助于理清在尝试修复此错误之前遇到的问题。 我们认为，您已经在代码中遇到了问题，否则您不会在此处尝试找出如何对其进行调试！ 因此，在开始调试之前，请确保您已确定了要解决的问题：

* 您期望代码做什么事情？

* 相反，发生了什么？

    如果运行您的应用程序时遇到了错误（异常），这可是一件好事 ！异常是在代码执行时，通常由于某种类型的错误，遇到的意外事件。 调试工具可帮您在代码中，定位发生异常的确切位置，可帮你调查可能的修复方法。

    如果发生了其它事情，问题的症结是什么？ 是否已猜想到在代码的哪里发生了问题？ 例如，如果你的代码显示一些文本，但文本不正确，您知道要么数据被损坏，要么设置显示文本的代码存在某种类型的 bug。 通过调试器单步跟踪代码，可以检查所有变量的每一次更改，以准确的发现何时以及如何给变量分配一个错误的值。

## <a name="examine-your-assumptions"></a>检查您的假设

调查 bug 或错误之前，想想那些让你期待某一结果的假设。 隐藏或未知假设可能会妨碍识别问题，即使你正使用调试器寻找问题的原因。 可能有一长串假设！以下是几个要问自己的问题，以挑战自己的假设。

* 是否使用正确的 API （比如，正确的对象、 函数、 方法或属性）？ 正在使用的 API 可能没按你所想的那样运行。 （在调试器中检查 API 调用后，修复此问题可能需要访问文档，以帮助识别正确的 API。）

* 是否正确的使用 API？ 您可能使用正确的 API，但没有以正确的方式使用它。

* 代码是否包含任何拼写错误？ 一些拼写错误，比如一些简单的变量名拼写错误，可能很难察觉，特别是使用的语言，不需要在使用变量之前，声明变量时。

* 是否修改了代码，但认为与出现的问题不相关？

* 是否期望对象或变量包含某个值 （或某个类型的值） 不同于实际发生？

* 是否知道代码的目的？ 调试别人的代码通常会更加困难。 如果不是你的代码，则在高效的调试之前，可能需要花时间确切地了解代码的功能。

    > [!TIP]
    > 编写代码时，从小开始，从代码的工作原理开始 ！ （优秀的示例代码对此很有帮助。）有时，从一小段代码开始修复大型或复杂的代码集更容易，这小段代码演示了您试图实现的核心任务。 然后，可以不断地修改或添加代码，测试每个地方的错误。

通过质疑假设，可以减少在代码中查找问题花费时间。 还可减少修复问题所需的时间。

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>通过在调试模式中单步跟踪代码，来找出发生问题的地方

通常运行应用时，您只会在代码运行后，看到错误和不正确的结果。 程序也可能意外终止，而不告诉你为什么。

调试器运行应用程序时，也称为 *调试模式* ，意味着调试器主动监视程序运行时，发生的所有事情。 它还允许您在应用的任何位置暂停，以检查其状态，然后单步跟踪代码每一行，以观看其中发生的一切。

在 Visual Studio 中，使用 **F5** 进入调试模式 (或在调试工具栏中 **调试** > **开始调试** 菜单命令或 **开始调试** 按钮 ![启动调试](../debugger/media/dbg-tour-start-debugging.png "开始调试"))。 如果发生了任何异常，Visual Studio 的异常帮助器将跳转到异常发生的地方，并提供其他有用信息。

如果未发生异常，一个好主意是在代码中查找问题的位置。 在调试器中使用 *断点* ，将给你一个仔细检查代码的机会。 断点是调试时，可信赖的最基本和最重要的功能。 断点指示 Visual Studio 在运行的代码中，哪个位置暂停，以便您可查看变量的值，或内存的行为，或代码的运行顺序。

在 Visual Studio 中，可以在代码行左侧边距中，通过单击来快速设置断点。 或将光标置于该行并按**F9**。

为了说明这些概念，我们带你了解一些已经有几个 bug 的示例代码。 虽然本次我们使用 C# ，但调试功能适用于 Visual Basic、 c + +、 JavaScript、 Python 和其他支持的语言。

### <a name="create-a-sample-app-with-some-bugs"></a>创建示例应用 （包含一些 bug)

接下来，我们将创建包含几个 bug 的应用程序。

1. 您必须已安装了 Visual Studio ，以及已安装 **.NET 桌面开发** 工作负载或 **.NET Core 跨平台开发** 工作负载其中一个，具体的安装哪一个，取决于想要创建的应用类型。

    如果尚未安装 Visual Studio，请访问 [Visual Studio 下载](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 页面，免费安装。

    如果您需要安装工作负载，但已安装了 Visual Studio ，单击**工具** > **获取工具和功能**。 Visual Studio 安装程序将启动。 选择 **.NET 桌面开发** (或 **.NET Core 跨平台开发**) 工作负荷，然后选择**修改**。

1. 打开 Visual Studio，选择**文件** > **新建** > **项目**。

1. 选择用于你应用程序代码的模板。

    对于.NET Framework， 在 **新的项目** 对话框中，从已安装的模板部分中选择 **Visual C#**， **Windows 桌面** ，然后在中间窗格中选择 **控制台应用 (.NET Framework)** 。

    对于.NET Core， 在**新项目**对话框中，从已安装的模板部分中选择 **Visual C#** ， **.NET Core** ，然后在中间窗格中选择 **控制台应用程序 （.NET Core）** 。

    如果看不到这些模板，则必须安装相应的工作负荷 （请参阅前面的步骤）。

1. 在 **名称** 栏位中，输入 **ConsoleApp FirstApp** ，然后单击 **确定** 。

    Visual Studio 在右窗格中的解决方案资源管理器中，将显示创建的控制台项目。

1. 在 *Program.cs* 中，将所有的默认代码替换为以下代码：

    ```csharp
    using System;
    using System.Collections.Generic;
    
    namespace ConsoleApp_FirstApp
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Welcome to Galaxy News!");
                IterateThroughList();
                Console.ReadKey();
            }
    
            private static void IterateThroughList()
            {
                var theGalaxies = new List<Galaxy>
            {
                new Galaxy() { Name="Tadpole", MegaLightYears=400, GalaxyType=new GType('S')},
                new Galaxy() { Name="Pinwheel", MegaLightYears=25, GalaxyType=new GType('S')},
                new Galaxy() { Name="Cartwheel", MegaLightYears=500, GalaxyType=new GType('L')},
                new Galaxy() { Name="Small Magellanic Cloud", MegaLightYears=.2, GalaxyType=new GType('I')},
                new Galaxy() { Name="Andromeda", MegaLightYears=3, GalaxyType=new GType('S')},
                new Galaxy() { Name="Maffei 1", MegaLightYears=11, GalaxyType=new GType('E')}
            };
    
                foreach (Galaxy theGalaxy in theGalaxies)
                {
                    Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
                }
    
                // Expected Output:  
                //  Tadpole  400,  Spiral 
                //  Pinwheel  25,  Spiral 
                //  Cartwheel, 500,  Lenticular
                //  Small Magellanic Cloud .2,  Irregular
                //  Andromeda  3,  Spiral
                //  Maffei 1,  11,  Elliptical
            }
        }
    
        public class Galaxy
        {
            public string Name { get; set; }
    
            public double MegaLightYears { get; set; }
            public object GalaxyType { get; set; }
    
        }
    
        public class GType
        { 
            public GType(char type)
            {
                switch(type)
                {
                    case 'S':
                        MyGType = Type.Spiral;
                        break;
                    case 'E':
                        MyGType = Type.Elliptical;
                        break;
                    case 'l':
                        MyGType = Type.Irregular;
                        break;
                    case 'L':
                        MyGType = Type.Lenticular;
                        break;
                    default:
                        break;
                }
            }
            public object MyGType { get; set; }
            private enum Type { Spiral, Elliptical, Irregular, Lenticular}
        }
    }
    ```

    此代码的目的是在列表中显示 galaxy 名称、到galaxy星系的距离和 galaxy 类型。在调试之前，理解代码的目的很重要。 下面是我们想要在输出中显示的列表，其中一个行的格式：

    *galaxy 名称*，*距离*， *galaxy 类型*。

### <a name="run-the-app"></a>运行应用

1. 在调试工具栏中按**F5**或**开始调试**按钮![启动调试](../debugger/media/dbg-tour-start-debugging.png "开始调试")，位于代码编辑器上方。

    调试器启动该应用时，没有向我们显示异常。但是，在控制台窗口中，看到未预期的输出。下面是预期的输出：

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    但是，相反我们看到：

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType 
    Pinwheel  25,  ConsoleApp_FirstApp.GType 
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    查看输出和我们的代码，我们知道`GType`存储 galaxy 类型的类名。 我们尝试显示实际的 galaxy 类型 （如"循环"），不是类名称 ！

### <a name="debug-the-app"></a>调试应用程序

1. 仍在运行应用时，设置断点旁边的左边距中单击`Console.WriteLine`这行代码中的方法调用。

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }    
    ```

    在设置断点，在左边距中显示的红点。

    因为我们看到的输出中的问题，我们将开始通过查看前面的代码在调试器中设置输出调试。

1. 单击**重新启动**![重新启动应用程序](../debugger/media/dbg-tour-restart.png "RestartApp")调试工具栏中的按钮 (**Ctrl** + **Shift**  +  **F5**)。

    应用程序会在你设置的断点处暂停。 黄色的突出显示指示调试器暂停的位置 （黄色的代码行具有尚未执行）。

1. 将鼠标悬停`GalaxyType`变量在右侧，再到左侧的扳手图标，展开`theGalaxy.GalaxyType`。 可以看到`GalaxyType`包含的属性`MyGType`，并且属性值设置为`Spiral`。

    ![检查变量](../debugger/media/beginners-inspect-variable.png)

    "循环"是实际上你想要打印到控制台的正确值 ！ 因此，您可以在运行应用时访问此值在此代码中的一个不错的起点。 在此方案中，我们将使用不正确的 API。 我们将看到是否我们可以解决此问题时在调试器中运行代码。

1. 在相同的代码中，仍在调试时，将光标放在末尾`theGalaxy.GalaxyType`并将其更改为`theGalaxy.GalaxyType.MyGType`。 尽管可以进行此更改，代码编辑器将显示一个错误，指示它不能编译此代码。

    ![语法错误](../debugger/media/beginners-edit.png)

1. 单击**编辑**中**编辑并继续**消息框。 请参阅现在中的错误消息**错误列表**窗口。 错误指示`'object'`不包含的定义`MyGType`。

    ![语法错误](../debugger/media/beginners-no-definition.png)

    即使我们设置类型的对象与每个 galaxy `GType` (其中包含`MGType`属性)，调试器不能识别`theGalaxy`对象类型的对象作为`GType`。 这是怎么回事？ 你想要浏览设置 galaxy 类型的任何代码。 时执行此操作时，可以看到`GType`类肯定有的一个属性`MyGType`，但某些内容不正确。 有关的错误消息`object`证明是线索; 到语言解释器，似乎是类型的对象类型`object`而不是类型的对象`GType`。

1. 通过代码与设置 galaxy 类型相关的查找，找到`GalaxyType`的属性`Galaxy`类指定为`object`而不是`GType`。

    ```csharp
    public object GalaxyType { get; set; }     
    ```

1. 将上面的代码更改为：

    ```csharp
    public GType GalaxyType { get; set; }     
    ```

1. 单击**重新启动**![重新启动应用程序](../debugger/media/dbg-tour-restart.png "RestartApp")调试工具栏中的按钮 (**Ctrl** + **Shift**  +  **F5**) 重新编译代码并重新启动。

    现在，调试器暂停上`Console.WriteLine`，你可以通过将鼠标悬停在`theGalaxy.GalaxyType.MyGType`，并确保正确设置值。

1. 通过单击左边距中的断点圆上删除断点 (或右键单击，然后选择**断点** > **删除断点**)，然后按**F5**以继续。

    应用程序运行，并显示输出。 它看起来很不错现在，但请注意的一点;预期小 Magellanic 云 galaxy 才会显示为不定期星系在控制台输出中，但它显示了没有 galaxy 类型根本。

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. 在此代码行上设置断点。

    ```csharp
    public GType(char type)
    ```

    此代码是 galaxy 类型设置，因此，我们想要更详细地介绍它。

1. 单击**重新启动**![重新启动应用程序](../debugger/media/dbg-tour-restart.png "RestartApp")调试工具栏中的按钮 (**Ctrl** + **Shift**  +  **F5**) 重新启动。

    设置了断点的代码行上暂停调试器。  

1. 将鼠标悬停`type`变量。 您看到的值`S`（后跟的字符代码）。 你感兴趣的值为`I`，因为您知道这是不定期 galaxy 类型。

1. 按**F5**并将鼠标悬停`type`再次变量。 重复此步骤，直到您看到的值`I`在`type`变量。

    ![检查变量](../debugger/media/beginners-inspecting-data.png)

1. 现在，请按**F11** (**调试** > **单步执行**或**单步执行**中调试工具栏按钮)。

    **F11**使调试器 （和执行代码） 一次一个语句。 **F10** (**单步跳过**) 是类似的命令，并学习如何使用调试器时都非常有用。

1. 按**F11**直到中的代码行上停止`switch`I 的值的语句。 这里，您将看到清除问题导致的拼写错误。 预期以转到此处设置的代码`MyGType`为异常 galaxy 类型，但调试器改为完全跳过此代码并上暂停`default`一部分`switch`语句。

    ![发现拼写错误](../debugger/media/beginners-typo.png)

    查看代码，请参阅中的存在拼写错误`case 'l'`语句。 它应该是`case 'I'`。

1. 在代码中单击`case 'l'`并将其替换为`case 'I'`。

1. 删除断点，然后依次**重新启动**按钮以重新启动该应用程序。

    现在已修复 bug，请参阅预期的输出 ！

    按任意键以完成应用程序。

## <a name="summary"></a>总结

查看问题，请使用的调试器和[单步命令](../debugger/navigating-through-code-with-the-debugger.md)如**F10**并**F11**若要查找的问题的代码区域。

> [!NOTE]
> 如果很难确定出现问题的代码区域，在之前出现此问题，运行的代码中设置断点，然后使用单步执行命令，直到看到问题清单。 此外可以使用[跟踪点](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)来记录向消息**输出**窗口。 通过查看记录的消息 （并且注意到的消息尚未登录 ！），通常可以隔离的问题的代码区域。 您可能需要多次重复此过程，以缩小它。

发现的问题的代码区域，使用的调试器进行调查。 若要查找问题的原因，请在调试器中运行你的应用时检查问题的代码：

* [检查变量](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)并检查它们是否包含应包含的值的类型。 如果您发现错误的值，找出其中设置值不正确 (若要查找的值已设置，您可能需要重新启动调试器，看看[调用堆栈](../debugger/how-to-use-the-call-stack-window.md)，和 / 或)。

* 检查你的应用程序是否执行预期的代码。 （例如，在示例应用程序，我们将 galaxy 类型设置为异常，则 switch 语句的代码但应用程序跳过由于拼写错误的代码。）

> [!TIP]
> 使用调试程序来帮助你发现 bug。 调试工具可以发现 bug*为您*仅在知道代码的意图。 如果您开发人员，表达该意图，一种工具可以只知道代码的意图。 编写[单元测试](../test/improve-code-quality.md)是如何实现的。

## <a name="next-steps"></a>后续步骤

在本文中，已了解的一些常规调试概念。 接下来，您可以开始学习如何使用 Visual Studio 进行调试。

> [!div class="nextstepaction"]
> [了解如何使用 Visual Studio 进行调试](../debugger/getting-started-with-the-debugger.md)
