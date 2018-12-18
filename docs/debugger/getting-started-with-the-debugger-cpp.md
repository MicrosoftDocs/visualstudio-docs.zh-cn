---
title: "学习使用 Visual Studio 调试器调试 C++"
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: debug-experiment
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- C++
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56ef97401a87f39e9c3bfd3138ee3a26646064c6
ms.sourcegitcommit: d7f232a7596420e40ff8051d42cdf90203af4a74
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2018
ms.locfileid: "52825874"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>教程：学习使用 Visual Studio 调试 C++ 代码

本文通过分步演练介绍了 Visual Studio 调试器的功能。 如果需要更加深入地了解调试器功能，请参阅[调试器功能之旅](../debugger/debugger-feature-tour.md)。 当你 *调试应用* 时，通常意味着调试器已附加到运行中的应用程序。 当执行此操作时，调试器在运行中提供许多方法让你查看代码正在做什么。 你可以单步跟踪代码、查看变量中存储的值、设置对变量的监视以查看值何时改变、检查代码的执行路径、查看代码分支是否正在运行等等。 如果这是你第一次尝试调试代码，可能需要在浏览本文之前阅读[零基础调试](../debugger/debugging-absolute-beginners.md)。

| | |
|---------|---------|
| ![视频的摄像机图标](../install/media/video-icon.png "观看视频") | [观看视频](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171)，其中展示了类似的步骤。 |

在本教程中，你将：

> [!div class="checklist"]
> * 启动调试器并命中断点。
> * 了解在调试器中单步跟踪代码的命令
> * 检查数据提示和调试器窗口中的变量
> * 检查调用堆栈

## <a name="prerequisites"></a>系统必备

