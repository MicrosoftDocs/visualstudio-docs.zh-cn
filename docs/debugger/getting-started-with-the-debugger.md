---
title: "学习调试"
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: debug-experiment
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d832753b798cc9e476b675f8791c1ab245b3adee
ms.sourcegitcommit: a34b7d4fdb3872865fcf98ba24a0fced58532adc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2018
ms.locfileid: "51561668"
---
# <a name="tutorial-learn-to-debug-using-visual-studio"></a>教程：学习使用 Visual Studio 调试C#代码

本文通过分步演练介绍了 Visual Studio 调试器的功能。当你在 *调试你的应用* 时，通常意味着调试器已附加在运行中的应用。当你这样做的时候，调试器提供很多种方法，在此时查看代码在做什么。你可以单步跟踪代码查看变量中存储的值，可以给变量设置监视，以查看变量何时发生改变，可以检查代码的执行路径，查看代码的分支是否在运行等等。如果这是你第一次尝试调试代码，在继续阅读本文前，你可能需要阅读 [Debugging for absolute beginners](../debugger/debugging-absolute-beginners.md) 和 [Fix bugs by writing better C# code](../debugger/write-better-code-with-visual-studio.md)。

| | |
|---------|---------|
| ![视频的摄像机图标](../install/media/video-icon.png "观看视频") | [观看有关调试的视频](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171)，其中展示了类似的步骤。 |

尽管演示应用为 C# 和 C++，但这些功能也适用于 Visual Basic、JavaScript 和 Visual Studio 支持的其他语言（除非另有说明）。 屏幕截图为 C#。

在本教程中，你将：

> [!div class="checklist"]
> * 启动调试器并命中断点。
> * 了解在调试器中逐步执行代码的命令
> * 检查数据提示和调试器窗口中的变量
> * 检查调用堆栈

## <a name="prerequisites"></a>系统必备

* 必须安装有 Visual Studio 2017 并具有“.NET 桌面开发”或“使用 C++ 的桌面开发”工作负载。

    如果尚未安装 Visual Studio，请转到  [Visual Studio 下载](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 页免费安装。

    如果需要安装工作负载，但已有 Visual Studio，则单击“新建项目”对话框左窗格中的“打开 Visual Studio 安装程序”链接（选择“文件” > “新建” > “项目”）。 Visual Studio 安装程序启动。 选择“.NET 桌面开发”或“使用 C++ 的桌面开发”工作负载，然后选择“修改”。

## <a name="create-a-project"></a>创建项目

1. 在 Visual Studio 中，依次选择“文件”>“新建项目”。

2. 在“Visual C#”或“Visual C++”下，选择“Windows 桌面”，然后在中间窗格中选择“控制台应用”（C++ 中的“Windows 控制台应用程序”）。

    如果没有看到“控制台应用程序”项目模板，请单击“新建项目”对话框左侧窗格中的“打开 Visual Studio 安装程序”链接。 Visual Studio 安装程序启动。 选择“.NET 桌面开发”或“使用 C++ 的桌面开发”工作负载，然后选择“修改”。

3. 键入名称（如“get-started-debugging”），然后单击“确定”。

    Visual Studio 随即创建项目。

    > [!NOTE]
    > 若要在本文中在 C# 和 C++ 示例代码间切换，请使用本页右上角的语言筛选器。

4. 在“Program.cs”(C#) 或“get-started-debugging.cpp”(C++) 中，将以下代码

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;

    namespace get_started_debugging
    {
        class Program
        {
            static void Main(string[] args)
            {
            }
        }
    }
    ```

    ```c++
    int main()
    {
        return 0;
    }
    ```

    替换为此代码：

    ```csharp
    using System;
    using System.Collections.Generic;

    public class Shape
    {
        // A few example members
        public int X { get; private set; }
        public int Y { get; private set; }
        public int Height { get; set; }
        public int Width { get; set; }
   
        // Virtual method
        public virtual void Draw()
        {
            Console.WriteLine("Performing base class drawing tasks");
        }
    }

    class Circle : Shape
    {
        public override void Draw()
        {
            // Code to draw a circle...
            Console.WriteLine("Drawing a circle");
            base.Draw();
        }
    }

    class Rectangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a rectangle...
            Console.WriteLine("Drawing a rectangle");
            base.Draw();
        }
    }

    class Triangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a triangle...
            Console.WriteLine("Drawing a trangle");
            base.Draw();
        }
    }

    class Program
    {
        static void Main(string[] args)
        {

            var shapes = new List<Shape>
            {
                new Rectangle(),
                new Triangle(),
                new Circle()
            };

            foreach (var shape in shapes)
            {
                shape.Draw();
            }

            // Keep the console open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }

    }

    /* Output:
        Drawing a rectangle
        Performing base class drawing tasks
        Drawing a triangle
        Performing base class drawing tasks
        Drawing a circle
        Performing base class drawing tasks
    */
    ```

    ```c++
    #include "pch.h"

    #include <string>
    #include <vector>
    #include <iostream>

    class Shape
    {
        int privateX = 0;
        int privateY = 0;
        int privateHeight = 0;
        int privateWidth = 0;

        int getX() const { return privateX; }
        void setX(int value) { privateX = value; }

        int getY() const { return privateY; }
        void setY(int value) { privateY = value; }

        int getHeight() const { return privateHeight; }
        void setHeight(int value) { privateHeight = value; }

        int getWidth() const { return privateWidth; }
        void setWidth(int value) { privateWidth = value; }

        public:
        // Virtual method
        virtual void Draw()
        {
            std::wcout << L"Performing base class drawing tasks" << std::endl;
        }
    };

    class Circle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a circle...
        std::wcout << L"Drawing a circle" << std::endl;
        Shape::Draw();
        }
    };

    class Rectangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a rectangle...
        std::wcout << L"Drawing a rectangle" << std::endl;
        Shape::Draw();
        }
    };

    class Triangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a triangle...
        std::wcout << L"Drawing a trangle" << std::endl;
        Shape::Draw();
        }
    };

    int main(std::vector<std::wstring> &args)
    {
        auto shapes = std::vector<Shape*>
        {
            new Rectangle(),
            new Triangle(),
            new Circle()
        };

        for (auto shape : shapes)
        {
            shape->Draw();
        }
    }

    /* Output:
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    */
    ```

## <a name="start-the-debugger"></a>启动调试器！

1. 在调试器工具条中按 **F5** (**调试 > 开始调试**) 或者 **开始调试** 按键 ![开始调试](../debugger/media/dbg-tour-start-debugging.png "开始调试")。

     按**F5**启动应用时，调试器会附加到应用进程, 但现在我们还未执行任何特殊操作来检查代码。所以应用只会加载，你可以看到控制台输出。

    ```
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     在本教程，我们将使用调试器仔细查看此应用，并了解调试器功能。

