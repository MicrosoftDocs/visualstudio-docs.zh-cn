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

毫无疑问，我们软件开发人员编写的代码，不会总是如我们所愿执行。 有时它会做一些完全不同的事情！遇到此情况, 下一件事就是找出原因，尽管我们冒着盯着代码看几小时的风险，但它可以更轻松、 更高效地使用调试工具、或调试器。

对于调试器，遗憾的是，在我们的代码中，不是所有的问题和 "bug" 都如魔法般不可思议地揭开。 *调试* 意味着可在调试工具，比如 Visual Studio ，一步一步跟踪代码的运行，以查找编程错误的确切点。 然后明白在代码中需做出的更改，调试工具通常允许您调试时临时更改，然后可以继续运行程序。

有效地使用调试器，是需要时间和练习来学习的技能，但从根本上说是每个软件开发人员的一项基本技能。 在本文中，我们将介绍调试的核心原理，并提供提示帮助你入门。

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>通过正确的问题问自己，明确问题

它有助于阐明在尝试修复此错误之前遇到了问题。 我们希望，您已经遇到了问题在代码中，否则您不会在此处尝试找出如何对其进行调试 ！ 因此，在开始调试之前，请确保您已确定尝试解决的问题：

* 您期望什么呢代码，以进行？

* 相反，有什么变化？

    如果运行您的应用程序时遇到了错误 （异常），这可以是一件好事 ！ 例外情况是运行代码，通常某种类型的错误时遇到意外的事件。 调试工具可以帮助您在代码中发生异常的确切位置，可帮助你调查可能的修复方法。

    如果其他操作发生问题的症状是什么？ 你已怀疑你的代码中出现此问题？ 例如，如果你的代码显示一些文本，但文本不正确，您知道是你的数据已损坏，或设置显示文本的代码存在某种类型的 bug。 通过单步执行代码在调试器中，可以到变量来发现的确切时间，以及如何分配不正确的值来检查每个更改。

## <a name="examine-your-assumptions"></a>检查您的假设

调查 bug 或错误之前，请考虑你预期的某些结果所做的假设。 隐藏或未知假设可以会妨碍识别问题，即使你要在调试器中就可在问题的原因。 可能有一长串的可能假设 ！ 以下是几个问题要问自己，怀疑假设。

* 正在使用正确的 API （即，右对象、 函数、 方法或属性）？ 正在使用的 API 可能不会执行您认为它。 （检查在调试器中的 API 调用后，解决此问题可能需要转至文档以帮助识别正确的 API。）

* 您是否正在正确使用 API？ 您可能使用 API 的权限，但没有使用它以正确的方式。

* 你的代码是否包含任何拼写错误？ 若要查看，尤其在使用不需要用完之前声明的变量的语言时，很难一些拼写错误，如简单的变量名拼写错误。

* 未对代码进行更改并认为它是与您要查看的问题不相关？

* 您是否期望的对象或变量来包含特定值 （或某个特定类型的值） 不同于实际发生？

* 您是否知道代码的含义？ 通常会更难进行调试其他人的代码。 如果不是你的代码，则可能需要花时间学习完全什么代码执行之前可以有效地调试。

    > [!TIP]
    > 编写代码时，开始很小，并开始使用代码的工作原理 ！ （优秀的示例代码就很有帮助。）有时，它是更轻松地通过一小段代码，演示你尝试实现的核心任务与启动修复的大型或复杂的一组代码。 然后，可以修改或添加代码以增量方式，每个点有错误的测试。

质疑假设，可能会减少在代码中查找问题所需的时间。 此外可缩短解决问题所需的时间。

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>逐句通过代码在调试模式下，若要查找出现问题

通常情况下运行应用时，您看到错误和不正确的结果仅后的代码运行。 程序还可能会意外终止而不告诉你为什么中。

运行应用程序中调试程序，也称为*调试模式下*，意味着调试器主动监视发生在程序运行的所有内容。 它还允许您暂停检查其状态，并将然后单步执行代码行的行，以观看每个细节，因为它发生的任何点处的应用。

在 Visual Studio 中，输入调试模式下使用**F5** (或**调试** > **开始调试**菜单命令或**开始调试**按钮![启动调试](../debugger/media/dbg-tour-start-debugging.png "开始调试")) 在调试工具栏中。 如果发生任何异常时，Visual Studio 的异常帮助器将转到异常的发生并提供其他有用信息的确切点。

如果未收到异常，您很可能是个好主意查找在代码中问题的位置。 这在其中使用*断点*调试器使自己更仔细检查你的代码有机会。 断点是可靠调试的最基本和最重要的功能。 断点指示其中 Visual Studio 应暂停运行中的代码，以便您可以看看变量值或内存的行为或运行代码的序列。

在 Visual Studio 中，可以通过在代码行旁的左边距中单击来快速设置断点。 或将光标置于行并按**F9**。

为了说明这些概念，我们会指导你已有几个 bug 的一些示例代码。 我们使用的 C# 中，但调试功能适用于 Visual Basic、 c + +、 JavaScript、 Python 和其他支持的语言。

### <a name="create-a-sample-app-with-some-bugs"></a>创建示例应用 （具有一些 bug)

接下来，我们将创建具有几个 bug 的应用程序。

1. 您必须安装 Visual Studio 和任何一个。**NET 桌面开发**工作负荷或。**.NET Core 跨平台开发**安装工作负载，具体的应用类型取决于想要创建。

    如果尚未安装 Visual Studio，请转到 [Visual Studio 下载](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)页免费安装。

    如果您需要安装工作负载，但已有 Visual Studio 中，单击**工具** > **获取工具和功能**。 Visual Studio 安装程序启动。 选择。**NET 桌面开发**(或。**.NET Core 跨平台开发**) 工作负荷中，然后选择**修改**。

1. 打开 Visual Studio 中，并选择**文件** > **新建** > **项目**。

1. 选择用于你的应用程序代码的模板。

    用于.NET Framework 中**新的项目**对话框框中，选择**Visual C#**， **Windows 桌面**从已安装的模板部分中，然后在中间窗格中选择**控制台应用 (.NET Framework)**。

    有关.NET Core 中**新项目**对话框框中，选择**Visual C#**， **.NET Core**从已安装的模板部分中，然后在中间窗格中选择**控制台应用程序 （.NET Core）**。

    如果看不到这些模板，则必须安装相应的工作负荷 （请参阅前面的步骤）。

1. 在中**名称**字段中，键入**ConsoleApp FirstApp**然后单击**确定**。

    Visual Studio 创建控制台项目，在右窗格中将显示在解决方案资源管理器中。

1. 在中*Program.cs*，所有的默认代码替换为以下代码：

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

    我们为此代码的意图是所有在列表中显示 galaxy 名称，与 galaxy 和 galaxy 类型之间的距离。 若要调试，务必了解代码的目的。 下面是我们想要在输出中显示的列表的一个行的格式：

    *galaxy 名称*，*距离*， *galaxy 类型*。

### <a name="run-the-app"></a>运行应用

1. 按**F5**或**开始调试**按钮![启动调试](../debugger/media/dbg-tour-start-debugging.png "开始调试")在调试工具栏中，位于代码编辑器上方。

    该应用启动时和有向我们显示由调试器没有例外情况。 但是，在控制台窗口中看到的输出是未达预期。 下面是预期的输出：

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    但是，我们看到的这只是：

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType 
    Pinwheel  25,  ConsoleApp_FirstApp.GType 
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    查找在输出和我们的代码，我们知道`GType`存储 galaxy 类型的类的名称。 我们尝试显示实际 galaxy 类型 （如"循环"），不是类名称 ！

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
