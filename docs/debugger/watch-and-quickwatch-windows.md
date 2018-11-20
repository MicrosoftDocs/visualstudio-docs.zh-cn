---
title: 在 Visual Studio 中的变量上设置监视 |Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 10/11/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a4db887a3e27d995229da6d954c4b3f66173e9e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897350"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>监视使用监视窗口和快速监视的变量 

当你进行调试时，可以使用**Watch** windows 和**快速监视**监视变量和表达式。 在调试会话期间，windows 才可用。

**观看**windows 可以在调试时一次显示多个变量。 **快速监视**对话框一次仅显示单个变量，并可以继续调试之前，必须关闭。

## <a name="observe-variables-with-a-watch-window"></a>观察使用监视窗口变量

您可以打开多个**Watch**窗口中，并观察中的多个变量**监视**窗口。 

例如，若要设置的值的监视`a`， `b`，和`c`在下面的代码：

```C++
int main()
{
    int a, b, c;
    a = 1;
    b = 2;
    c = 0;

    for (int i = 0; i < 10; i++)
    {
        a++;
        b *= 2;
        c = a + b;
    }

    return 0;
}

```

1. 上设置断点`c = a + b;`通过单击左边距中的行选择**调试** > **切换断点**，或按**F9**。
   
1. 开始调试通过选择绿色**启动**箭头或**调试** > **开始调试**，或按**F5**。 在断点处暂停执行。
   
1. 打开**Watch**通过选择窗口**调试** > **Windows** > **监视** >  **观看 1**，或按**Ctrl**+**Alt**+**W** > **1**.
   
   可以打开其他**Watch**窗口中的，选择 windows **2**， **3**，或者**4**。
   
1. 在中**Watch**窗口中，选择空的行，并类型变量`a`。 执行相同操作`b`和`c`。
   
   ![监视变量](../debugger/media/watchvariables.png "WatchVariables")
   
1. 继续进行调试，通过选择**调试** > **单步执行**或按**F11**根据需要以继续。 在变量中的值**Watch**窗口中更改在循环`for`循环。
   
>[!NOTE]
>仅 c + + 
>- 您可能需要限定变量名或使用变量名称的表达式的上下文。 上下文是函数、 源文件，该文件或变量所处的模块。 如果需要限定上下文，使用[上下文运算符 （c + +）](../debugger/context-operator-cpp.md)中的语法**名称**中**观看**窗口。 
>  
>- 您可以添加寄存器名和使用的变量名 **$\<注册&nbsp;名称 >** 或 **@\<注册&nbsp;名称 >** 到**名称**中**监视**窗口。 有关详细信息，请参阅 [Pseudovariables](../debugger/pseudovariables.md)。

## <a name="use-expressions-in-a-watch-window"></a>在监视窗口中使用表达式

您可以观察到任何有效的表达式中的调试器识别**监视**窗口。

例如，对于前面部分中的代码，可以获取三个值的平均值通过输入`(a + b + c) / 3`中**观看**窗口：

![监视表达式](../debugger/media/watchexpression.png "监视表达式")

在中计算表达式的规则**监视**窗口通常是与中的代码语言表达式的计算规则相同。 如果表达式具有语法错误，出现相同的编译器错误，如代码编辑器中所示。 例如，在上述表达式中的有拼写错误生成中的出现此错误**监视**窗口：

![观看表达式错误](../debugger/media/watchexpressionerror.png "观看表达式错误")

中可能会显示一个带有两个波浪条纹图标圆圈**监视**窗口。 此图标表示调试器会计算该表达式，因为潜在的跨线程依赖关系。 计算代码需要暂时，运行您的应用程序中的其他线程，但由于在中断模式下，应用程序中的所有线程通常已都停止。 允许其他线程暂时运行可能对您的应用程序和调试器的状态的意外的影响可以忽略断点和这些线程上的异常等事件。

### <a name="bkmk_refreshWatch"></a> 刷新监视值

刷新图标 （环形箭头） 中可能会显示**监视**窗口时计算表达式。 刷新图标指示错误或已过期的值。 

