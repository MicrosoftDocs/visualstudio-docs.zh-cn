---
title: 检查自动和局部变量窗口中的变量 |Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 04/17/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 35fa37831ad79a55effe849f8605ae6b5d299d3a
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349645"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>检查自动和局部变量窗口中的变量

在调试时 **自动** 和 **局部变量** 窗口显示变量值。 在启调试会话时，这两个窗口才可用。 **自动** 窗口显示当前断点周围使用的变量。 **局部变量**窗口显示在当前代码作用域内定义的变量, 通常是当前函数或方法定义的变量。如果现在是你第一次尝试调试代码， 在开始之前，可能需要去阅读这些文章 [使用Visual Studio写最好的C#代码](../debugger/write-better-code-with-visual-studio.md) 和 [零基础调试代码](../debugger/debugging-absolute-beginners.md)。

若要打开**自动**窗口中的，调试时，选择**调试** > **窗口** > **自动**，或按**Ctrl**+**Alt**+**V** > **A**。

若要打开**局部变量**窗口中的，调试时，选择**调试** > **窗口** > **局部变量**，或按**Alt**+**4**。

如果您需要了解基本调试功能的更多信息，请参阅[开始使用调试器](../debugger/getting-started-with-the-debugger.md)。

> [!NOTE]
> 本主题适用于Visual Studio Windows版。 Visual Studio Mac 版 中，请参阅[在 Visual Studio for Mac 的数据可视化效果](/visualstudio/mac/data-visualizations)。

## <a name="use-the-autos-and-locals-windows"></a>使用自动和局部变量窗口

在**自动**和**局部变量**窗口中显示数组和对象树控件。选择变量名左侧的箭头以展开所属字段和属性。 下例<xref:System.IO.FileStream?displayProperty=fullName>对象中**局部变量**窗口：

![局部变量 FileStream](../debugger/media/locals-filestream.png "局部变量 FileStream")

中的红色值**局部变量**或**自动**窗口意味着在最后一次计算中已更改值。 此更改可能是来自上一个调试会话，或因为您更改在窗口中的值。

在调试器窗口中的默认数字格式为 decimal。 若要将其更改为十六进制，右键单击**局部变量**或**自动**窗口，然后选择**十六进制显示**。 此更改会影响所有调试器窗口。

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>编辑自动或局部变量窗口中的变量值

若要编辑的值中的大多数变量**自动**或**局部变量**windows 中，双击值并输入新值。

你可以输入表达式作为一个值，例如 `a + b`。 调试器接受大多数合法的语言表达式。

在本机 C++ 代码中，你可能需要限定变量名的上下文。 有关详细信息，请参阅[上下文运算符 （c + +）](../debugger/context-operator-cpp.md)。

>[!CAUTION]
>请确保你了解后果之前更改值和表达式。 可能存在的问题是：
>
>-   计算某些表达式可以更改变量的值，或会影响程序的状态。 例如，计算`var1 = ++var2`更改的值都`var1`和`var2`。 这些表达式被视为具有[副作用](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))。 如果您不了解这些副作用会导致意外的结果。
>
>-   编辑浮点值时，由于要将小数部分从十进制转换为二进制，因此所得的结果可能存在微小误差。 甚至看起来无关紧要的编辑都能引起浮点变量中的位的某些更改。

## <a name="change-the-context-for-the-autos-or-locals-window"></a>将自动或局部变量窗口的上下文

可以使用**调试位置**工具栏来选择所需的函数、 线程或进程，这会更改为上下文**自动**并**局部变量**windows。

若要启用**调试位置**工具栏上，单击工具栏区域和选择的空白部分**调试位置**从下拉列表中或选择**视图** >  **工具栏** > **调试位置**。

设置断点并开始调试。 当到达断点时，执行暂停，你可以查看中的位置**调试位置**工具栏。

![调试位置工具栏](../debugger/media/debuglocationtoolbar.png "调试位置工具栏")

## <a name="bkmk_whatvariables"></a> 自动窗口中的变量

 **自动**窗口是可用于C#，Visual Basic 和 c + + 代码，但不适用于 JavaScript 或F#。

 不同的代码语言显示在不同的变量**自动**窗口。

 - 在C#和 Visual Basic**自动**窗口显示当前或前一行中使用的任何变量。 例如，在C#或 Visual Basic 代码中，声明以下四个变量：

   ```csharp
       public static void Main()
       {
          int a, b, c, d;
          a = 1;
          b = 2;
          c = 3;
          d = 4;
       }
   ```

   在行上设置断点`c = 3;`，并启动调试器。 时暂停执行，**自动**窗口将显示：

   ![自动 CSharp](../debugger/media/autos-csharp.png "自动 CSharp")

   值`c`为 0，因为行`c = 3`尚未执行。

 - C + +**自动**窗口将显示执行会暂停当前行之前的至少三行中使用的变量。 例如，在 c + + 代码中，声明六个变量：

   ```C++
       void main() {
           int a, b, c, d, e, f;
           a = 1;
           b = 2;
           c = 3;
           d = 4;
           e = 5;
           f = 6;
       }
   ```

    在行上设置断点`e = 5;`并运行调试器。 当执行停止时，**自动**窗口将显示：

    ![自动 c + +](../debugger/media/autos-cplus.png "自动 c + +")

    在变量`e`是未初始化，因为行`e = 5`尚未执行。

##  <a name="bkmk_returnValue"></a> View return values of method calls
 在.NET 和 c + + 代码中，可以检查中的返回值**自动**窗口时单步或跳出方法调用。 查看方法调用返回时它们不会存储在本地变量的值会很有用。 可以使用一种方法，作为一个参数，或另一种方法的返回值。

 例如，以下C#代码将添加两个函数的返回值：

```csharp
static void Main(string[] args)
{
    int a, b, c, d;
    a = 1;
    b = 2;
    c = 3;
    d = 4;
    int x = sumVars(a, b) + subtractVars(c, d);
}

private static int sumVars(int i, int j)
{
    return i + j;
}

private static int subtractVars(int i, int j)
{
    return j - i;
}
```

若要查看的返回值`sumVars()`和`subtractVars()`方法调用自动窗口中：

1. 在 `int x = sumVars(a, b) + subtractVars(c, d);` 行上设置断点。

1. 开始调试，并在断点处暂停执行，选择**单步跳过**或按**F10**。 您应看到在以下的返回值**自动**窗口：

  ![自动返回值C# ](../debugger/media/autosreturnvaluecsharp2.png "自动返回值C#")

## 请参阅  
 [什么是调试?](../debugger/what-is-debugging.md)  
 [使用Visual Studio写最好的C#代码](../debugger/write-better-code-with-visual-studio.md)  
 [首次了解调试器](../debugger/debugger-feature-tour.md)
 [调试器窗口](../debugger/debugger-windows.md)