2. 按红色的停止（![停止调试](../debugger/media/dbg-tour-stop-debugging.png "Stop Debugging")）按钮来停止调试器。

## <a name="set-a-breakpoi## 设置断点并启动调试器

1. 在 `Main` 函数的 `foreach` 循环（C++ `main` 函数中的 `for` 循环）中，通过单击以下代码行的左端来设置断点：

    `shape.Draw()`（或者，C++ 中的 `shape->Draw()`）

    设置断点的位置会出现一个红色圆圈。

    断点是可靠调试最基本和最重要的功能。 断点指示 Visual Studio 应在哪个位置挂起你的运行代码，以使你可以查看变量的值或内存的行为，或确定代码的分支是否运行。 

2. 按 **F5** 或**开始调试**按钮，应用随即启动，调试器将运行到你设置断点的代码行。

    ![设置并命中断点](../debugger/media/get-started-set-breakpoint.gif)

    黄色箭头表示调试器暂停处的语句，它还在同一点上挂起正在运行的应用（此语句尚未执行）。

     如果应用尚未运行，则按 **F5** 会启动调试器并在第一个断点处停止。 另外，按 **F5** 将继续运行应用至下一个断点。

    当你想要详细检查代码行或代码段时，断点功能非常有用。

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>在调试器中使用单步执行命令定位代码

大多数情况下，我们使用键盘快捷方式，因为这是在调试器中快速执行应用的好方法（括号中显示了等效的命令，如菜单命令）。