若要刷新值，选择刷新图标，或按空格键。 调试器尝试重新计算该表达式。 但是，可能不需要，也将无法重新计算该表达式，具体取决于计算的值不是原因。 

悬停在刷新图标，或请参阅**值**列不计算该表达式的原因。 原因包括：

- 在计算表达式，如前面的示例中所示时发生错误。 超时可能会出现，或者变量可能超出范围。
  
- 表达式中有可能会触发在应用中的副作用的函数调用。 请参阅[表达式的副作用](#bkmk_sideEffects)。
  
- 已禁用的属性和隐式函数调用的自动求值。 
  
如果因为属性和隐式函数调用的自动求值已被禁用，将显示刷新图标，你可以通过选择启用它**启用属性求值和其他隐式函数调用**中**工具**  > **选项** > **调试** > **常规**。

若要演示如何使用刷新图标：

1. 在中**工具** > **选项** > **调试** > **常规**，清除**启用属性求值和其他隐式函数调用**复选框。 
   
1. 输入以下代码，然后在**Watch**窗口中，在设置监视`list.Count`属性。 
   
   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```
   
1. 开始调试。 **监视**窗口会显示类似于以下消息：
   
   ![刷新监视](../debugger/media/refreshwatch.png "刷新监视")
   
1. 若要刷新值，选择刷新图标，或按空格键。 调试器会重新计算该表达式。 

### <a name="bkmk_sideEffects"></a> 表达式的副作用 

计算某些表达式可以更改变量的值，或会影响您的应用程序的状态。 例如，计算下列表达式会更改 `var1`的值：

```csharp
var1 = var2
```

此代码可能会导致[副作用](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))。 副作用可使调试更加困难通过更改你的应用进行操作的方法。

只有一次，当你首次输入计算具有副作用的表达式。 之后，该表达式显示在灰**监视**禁用窗口中，并进一步评估。 工具提示或**值**列说明，该表达式会导致副作用。 可以通过选择出现在值旁边的刷新图标来强制重新计算。

若要阻止的负面影响指定的一种方法是关闭自动函数计算。 在中**工具** > **选项** > **调试** > **常规**，取消选择**启用属性求值和其他隐式函数调用**。

有关C#仅当关闭属性计算或隐式函数调用，您可以强制计算通过添加**ac**给一个变量的格式修饰符**名称**中**监视**窗口。 请参阅[格式说明符在 C# 中的](../debugger/format-specifiers-in-csharp.md)。

## <a name="bkmk_objectIds"></a> 在监视窗口中使用对象 Id (C#和 Visual Basic)

有时你想要观察特定对象的行为。 例如，你可能想要跟踪本地变量引用该变量超出范围后的对象。 在C#和 Visual Basic 中，您可以创建的特定实例的引用类型的对象 Id 和中使用它们**观看**窗口和断点条件中。 对象 ID 由公共语言运行时 (CLR) 调试服务生成并与对象相关联。

> [!NOTE]
> 对象 Id 创建弱引用，不会阻止对象被垃圾回收。 它们仅对当前调试会话有效。

在下面的代码中，`MakePerson()`方法创建`Person`使用本地变量： 

```csharp
class Person
{
    public Person(string name)
    {
        Name = name;
    }
    public string Name { get; set; }
}

public class Program
{
    static List<Person> _people = new List<Person>();
    public static void Main(string[] args)
    {
        MakePerson();
        DoSomething();
    }

    private static void MakePerson()
    {
        var p = new Person("Bob");
        _people.Add(p);
    }

    private static void DoSomething()
    {
        // more processing
         Console.WriteLine("done");
    }
}
```

若要了解的名称`Person`中`DoSomething()`方法，你可以添加对引用`Person`中的对象 ID**监视**窗口。

1. 之后在代码中设置断点`Person`创建对象。
   
1. 开始调试。
   
1. 当在断点处暂停执行时，打开**局部变量**通过选择窗口**调试** > **Windows** > **局部变量**.
   
1. 在中**局部变量**窗口中，右键单击`Person`变量，然后选择**创建对象 ID**。
   
   应会看到一个美元符号 (**$**) 在**局部变量**窗口中，这是对象 id。
   
1. 添加到的对象 ID **Watch**窗口中的右键单击对象 ID 并选择**添加监视**。
   
1. 在中设置另一个断点`DoSomething()`方法。
   
1. 继续调试。 当执行过程中暂停`DoSomething()`方法，**观看**窗口将显示`Person`对象。
   
   > [!NOTE]
   > 如果你想要查看对象的属性，如`Person.Name`，必须通过选择启用属性求值**工具** > **选项** >  **调试** > **常规** > **启用属性求值和其他隐式函数调用**。

## <a name="dynamic-view-and-the-watch-window"></a>动态视图和监视窗口

某些脚本语言 （例如，JavaScript 或 Python） 使用动态或[鸭子类型](https://en.wikipedia.org/wiki/Duck_typing)类型化和.NET 4.0 和更高版本支持很难在一般调试窗口中观察到的对象。

**Watch**窗口中显示这些对象作为动态对象，从实现的类型创建<xref:System.Dynamic.IDynamicMetaObjectProvider>接口。 动态对象节点显示动态成员的动态对象，但不允许编辑成员值。 

若要刷新**动态视图**值，选择[刷新图标](#bkmk_refreshWatch)动态对象节点旁边。 

若要仅显示**动态视图**对象，将添加**动态**动态对象名称后格式说明符**观看**窗口：

- 对于 C# 中： `ObjectName, dynamic`
- 对于 Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- C#调试器不会自动重新计算中的值**动态视图**当进入下一行代码。 
>- Visual Basic 调试程序会自动刷新通过添加的表达式**动态视图**。
>- 评估的成员**动态视图**可以[副作用](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))。 

**要插入新监视变量的对象强制转换为一个动态对象：**
  
1. 右键单击的任何子**动态视图**。
1. 选择**添加监视**。 `object.name`变得`((dynamic) object).name`，并显示在一个新**监视**窗口。

调试器还将添加**动态视图**于的对象的子节点**自动**窗口。 若要打开**自动**窗口中的，在调试期间，选择**调试** > **Windows** > **自动**。 

**动态视图**还增强了对 COM 对象的调试。 当在调试器进入 COM 对象包装在**System.__ComObject**，它将添加**动态视图**对象节点。

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>观察单个变量或使用快速监视表达式

可以使用**快速监视**观察单个变量。 

例如，对于下面的代码：

```csharp
static void Main(string[] args)
{
    int a, b;
    a = 1;
    b = 2;
    for (int i = 0; i < 10; i++)
    {
        a = a + b;
    }
}
```

若要观察`a`变量， 
   
1. 在 `a = a + b;` 行上设置断点。
   
1. 开始调试。 在断点处暂停执行。
   
1. 选择的变量`a`在代码中。
   
1. 选择**调试** > **快速监视**，按**Shift**+**F9**，或右键单击并选择**快速监视**。 
   
   **快速监视**此时将显示对话框。 `a`变量处于**表达式**框**值**的**1**。
   
   ![快速监视变量](../debugger/media/quickwatchvariable.png "快速监视变量")
   
1. 若要评估表达式中使用变量，键入一个表达式类似于`a + b`中**表达式**，然后选择**重新评估**。
   
   ![快速监视表达式](../debugger/media/quickwatchexpression.png "快速监视表达式")
   
1. 若要添加的变量或表达式从**快速监视**到**监视**窗口中，选择**添加监视**。
   
1. 选择**关闭**以关闭**快速监视**窗口。 (**快速监视**是模式对话框，因此无法继续调试，只要它已打开。)
   
1. 继续调试。 您可以观察中的变量**监视**窗口。

## <a name="see-also"></a>请参阅

 [什么是调试？](../debugger/what-is-debugging.md)  
 [使用Visual Studio写出最好的C#代码](../debugger/write-better-code-with-visual-studio.md)  
 [首次了解调试](../debugger/debugger-feature-tour.md) 
 [调试器窗口](../debugger/debugger-windows.md)
