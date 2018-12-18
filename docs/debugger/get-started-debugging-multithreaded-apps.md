---
title: 了解如何调试多线程应用程序
description: 使用 Visual Studio 中的并行堆栈和并行监视窗口进行调试
ms.custom: H1HackMay2017
ms.date: "11/16/2018"
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66239362e454d5ab333214c444aeee3fa54b1b8a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936846"
---
# <a name="get-started-debugging-multithreaded-applications"></a>调试多线程应用程序入门
Visual Studio 提供多种工具和用户界面元素，以帮助您调试多线程应用程序。 本教程演示如何使用线程标记、**并行堆栈**窗口、**并行监视**窗口、条件断点、筛选器断点。 本教程中，只需要几分钟，但完成它将使您熟悉用于调试多线程应用程序的功能。

| | |
|---------|---------|
| ![视频的摄像机图标](../install/media/video-icon.png "观看视频") | [观看视频](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171)上显示了类似的步骤的多线程调试。 |

另外两个主题提供有关使用其他多线程调试工具的额外信息：

- 有关演示如何使用**调试位置**工具栏和**线程**窗口，请参阅[演练： 调试多线程应用程序](../debugger/how-to-use-the-threads-window.md)。

- 使用<xref:System.Threading.Tasks.Task>（托管代码）和并发运行时 （C++）示例，请参阅[演练： 调试并行应用程序](../debugger/walkthrough-debugging-a-parallel-application.md)。 有关对于大多数多线程应用程序类型的常规调试技巧，请阅读本主题和链接的主题。
  
你首先需要一个多线程应用程序项目。 如下的示例。  
  
#### <a name="create-a-multithreaded-app-project"></a>创建一个多线程应用项目  
  
1.  打开**文件**菜单，选择**新建** > **项目**。  
  
     此时将出现 **新建项目** 对话框。  
  
2.  选择右侧某个语言： **Visual C#**， **Visual c + +**，或**Visual Basic**。  
  
3.  **Windows 桌面** 中，选择**控制台应用**。  
  
4.  在 **名称** 栏中，键入名称 MyThreadWalkthroughApp。  
  
5.  单击 **“确定”**。  
  
     新的控制台项目随即显示。 创建该项目后，将显示源文件。 根据您选择的语言，源文件名称可能是 Program.cs、 MyThreadWalkthroughApp.cpp 或 Module1.vb 。  
  