1. 在 `Main` 方法（C++ 中的 `shape->Draw`）的 `shape.Draw` 方法调用中暂停时，按 **F11**（或选择**调试 > 单步执行**）前进到 `Rectangle` 类的代码。

     ![使用 F11 单步执行代码](../debugger/media/get-started-f11.png "F11单步执行")

     F11 是**单步执行**命令，每单击一次，应用就执行一个语句。 F11 是一种以最详尽方式检查执行流的好方法。 （为了更快地浏览代码，我们还向你展示一些其他选项。）默认情况下，调试器会跳过非用户代码（如果需要更多详细信息，请参阅[仅我的代码](../debugger/just-my-code.md)）。

2. 按几次 **F10**（或选择**调试 > 逐过程**），直到调试器停止于 `base.Draw` 方法调用（C++ 中的 `Shape::Draw`），然后再按一次 **F10**。

     ![使用 F10 单步跳过代码](../debugger/media/get-started-step-over.png "F10 Step Over")

     请注意，这次调试器不会单步执行基类 (`Shape`) 的 `Draw` 方法。 按 F10 将使调试器前进，但不会逐语句执行应用程序代码中的函数或方法（代码仍将执行）。 通过在进行 `base.Draw`（或 `Shape::Draw`）方法调用时按 F10（而不是 F11），我们跳过了 `base.Draw` 的实现代码（或许我们现在对此已不感兴趣）。

## <a name="navigate-code-using-run-to-click"></a> 使用“点击运行”定位代码

1. 在代码编辑器中，向下滚动并将鼠标悬停在 `Triangle` 类中的 `Console.WriteLine` 方法（C++ 中的 `std::cout`）上，直到左侧出现绿色的**点击运行**按钮（![点击](../debugger/media/dbg-tour-run-to-click.png "RunToClick")）。

     ![使用“点击运行”功能](../debugger/media/get-started-run-to-click.png "点击运行")

   > [!NOTE]
   > “点击运行”是 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] 中的新增按钮。 如果未看到绿色箭头按钮，请在此示例中改为使用 **F11** 以使调试器前进到正确的位置。

2. 单击**点击运行**按钮（![点击运行](../debugger/media/dbg-tour-run-to-click.png "RunToClick")）。

    使用此按钮类似于设置临时断点。 **点击运行**对于快速到达应用代码的可见区域十分方便（你可在任何打开的文件中点击）。

    调试器前进到 `Triangle` 类的 `Console.WriteLine` 方法实现（C++ 中的 `std::cout`）。

    暂停时，你注意到有拼写错误！ “Drawing a trangle”输出拼写错误。 在调试器中运行应用时，我们可直接在此处修复它。

## <a name="edit-code-and-continue-debugging"></a>编辑代码并继续调试

1. 单击“Drawing a trangle”内并键入校正，将“trangle”更改为“triangle”。

1. 再按一次 **F11**，你会看到调试器再次前进。

    > [!NOTE]
    > 根据你在调试器中编辑的代码类型，可能会看到一条警告消息。 在某些情况下，代码需要重新编译才能继续。

## <a name="step-out"></a>跳出

假设你已完成了对 `Triangle` 类中 `Draw` 方法的检查，并且希望退出该函数但想继续留在调试器中。 可使用**跳出**命令执行此操作。

1. 按 **Shift** + **F11**（或**调试 > 跳出**）。

     此命令将恢复应用执行（并使调试器前进），直到当前函数返回。

     你应当会回到 `Main` 方法的 `foreach` 循环（C++ 中的 `for` 循环）中。

## <a name="restart-your-app-quickly"></a>快速重启应用

单击调试工具栏中的**重启**（![重启应用](../debugger/media/dbg-tour-restart.png "RestartApp")）按钮（**Ctrl** + **Shift** + **F5**）。

当你按下**重启**时，与停止应用并重启调试器相比，它节省了时间。 调试器在执行代码的第一个断点处暂停。

调试器再次在 `shape.Draw()` 方法（C++ 中的 `shape->Draw()`）上设置的断点处停止。

## <a name="inspect-variables-with-data-tips"></a>使用数据提示检查变量

允许你检查变量的功能是调试器最有用的功能之一，并且有不同的方法来执行此操作。 通常，当尝试使用调试解决问题时，你试图在特定情况下查明变量中保存的值是否与预期相符。

1. 在 `shape.Draw()` 方法（C++ 中的 `shape->Draw()`）上暂停时，将鼠标悬停在 `shapes` 对象上，你会看到其默认属性值 `Count` 属性。