* 必须已安装 Visual Studio 2017 和 **C++ 桌面开发** 工作负载。

    如果尚未安装 Visual Studio，请转到  [Visual Studio 下载](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 页免费安装。

    如果需要安装工作负载，但已安装 Visual Studio，单击 **新建项目** 对话框左窗格中的 **打开 Visual Studio 安装程序** 链接（选择 **文件** > **新建** > **项目**）。 将启动 Visual Studio 安装程序。 选择 **使用 C++ 的桌面开发** 工作负载，然后选择 **修改** 。

## <a name="create-a-project"></a>创建一个项目

1. 在 Visual Studio 中，依次选择 **文件 > 新建项目** 。

2. 在 **Visual C++** 下，选择 **Windows 桌面** ，然后在中间窗格中选择**Windows 控制台应用程序**。

    如果没有看到 **Windows 控制台应用程序** 项目模板，请单击 **新建项目** 对话框左侧窗格中的 **打开 Visual Studio 安装程序** 链接。 将启动 Visual Studio 安装程序。 选择 **使用 C++ 的桌面开发** 工作负载，然后选择 **修改** 按钮。

3. 键入名称（如 **get-started-debugging**），然后单击 **确定**。

    Visual Studio 随即创建项目。

4. 在 *get-started-debugging.cpp* 中，按如下替换代码：

    ```c++
    int main()
    {
        return 0;
    }
    ```

    替换为此代码：

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

1. 按 **F5**（**调试 > 开始调试**）或调试工具栏中的 **开始调试** 按钮（![开始调试](../debugger/media/dbg-tour-start-debugging.png "Start Debugging")）。

     按 **F5** 启动应用后，调试器会附加到应用进程，但现在我们还未执行任何特殊操作来检查代码。 因此应用只是刚开始加载，你会看到控制台如下输出。

    ```
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     在本教程中，我们将使用调试器仔细查看此应用，并查看调试器功能。

2. 按红色的停止（![停止调试](../debugger/media/dbg-tour-stop-debugging.png "Stop Debugging")）按钮来停止调试器。

## <a name="set-a-breakpoint-and-start-the-debugger"></a>设置断点并启动调试器

1. 在 `main` 函数的 `for` 循环中，通过单击以下代码行的左侧空白处来设置断点：

    `shape->Draw()`

    设置断点的位置会出现一个红色圆圈。

    断点是可信赖调试的最基本和最重要的功能。 断点指示 Visual Studio 应在哪个位置挂起你的运行代码，以使你可以查看变量的值、或内存的行为、或确定代码的分支是否运行。 

2. 按 **F5** 或 **启动调试** 按钮 ![Start Debugging](../debugger/media/dbg-tour-start-debugging.png "Start Debugging")，应用随即启动，并且调试器将运行到你设置断点的代码行。

    ![设置并命中断点](../debugger/media/get-started-set-breakpoint-cpp.gif)

    黄色箭头表示调试器暂停在哪条语句，它还在同一位置暂停应用执行（此语句尚未执行）。

     如果应用尚未运行，按 **F5** 启动调试器并在第一个断点处停止。 否则，按 F5 将继续运行应用至下一个断点。

    当你知道要详细检查的代码行或代码段时，断点功能非常有用。

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>使用单步执行命令在调试器中浏览代码

绝大多数情况下，我们使用键盘快捷键，因为这是在调试器中快速执行应用的好方法（括号中显示了等效的命令，如菜单命令）。

1. 当暂停在 `main` 函数中的 `shape->Draw` 方法时，按 **F11**（或选择 **调试 > 逐语句**）前进执行代码到 `Rectangle` 类。

     ![使用 F11 逐语句跟踪代码](../debugger/media/get-started-f11-cpp.png "F11 逐语句")

     F11 是 **逐语句** 命令，每单击一次，应用就执行一条语句。 F11 是一种以最详细地检查执行流的好方法。 （为了更快地浏览代码，我们还向你展示一些其他选项。）默认情况下，调试器会跳过非用户代码（如果需要更多详细信息，请参阅[仅我的代码](../debugger/just-my-code.md)）。

2. 按几次 **F10**（或选择 **调试 > 逐过程**），直到调试器停止在调用 `Shape::Draw` 方法处，然后再按一次 **F10** 。

     ![使用 F10 逐过程跟踪代码](../debugger/media/get-started-step-over-cpp.png "F10 逐过程")

     请注意，这次调试器不会逐过程跟踪基类 (`Shape`) 的 `Draw` 方法。 按 F10 将使调试器前进，但不会步入应用程序代码中的函数或方法（代码仍将执行）。 通过在调用 `Shape::Draw` 方法的这行代码上按 F10（而不是 **F11**），我们跳过了基类中 `Draw` 方法的实现代码（我们现在可能对此已不感兴趣）。

## <a name="navigate-code-using-run-to-click"></a>使用“运行以单击”浏览代码

1. 在代码编辑器中，向下滚动并将鼠标悬停在 `Triangle` 类中的 `std::cout` 上，直到左侧出现绿色的“运行以单击”按钮（![运行以单击](../debugger/media/dbg-tour-run-to-click.png "RunToClick")。

     ![使用“运行以单击”功能](../debugger/media/get-started-run-to-click-cpp.png "运行以单击")

   > [!NOTE]
   > **运行以单击** 是 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] 中的新增按钮。 如果未看到绿色箭头按钮，请在此示例中改为使用 **F11** 以使调试器前进到正确的位置。

2. 单击 **运行以单击** 按钮（![运行以单击](../debugger/media/dbg-tour-run-to-click.png "RunToClick")）。

    使用此按钮类似于设置临时断点。 **运行以单击** 可非常方便的快速到达应用代码的可见区域（你可在任何打开的文件中单击）。

    调试器前进到 `Triangle` 类的 `std::cout` 方法实现。

    暂停时，你注意到有拼写错误！ 提示 **rawing a trangle** 拼写错误。 我们可以在调试器中运行应用时，直接在此处修复它。

## <a name="edit-code-and-continue-debugging"></a>编辑代码并继续调试

1. 单击“Drawing a trangle”内并键入校正，将“trangle”更改为“triangle”。

1. 按一下 **F11** ，你会看到提示代码正在重新编译的消息，然后调试器将再次前进。

    > [!NOTE]
    > 根据你在调试器中编辑的代码类型，可能会看到一条警告消息。 在某些情况下，代码需要重新编译才能继续执行。

## <a name="step-out"></a>单步跳出

假设你已完成了对 `Triangle` 类中 `Draw` 方法的检查，并且希望在退出函数后，但留在调试器中。 可使用 **跳出** 命令执行此操作。

1. 按 **Shift** + **F11**（或 **调试 > 跳出**）。

     此命令将恢复应用执行（并使调试器前进），直到当前函数返回。

     你应会回到 `main` 方法的 `for` 循环中。

## <a name="restart-your-app-quickly"></a>快速重启应用

单击调试工具栏中的 **重启**（![重启应用](../debugger/media/dbg-tour-restart.png "RestartApp")）按钮（Ctrl + Shift + F5）。

当你按下 **重启** 时，与停止应用并重启调试器相比，它节省了时间。 调试器在执行代码命中的第一个断点处暂停。

调试器再次在你在 `shape->Draw()` 方法上设置的断点处停止。

## <a name="inspect-variables-with-data-tips"></a>使用数据提示检查变量

允许你检查变量是调试器最有用的功能之一，并且有不同的方法来执行此操作。 通常，当尝试通过调试解决问题时，你试图找出变量，是否在特定时间具有了你期望的值。

1. 在 `shape->Draw()` 方法上暂停时，将鼠标悬停在 `shapes` 容器（矢量对象）上，你会看到其默认属性值 `size` 属性，显示为 `size=3`。

1. 展开 `shapes` 对象以查看其所有属性，例如具有内存地址的数组 `[0]` 的第一个索引。

    可以进一步展开对象以查看其属性。

1. 展开第一个索引 `[0]` 以查看矩形的 `privateHeight` 属性。

     ![查看数据提示](../debugger/media/get-started-data-tip-cpp.png "查看数据提示")

     通常，在调试时，你需要快速检查对象的属性值，数据提示是一种实现此目的的好方法。

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>使用“自动”和“局部变量”窗口检查变量

1. 查看代码编辑器底部的 **自动** 窗口。

     ![在“自动”窗口中检查变量](../debugger/media/get-started-autos-window-cpp.png "自动窗口")

    在 **自动** 窗口中，可看到变量及其当前值。 对于 C++，**自动** 窗口显示前三行代码中的变量。

2. 接下来，我们来看看 **自动** 窗口旁边的选项卡中的 **局部变量** 窗口。

    **局部变量** 窗口显示当前[作用域](https://www.wikipedia.org/wiki/Scope_(computer_science))中的变量，即当前代码执行上下文。

## <a name="set-a-watch"></a>设置监视

1. 在主代码编辑器窗口中，右键单击 `shapes` 对象，然后选择 **添加监视** 。

    **监视** 窗口将在代码编辑器的底部打开。 可使用 **监视** 窗口指定要关注的变量（或表达式）。

    现在，你在 `shapes` 对象上设置好了监视，当你在调试器中浏览时，可看到其值发生变化。 与其他变量窗口不同，**监视** 窗口始终显示你正在监视的变量（当超出作用域时，它们会变灰）。

## <a name="examine-the-call-stack"></a>检查调用堆栈

1. 在 `for` 循环中暂停时，单击 **调用堆栈** 窗口，默认情况下，该窗口在右下方窗格中打开。

2. 按几下 **F11** ，直到看到调试器在代码编辑器中 `Rectangle` 类的 `Shape::Draw` 方法中暂停。 查看 **调用堆栈** 窗口。

    ![检查调用堆栈](../debugger/media/get-started-call-stack-cpp.png "ExamineCallStack")

    **调用堆栈** 窗口显示方法和函数被调用的顺序。 最上面一行显示当前函数（此示例中的 `Rectangle::Draw` 方法）。 第二行显示从 `main` 函数调用的 `Rectangle::Draw` ，依此类推。

   > [!NOTE]
   > **调用堆栈** 窗口类似于某些 IDE（如 Eclipse）中的调试透视图。

    调用堆栈是检查和理解应用执行流的好方法。

    可双击代码行来查看该源代码，这也会更改调试器正在检查的当前作用域。 此操作不会使调试器前进。

    还可使用 **调用堆栈** 窗口中的右键菜单执行其他操作。 例如，你可将断点插入到指定的函数中，使用 **运行到光标处** 推进调试器，然后检查源代码。 有关详细信息，请参阅[如何：检查调用堆栈](../debugger/how-to-use-the-call-stack-window.md)。

## <a name="change-the-execution-flow"></a>更改执行流

1. 在调试器暂停在 `Shape::Draw` 方法调用后，使用鼠标抓住左侧的黄色箭头（执行指针），将黄色箭头向上移动一行到 `std::cout` 方法调用上。

1. 按 **F11**。

    调试器将重新运行 `std::cout` 方法（你会在控制台窗口输出中看到）。

    通过更改执行流，你可以进行测试不同代码执行路径或重新运行代码等操作，而无需重启调试器。

    > [!WARNING]
    > 通常你需要小心使用此功能，工具提示中会出现警告。 你也可能会看到其他警告。 移动指针无法将应用程序还原到更早的应用状态。

1. 按 **F5** 继续运行应用。

    恭喜你完成本教程！

## <a name="next-steps"></a>后续步骤

在本教程中，你已了解了如何启动调试器、单步跟踪代码以及检查变量。 你可能会希望更深入地了解调试器功能，以及查看指向更多信息的链接。

> [!div class="nextstepaction"]
> [初探调试器](../debugger/debugger-feature-tour.md)