6.  删除出现在源代码文件中的代码，并替换为此处显示的示例代码。

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // 此方法将在线程启动时被调用。
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // 暂停片刻，提供一个延迟
            // 使线程更明显。
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended.");
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // 启动线程。
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    #include "stdafx.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    using namespace;

    int count = 0;

    void doSomeWork() {

        cout << "The doSomeWork function is running on another thread." << endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        this_thread::sleep_for(chrono::seconds(3));
        cout << "The function called by the worker thread has ended." << endl;
    }

    int main() {
        vector<thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(thread(doSomeWork));
            cout << "The Main() thread calls this after starting the new thread" << endl;
        }

        for (auto& thread : threads) {
            thread.join();
        }

        return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' 此方法将在线程启动时被调用。
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' 暂停片刻，提供一个延迟
            ' 使线程更明显。
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended.")
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' 创建线程对象, 使用 ThreadStart delegate
            ' 传递 serverObject.InstanceMethod 方法。
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' 启动线程。
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```
  
7.  在 **文件** 菜单上，单击 **全部保存** 。  
  
#### <a name="begin-the-multithreaded-app"></a>调试多线程应用
  
-   在源代码编辑器中，查找以下代码： 
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3));
    cout << "The function called by the worker thread has ended." << endl; 
    ```  

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```
  
1. 在左侧滚动条槽中左键单击`Thread.Sleep`或`this_thread::sleep_for`语句插入新断点。  
  
    在源代码编辑器左侧的滚动条槽，将显示一个红色圆圈。 这表示在该位置已设置一个断点。 
  
2. 在**调试**菜单上，单击**开始调试**(**F5**)。  
  
    Visual Studio 将生成该解决方案，应用程序在被调试器附加的情况下开始运行，然后应用程序在断点处停止。  
  
   > [!NOTE]
   > 如果焦点切换到控制台窗口中，单击在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]窗口，以使焦点返回到[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
3. 在源代码编辑器中，找到该断点所在的行。  
  
#### <a name="ShowThreadsInSource"></a>发现线程标记  

1.  在调试工具栏中，单击**在源中显示线程**按钮![在源中显示线程](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")。

2. 按一下 **F11** 使调试器前进一个代码行。
  
3.  查看窗口左侧的滚动条槽。 在此行中，你会看到*线程标记* 图标![线程标记](../debugger/media/dbg-thread-marker.png "ThreadMarker") ，类似于两根细线。 线程标记指示线程在此位置停止。

    线程标记可以被断点部分隐藏。 
  
4.  将指针悬停在线程标记上。 将出现一个数据提示。 该数据提示将告诉您每个已停止线程的名称和线程 ID 号。 在这种情况下，名称可能是`<noname>`。 
  
5.  选择线程标记，以查看快捷菜单上可用的选项。
    
## <a name="ParallelStacks"></a>查看线程的位置

在 **并行堆栈** 窗口中，您可以切换线程视图和 （适用于基于任务的编程） 任务视图，您可以查看每个线程的调用堆栈信息。 在此应用中，我们可以使用线程视图。

1. 通过选择**调试 > 窗口 > 并行堆栈**，打开**并行堆栈**窗口。 您应看到类似于以下内容。确切信息将根据当前每个线程的位置、您的硬件、以及您的编程语言而异。

    ![并行堆栈窗口](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    在此示例中，从左到右将看到托管代码的此信息：
    
    - 主线程 （左侧） 上已停止`Thread.Start`，由线程标记图标指示停止点![线程标记](../debugger/media/dbg-thread-marker.png "ThreadMarker")。
    - 两个线程已进入`ServerClass.InstanceMethod`，其中之一是当前线程 （黄色箭头），而另一个线程已停止在`Thread.Sleep`。
    - 新线程 （右侧）也已启动，但是停止在`ThreadHelper.ThreadStart`。

2.  在**并行堆栈**窗口中右键单击，查看快捷菜单上有哪些可用选项。

    您可以从这些右键单击菜单中执行各种操作，但对于本教程中我们将在**并行监视**窗口中展示更多这些细节 （下一节）。

    > [!NOTE]
    > 要查看包含每个线程信息的列表视图，请使用**线程**窗口。 请参阅[演练： 调试多线程应用程序](../debugger/how-to-use-the-threads-window.md)。

## <a name="set-a-watch-on-a-variable"></a>对变量设置监视

1. 通过选择窗口**调试** > **窗口** > **并行监视** > **并行监视 1**打开**并行监视**。

2. 单击你看到`<Add Watch>`文本的单元格 （或第 4 列中的空标头单元格），输入`data`。

    在窗口中显示每个线程的数据变量的值。

3. 单击你看到`<Add Watch>`文本的单元格 （或第五个列中的空标头单元格），输入`count`。

    在窗口中显示为每个线程计数变量的值。 （如果看不到这么多的信息，请尝试按 **F11** 几次以继续在调试器中的线程执行。）

    ![并行监视窗口](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. 右键单击某个窗口以查看可用选项中的行。

## <a name="flagging-and-unflagging-threads"></a>标记线程和取消标记线程  
可以标记线程来追踪重要的线程，并忽略其它线程。  
  
1. 在**并行监视**窗口中，按住 **Shift** 键并选择多个行。

2. 右键单击并选择**标志**。

    现在，将标记所有所选的线程。 现在，您可以筛选仅显示已标记线程。
  
3.  在**并行监视**窗口中，选择**仅显示标记的线程**按钮![显示已标记线程](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker")。  
  
    现在只有标记的线程显示在该列表中。

    > [!TIP]
    > 在你已标记一些线程后，可以右键单击代码编辑器中的代码行，然后选择**将标记的线程运行到光标处**。请确保选择所有已标记的线程将达到的代码。Visual Studio 将在选择的代码行处暂停线程，这将中止线程，通过[冻结和解冻线程](#bkmk_freeze)更容易控制执行序列。

5.  单击**仅显示标记的线程**按钮可以切换回**显示所有线程**模式。
    
#### <a name="to-unflag-threads"></a>取消标记线程

若要取消标记线程，可在**并行监视**窗口右键单击一个或多个已标记线程，然后选择**取消标记**。

## <a name="bkmk_freeze"></a> 冻结和解冻线程执行 

> [!TIP]
> 您可以冻结和解冻 （暂停和恢复） 线程，来控制线程执行工作的顺序。 这可以帮助你解决并发问题，例如死锁和争用条件。
  
1.  在**并行监视**窗口中，选中所用行，右键单击并选择**冻结**。

    在第二个列中，每个行出现一个暂停图标。 暂停图标指示该线程已冻结。

2.  仅通过选择一行，取消选中其他行。

3.  右键单击某一行，然后选择**解冻**。

    暂停图标在此行上消失，表明线程已不再被冻结。

4.  切换到代码编辑器中，单击**F11**。 仅运行未冻结的线程。

    应用还实例化某些新线程。 任何未标记的新线程，不会被冻结。

## <a name="bkmk_follow_a_thread"></a> 通过使用条件断点执行单线程

在调试器中对单线程逐步跟踪，可能很有帮助。一种方法是冻结你不感兴趣的线程。在某些情况下，你可能需要在不冻结其它线程的情况下，跟踪单个线程，例如重现特定bug。 若要不冻结其他线程的情况下，跟踪某个线程，必须避免在你感不兴趣的线程上中断。 您可以通过设置[条件断点](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)执行此操作。

你可以设置不同的条件断点，例如，线程名称或线程 ID 。如果你知道数据对于每个线程都是唯一的，那么在数据上设置条件断点可能会有所帮助。 这是常见的调试方案，您对某些特定的数据值，比对任何特定的线程更感兴趣。

1. 右键单击以前创建的断点，然后选择**条件**。

2. 在**断点设置**窗口中，键入`data == 5`作为条件表达式。

    ![条件断点](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > 如果对某些特定线程更感兴趣，可以使用线程名称或线程 ID 做为条件。 若要在**断点设置**窗口中执行此操作，选择**筛选器**而不是**条件表达式**，并按照筛选器提示操作。 您可能需要在应用程序代码中使用线程名称，因为线程 Id 在重启调试器时会发生变化。

3. 关闭**断点设置**窗口。

4. 单击重启![重新启动应用程序](../debugger/media/dbg-tour-restart.png "RestartApp")按钮以重启调试会话。

    将分解为其数据变量为 5 的线程上的代码。 黄色箭头 （当前调试器上下文） 中查找**并行监视**窗口，验证是否。

5. 现在，可以单步执行代码 (F10) 和单步执行代码 (F11) 并遵循单一线程的执行。

    只要断点条件是唯一的线程，并且调试器不会命中 （可能需要禁用它们） 的其他线程上的任何其他断点，可以单步执行代码并单步执行代码而无需切换到其他线程。

    > [!NOTE]
    > 当您推进调试器进度时，将运行所有线程。 但是，调试器不会中断到其他线程上的代码中，除非其中一个其他线程遇到断点。 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>有关多线程调试窗口的详细信息 

#### <a name="to-switch-to-another-thread"></a>若要切换到另一个线程 

- 若要切换到另一个线程，请参阅[如何： 切换到另一个线程时调试](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>若要了解有关并行堆栈和并行监视窗口的详细信息  
  
- 请参阅[如何： 使用并行堆栈窗口](../debugger/using-the-parallel-stacks-window.md) 

- 请参阅[如何： 使用并行监视窗口](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>请参阅  
 [调试多线程应用程序](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [如何：在调试时切换到另一个线程](../debugger/how-to-switch-to-another-thread-while-debugging.md)