1. 展开 `shapes` 对象以查看其所有属性，例如数组 `[0]` 的第一个索引，其值为 `Rectangle` (C#) 或内存地址 (C++)。

     ![查看数据提示](../debugger/media/get-started-data-tip.gif "查看数据提示")

    可进一步展开对象以查看其属性，例如矩形的 `Height` 属性。

    通常，在调试时，你需要快速检查对象的属性值，数据提示是一种实现此目的的好方法。

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>使用“自动”和“局部变量”窗口检查变量

1. 查看代码编辑器底部的“自动”窗口。

     ![在“自动”窗口中检查变量](../debugger/media/get-started-autos-window.png "自动窗口")

    在“自动”窗口中，可看到变量及其当前值。 **自动**窗口显示当前行或前一行使用的所有变量（在 C++ 中，该窗口显示前三个代码行中的变量。 查看文档以了解特定于语言的行为）。

    > [!NOTE]
    > 在 JavaScript 中，支持**局部变量**窗口，但不支持**自动**窗口。

2. 接下来，我们来看看**自动**窗口旁边的选项卡中的**局部变量**窗口。

    **局部变量**窗口显示当前[作用域](https://www.wikipedia.org/wiki/Scope_(computer_science))中的变量。

## <a name="set-a-watch"></a>设置监视

1. 在主代码编辑器窗口中，右键单击 `shapes` 对象，然后选择**添加监视**。

    **监视**窗口将在代码编辑器的底部打开。 可使用**监视**窗口指定要关注的变量（或表达式）。

    现在，你在 `shapes` 对象上设置好了监视，当你在调试器中移动时，可看到其值发生变化。 与其他变量窗口不同，**监视**窗口始终显示你正在监视的变量（当超出作用域时，它们会变灰）。

## <a name="examine-the-call-stack"></a>检查调用堆栈

1. 在 `foreach` 循环（C++ 中的 `for` 循环）中暂停时，单击**调用堆栈**窗口，默认情况下，该窗口在右下方窗格中打开。

2. 单击 **F11** 几次，直至看到调试器在代码编辑器中的 `Circle.Draw` 方法中暂停。 查看“调用堆栈”窗口。

    ![检查调用堆栈](../debugger/media/get-started-call-stack.png "ExamineCallStack")

    **调用堆栈**窗口显示方法和函数被调用的顺序。 最上面一行显示当前函数（此应用中的 `Circle.Draw` 或 `Circle::Draw` 方法）。 第二行显示 `Circle.Draw` 是从 `Main` 方法（C++ 中的 `main`）调用的，依此类推。

   > [!NOTE]
   > **调用堆栈**窗口类似于某些 IDE（如 Eclipse）中的调试透视图。

    使用调用堆栈来检查和理解应用执行流程是一种好办法。

    可双击代码行来查看该源代码，这也会更改调试器正在检查的当前作用域。 此操作不会使调试器前进。

    还可使用**调用堆栈**窗口中的右键单击菜单执行其他操作。 例如，你可将断点插入到指定的函数中，使用**运行到光标处**推进调试器，然后检查源代码。 有关详细信息，请参阅[如何：检查调用堆栈](../debugger/how-to-use-the-call-stack-window.md)。

## <a name="change-the-execution-flow"></a>更改执行流

1. 在 `Circle.Draw` 方法调用中暂停调试器后，按几次 **F11**，直到调试器暂停于 `base.Draw` 方法调用（C++ 中的 `Shape::Draw`）。

1. 使用鼠标抓住左侧的黄色箭头（执行指针），将黄色箭头向上移动一行到 `Console.WriteLine`（C++ 中的 `std::cout`）方法调用。

1. 再按一次 **F11**。

    调试器重新运行 `Console.WriteLine` 方法（C++ 中的 `std::cout`）。

    通过更改执行流，你可以进行测试不同代码执行路径或重新运行代码等操作，而无需重启调试器。

    > [!WARNING]
    > 通常你需要小心使用此功能，工具提示中会出现警告。 你也可能会看到其他警告。 移动指针无法将应用程序还原到更早的应用状态。

1. 按 **F5** 继续运行应用。

    恭喜你完成本教程！

## <a name="next-steps"></a>后续步骤

在本教程中，你已了解了如何启动调试器、逐步执行代码以及检查变量。 你可能会希望更深入地了解调试器功能以及查看指向更多信息的链接。

> [!div class="nextstepaction"]
> [首次了解调试器](../debugger/debugger-feature-tour.md)
