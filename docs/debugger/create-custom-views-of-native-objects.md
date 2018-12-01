---
title: 创建本机对象的自定义视图
description: 使用 Natvis 框架自定义 Visual Studio 调试器中显示本机类型的方式
ms.custom: ''
ms.date: 10/31/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 937692f11cbd642da823d6f7d13bcd90de59b388
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000856"
---
# <a name="create-custom-views-of-native-objects-in-the-debugger"></a>在调试器中创建本机对象的自定义视图

Visual Studio *Natvis* framework 在调试器变量窗口中自定义本机类型，比如在**局部变量**和**观看**窗口，以及**数据提示**窗口。 Natvis 可视化效果在调试期间可使更多类型可见。 

Natvis 替换了Visual Studio 的早期版本中的*autoexp.dat* XML 语法，提供了更好的诊断、版本控制，以及支持多个文件。  

Natvis 并不适用于：

- 使用 c + + Windows 桌面项目**调试器类型**设置为**混合**下**配置属性** > **调试**. 
- [混合模式调试](how-to-debug-in-mixed-mode.md)在托管的兼容模式下的 Windows 桌面应用程序 (**工具** > **选项** > **调试**  > **常规** > **使用托管的兼容模式**)。

## <a name="BKMK_Why_create_visualizations_"></a>Natvis 可视化效果

使用 Natvis 框架，可以为你创建的类型窗口可视化规则，以便开发人员在调试中可以更轻松地查看。  

例如，下 图显示类型的变量[Windows::UI::Xaml::Controls::TextBox](http://go.microsoft.com/fwlink/?LinkId=258422)在调试器窗口中未应用任何自定义可视化。  

![TextBox 默认可视化](../debugger/media/dbg_natvis_textbox_default.png "TextBox 默认可视化")  

高亮显示行显示 `Text` 类的 `TextBox` 属性。复杂的类层次结构使得难以找到此属性。 调试器不知道如何解释自定义字符串类型，因此你看不到文本框中的字符串。  

在变量窗口中，当应用 Natvis 可视化工具自定义规则时，同样的`TextBox`看起来要简单得多。类的重要成员在一起显示，且调试器显示自定义字符串类型的基础字符串值。  

![使用可视化工具的 TextBox 数据](../debugger/media/dbg_natvis_textbox_visualizer.png "使用可视化工具的 TextBox 数据")  

##  <a name="BKMK_Using_Natvis_files"></a>使用 C++ 项目中的.natvis 文件  

使用 Natvis *.natvis*文件指定可视化规则。 一个 *.natvis*文件是 XML 文件与 *.natvis*扩展。 Natvis 架构中定义 *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*。  

可视化条目表示基本结构 *.natvis*文件是一个或多个`Type`元素。 每个的完全限定的名称`Type`元素中指定其`Name`属性。  

```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
  <Type Name="MyNamespace::CFoo">  
    .  
    .  
  </Type>  

  <Type Name="...">  
    .  
    .  
  </Type>  
</AutoVisualizer>  
```  

Visual Studio 提供了一些 *.natvis*中的文件 *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*文件夹。 这些文件具有许多通用类型的可视化规则，并可作为用于编写新类型的可视化效果的示例。  

### <a name="add-a-natvis-file-to-a-c-project"></a>将.natvis 文件添加到 c + + 项目  

您可以添加 *.natvis*到任何 c + + 项目文件。  

**若要添加一个新 *.natvis*文件：**

1. 选择中的 c + + 项目节点**解决方案资源管理器**，然后选择**项目** > **添加新项**，或右键单击该项目并选择**添加**  > **新项**。
   
1. 在中**添加新项**对话框中，选择**Visual c + +** > **实用工具** > **调试器可视化文件 (.natvis)**. 
   
1. 命名该文件，然后选择**添加**。
   
   新文件添加到**解决方案资源管理器**，并在 Visual Studio 文档窗格中打开。 

Visual Studio 调试器自动加载 *.natvis* c + + 项目中的文件，并且默认情况下，还在生成项目时在 *.pdb* 文件包含它们。 如果调试生成的应用程序时，调试器将从 *.pdb* 文件加载 *.natvis* 文件，即使你没有打开该项目。 如果不想在 *.pdb* 文件中包含 *.natvis* 文件，你可以从生成中排除它 *.pdb* 文件。

**从 *.pdb*文件中排除 *.natvis*文件:**

1. 在 **解决方案资源管理器** 中选择 *.natvis* 文件，然后选择**属性**图标，或右键单击该文件并选择**属性**.
   
1. 选择下拉列表箭头旁边的**从生成中排除**，然后选择**是**，选择**确定**。  

>[!NOTE]
>对于正在调试可执行文件的项目，使用解决方案项添加 *.pdb* 中任何不存在的 *.natvis* 文件，因为没有可用的 c + + 项目。  

>[!NOTE]
>*.pdb文件* 加载 Natvis 规则 仅适用于 *.pdb* 模块中的文件类型引用。例如，如果 *Module1.pdb* 具有名为`Test`类型的 Natvis 条目，它仅适用于 *Module1.dll* 中的 `Test`类 。 如果另一个模块还定义一个名为`Test` 的类，则 *Module1.pdb* Natvis 条目将不适用于它。  

### <a name="BKMK_natvis_location"></a> Natvis 文件位置  

您可以添加 *.natvis* 文件到你的用户目录或系统目录中，如果你希望它们适用于多个项目。  

*.Natvis* 文件按以下顺序计算：  

1. 任何嵌入 *.pdb* 文件中的 *.natvis* 文件中你进行调试时，除非加载的项目中存在的同名文件。  

1. 任何c + + 项目或顶级解决方案中加载的 *.natvis* 文件。 此组包括所有已加载的 c + + 项目，包括其他语言中的类库，但不是项目。 

1.  特定于用户的 Natvis 目录 (例如， *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*)。  

1.  系统级 Natvis 目录 (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*)。 此目录随 Visual Studio 一起安装的 *.natvis* 文件。 如果您具有管理员权限，可以将文件添加到此目录中。  

## <a name="modify-natvis-files-while-debugging"></a>在调试时修改.natvis 文件  

您可以在IDE调试时，修改项目的 *.natvis* 文件。 在Visual Studio打开同一个文件实例，进行调试时，修改然后保存该文件。 在该文件保存后， **监视** 和 **局部变量** 窗口自动刷新，显示已改变的内容。 

在调试解决方案时，可以添加或删除 *.natvis* 文件，并且 Visual Studio 将随之添加或删除相关的可视化效果。  

在进行调试时无法更新已嵌入 *.pdb* 文件中的 *.natvis* 文件。  

如果你在 Visual Studio 外部修改 *.natvis文件* ，所做的更改不会自动生效。 若要更新调试器窗口，可以在 **监视** 窗口中，使用 **.natvisreload** 命令重新计算。 然后无需重新启动调试会话，更改自动生效。  

此外使用 **.natvisreload** 命令，将升级 *.natvis* 文件到较新版本。 例如， *.natvis* 文件可能签入源代码管理，并且你需要获得其它人最近所做的改动。 

##  <a name="BKMK_Expressions_and_formatting"></a> 表达式和格式化  
Natvis 可视化效果使用 C++ 表达式指定需显示的数据项。 除了[上下文运算符 （c + +）](../debugger/context-operator-cpp.md)所述，在调试器中增强和限制 c + + 表达式功能，还要注意以下事项：  

- Natvis 表达式在可视化对象上下文而非当前堆栈框架中进行计算。 例如，`x`在 Natvis 表达式引用了名为字段**x**中不到名为的本地变量进行可视化的对象**x**位于当前函数。 但您可以访问全局变量，不能访问 Natvis 表达式中的局部变量。  

- Natvis 表达式不允许函数求值或副作用。 函数调用和赋值运算符将被忽略。 由于 [调试器内部函数](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) 没有副作用，因此可以从所有 Natvis 表达式自由调用它们，即使不允许其他函数调用。  

- 若要控制表达式的显示方式，可以使用[格式说明符在 c + +](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers)中所述的任何格式说明符。 在natvis内部时，将忽略格式说明符，如[ArrayItems 展开](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion)中的`Size`表达式。  

## <a name="natvis-views"></a>Natvis 视图  

您可以定义不同的 Natvis 视图以不同方式显示类型。 例如，下面是的可视化效果`std::vector`，它定义一个名为`simple`的简化的视图。 在默认视图和`simple`视图中显示`DisplayString`和`ArrayItems`元素，而`[size]`并`[capacity]`项中未显示`simple`视图。 

```xml
<Type Name="std::vector&lt;*&gt;">  
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>  
    <Expand>  
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>  
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>  
        <ArrayItems>  
            <Size>_Mylast - _Myfirst</Size>  
            <ValuePointer>_Myfirst</ValuePointer>  
        </ArrayItems>  
    </Expand>  
</Type>  
```  


在中**监视**窗口中，使用 **，查看**格式说明符来指定替代视图。 简单视图将显示为**vec,view(simple)**:  

![具有简单视图的监视窗口](../debugger/media/watch-simpleview.png "具有简单视图的监视窗口")  

##  <a name="BKMK_Diagnosing_Natvis_errors"></a> Natvis 错误  

当调试器遇到可视化条目中的错误时，它将忽略它们。 它在其原始格式显示的类型，或选取其他适当的可视化效果时。 可以使用 Natvis 诊断，来帮助了解为什么调试器忽略可视化条目，还可以查看基础语法和分析错误。 

**若要打开 Natvis 诊断：**

- 下**工具** > **选项**(或**调试** > **选项**) >**调试** > **输出窗口**，将**Natvis 诊断消息 （c + +）** 到**错误**，**警告**，或**详细**，然后选择**确定**。 

错误会显示在**输出**窗口。  

##  <a name="BKMK_Syntax_reference"></a> Natvis 语法参考  

###  <a name="BKMK_AutoVisualizer"></a> AutoVisualizer 元素  
`AutoVisualizer`元素是*.natvis*文件的根节点，并包含命名空间`xmlns:`属性。 

```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

`AutoVisualizer`元素可以具有[类型](#BKMK_Type)， [HResult](#BKMK_HResult)， [UIVisualizer](#BKMK_UIVisualizer)，并且[CustomVisualizer](#BKMK_CustomVisualizer)子级。 

###  <a name="BKMK_Type"></a>Type 元素  

基本`Type`如本示例所示：  

```xml
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  
```  

 `Type`元素指定：  

1. 有关应使用哪种类型的可视化效果 (`Name`属性)。  
   
2. 该类型的对象的值是什么样的（ `DisplayString` 元素）。  
   
3. 该类型的成员应如下所示在变量窗口中展开的类型 (`Expand`节点)。  
   
#### <a name="templated-classes"></a>模板化类
`Name`的属性`Type`元素接受一个星号`*`作为可用于模板化类名的通配符字符。  

在以下示例中，无论对象是使用相同的可视化效果`CAtlArray<int>`或`CAtlArray<float>`。 如果没有为特定可视化条目`CAtlArray<float>`，则它将优先于泛型条目。  

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

可以使用宏 $T1 和 $T2，引用在可视化条目中的模板参数等。 若要查找这些宏的示例，请参阅 *.natvis*文件随 Visual Studio。  

####  <a name="BKMK_Visualizer_type_matching"></a> 可视化工具类型匹配  
如果可视化条目无法进行验证，则使用下一个可用的可视化效果。  

#### <a name="inheritable-attribute"></a>可继承的特性  
可选`Inheritable`属性指定一个可视化效果仅适用于基类型，还是对基类型及其所有派生类型。 `Inheritable` 的默认值为 `true`。  

在以下示例中，可视化效果仅适用于`BaseClass`类型：  

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

#### <a name="priority-attribute"></a>优先级特性  

可选`Priority`属性指定要在其中使用备用定义的顺序，如果某个定义无法分析。 可能值`Priority`是： `Low`， `MediumLow`，`Medium`， `MediumHigh`，并`High`。 默认值为 `Medium`。 `Priority`属性用于区分仅内相同的优先级 *.natvis*文件。  

下面的示例首先分析与 2015 STL 匹配的条目。 如果分析失败，它会使用 STL 的 2013年版本的备用条目：  

```xml
<!-- VC 2013 -->  
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">  
     <DisplayString>{_Callee}</DisplayString>  
    <Expand>  
        <ExpandedItem>_Callee</ExpandedItem>  
    </Expand>  
</Type>  

<!-- VC 2015 -->  
<Type Name="std::reference_wrapper&lt;*&gt;">  
    <DisplayString>{*_Ptr}</DisplayString>  
    <Expand>  
        <Item Name="[ptr]">_Ptr</Item>  
    </Expand>  
</Type>  
```  

### <a name="optional-attribute"></a>可选特性  
可以将`Optional`的任何节点上的属性。 如果无法分析可选节点内的子表达式，调试器将忽略该节点，但将应用的其余部分`Type`规则。 在下面的类型中， `[State]` 不可选，但 `[Exception]` 可选。  如果`MyNamespace::MyClass`有一个名为 _`M_exceptionHolder`，这两种`[State]`节点和`[Exception]`节点显示，但是，如果没有`_M_exceptionHolder`字段中，仅`[State]`节点出现。

```xml
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

###  <a name="BKMK_Condition_attribute"></a> 条件属性  

可选`Condition`属性可用于许多可视化元素，并指定何时使用可视化规则。 如果条件特性内的表达式解析为`false`，则可视化规则不适用。 如果其计算结果为`true`，或者没有任何`Condition`应用特性，可视化效果。 此属性可用于在可视化条目中 if-else 逻辑。 

例如，以下可视化效果具有两个`DisplayString`智能指针类型的元素。 当`_Myptr`成员为空，第一个条件`DisplayString`元素解析为`true`，因此该窗体显示。 当`_Myptr`成员不为空，该条件计算结果为`false`，第二个`DisplayString`元素显示。  

```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
```  

### <a name="includeview-and-excludeview-attributes"></a>IncludeView 和 ExcludeView 特性  

`IncludeView`和`ExcludeView`属性指定要显示或不在特定视图中显示的元素。 例如，在以下的 Natvis 规范`std::vector`，则`simple`视图不显示`[size]`和`[capacity]`项。

```xml
<Type Name="std::vector&lt;*&gt;">  
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>  
    <Expand>  
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>  
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>  
        <ArrayItems>  
            <Size>_Mylast - _Myfirst</Size>  
            <ValuePointer>_Myfirst</ValuePointer>  
        </ArrayItems>  
    </Expand>  
</Type>  
```  

可以使用`IncludeView`和`ExcludeView`类型及各个成员属性。  

###  <a name="BKMK_Versioning"></a> Version 元素  
`Version`元素的范围限定为特定模块及版本的可视化条目。 `Version`元素可帮助避免发生名称冲突，可减少无意匹配，并允许不同类型的版本的不同可视化效果。  

如果由不同模块使用的常见头文件定义了一种类型，版本控制的可视化效果时才出现类型中指定的模块版本。  

在以下示例中，可视化效果是仅适用于`DirectUI::Border`中找到类型`Windows.UI.Xaml.dll`从 1.0 到 1.5 版。 

```xml
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

###  <a name="BKMK_DisplayString"></a> DisplayString 元素 
`DisplayString`元素指定要显示为变量的值的字符串。 它接受混合表达式的任意字符串。 大括号内的所有内容都可解释为表达式。 例如，以下`DisplayString`条目：  

```xml
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  
```  

表示类型的变量`CPoint`显示如此图中所示：  

 ![使用 DisplayString 元素](../debugger/media/dbg_natvis_cpoint_displaystring.png "使用 DisplayString 元素")  

中`DisplayString`表达式中，`x`和`y`，这属于`CPoint`，是大括号内，因此它们的值进行评估。 该示例还演示如何通过使用双大括号转义大括号 (`{{`或`}}`)。  

> [!NOTE]
> `DisplayString` 元素是唯一接受任意字符串和大括号语法的元素。 所有其他可视化元素接受调试器可以计算的表达式。  

###  <a name="BKMK_StringView"></a> StringView 元素 

`StringView`元素定义一个值，调试器可以将发送到内置文本可视化工具。 例如，给定以下可视化效果`ATL::CStringT`类型：  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>
```  

`CStringT`如下例所示的变量窗口中显示的对象：   

![CStringT DisplayString 元素](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT DisplayString 元素")  

添加`StringView`元素告知调试器，它可以将值显示为文本可视化效果。  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

在调试期间，您可以选择该变量旁边的放大镜图标，然后选择**文本可视化工具**来显示字符串的**m_pszData**指向。  

 ![使用 StringView 可视化工具的 CStringT 数据](../debugger/media/dbg_natvis_stringview_cstringt.png "使用 StringView 可视化工具的 CStringT 数据")  

表达式`{m_pszData,su}`包含 c + + 格式说明符**su**，以将值显示为 Unicode 字符串。 有关详细信息，请参阅[格式说明符在 c + +](../debugger/format-specifiers-in-cpp.md)。  

###  <a name="BKMK_Expand"></a> 展开元素 

可选`Expand`节点自定义可视化类型的子级时展开变量窗口中的类型。 `Expand`节点接受定义子元素的子节点的列表。  

- 如果`Expand`节点不指定在可视化条目中，子级使用默认展开规则。  
  
- 如果`Expand`节点指定与在其下没有子节点类型在调试器窗口中无法进行扩展。  

####  <a name="BKMK_Item_expansion"></a> Item 展开  

 `Item`元素是在最基本的常见元素`Expand`节点。 `Item` 定义单个子元素。 例如，`CRect`类的字段`top`， `left`， `right`，和`bottom`具有以下可视化条目：  

```xml
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  
```  

在调试器窗口中，`CRect`类型看起来如下例所示：  

![具有 Item 元素扩展的 CRect](../debugger/media/dbg_natvis_expand_item_crect1.png "具有 Item 元素扩展的 CRect")  

调试器将计算中指定的表达式`Width`并`Height`元素，并显示中的值**值**变量窗口中的列。 

调试器会自动创建 **[原始视图]** 为每个自定义扩展的节点。 上面的屏幕截图显示 **[原始视图]** 展开节点，以显示该对象的默认原始视图与其 Natvis 可视化的区别。 默认展开创建基类的子树，并列出所有数据成员的类的基类作为子级。  

> [!NOTE]
> 如果项元素的表达式指向一个复杂类型，**项**节点本身是可展开。  

####  <a name="BKMK_ArrayItems_expansion"></a> Size  
使用 `ArrayItems` 节点使 Visual Studio 调试器将类型解释为数组并显示其各个元素。 `std::vector` 的可视化效果是一个很好的示例：  

```xml
<Type Name="std::vector&lt;*&gt;">  
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_Mylast - _Myfirst</Item>  
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>  
    <ArrayItems>  
      <Size>_Mylast - _Myfirst</Size>  
      <ValuePointer>_Myfirst</ValuePointer>  
    </ArrayItems>  
  </Expand>  
</Type>  
```  

`std::vector` 在变量窗口中展开时显示其自身的元素：  

![使用 ArrayItems 扩展的 std:: vector](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std:: vector 使用 ArrayItems 扩展")  

`ArrayItems`节点必须具有：  

- 一个`Size`（求值表达式必须为整数） 为使调试器了解数组长度。  
- 一个`ValuePointer`指向第一个元素的表达式 (它必须是不是元素类型的指针`void*`)。  

数组下限的默认值为 0。 若要覆盖的值，请使用`LowerBound`元素。 *.Natvis*文件随 Visual Studio 提供了示例。  

>[!NOTE]
>可以使用`[]`运算符，例如`vector[i]`，使用任何一维数组可视化效果`ArrayItems`，即使该类型本身 (例如`CATLArray`) 不允许此运算符。  

此外可以指定多维数组。 在这种情况下，调试器需要稍多的信息来正确显示子元素：  

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">  
  <DisplayString>extent = {_M_extent}</DisplayString>  
  <Expand>  
    <Item Name="extent">_M_extent</Item>  
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">  
      <Direction>Forward</Direction>  
      <Rank>$T2</Rank>  
      <Size>_M_extent._M_base[$i]</Size>  
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>  
    </ArrayItems>  
  </Expand>  
</Type>  
```  

- `Direction` 指定数组是行优先顺序还是列优先顺序中。 
- `Rank` 指定数组的秩。 
- `Size`元素接受的隐式`$i`参数，它将替换为维索引以查找该维度中数组的长度。 在上一示例中，表达式`_M_extent.M_base[0]`应为提供的第 0 个维度长度`_M_extent._M_base[1]`当月 1 日起，依次类推。  

下面是一个二维`Concurrency::array`对象在调试器窗口中所示：  

![具有 ArrayItems 扩展的二维数组](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "具有 ArrayItems 扩展的二维数组")  

####  <a name="BKMK_IndexListItems_expansion"></a> IndexListItems 展开  

可以使用`ArrayItems`扩展仅当数组元素连续排列在内存中。 调试器通过其指针递增只需获取的下一个元素。 如果您需要处理的值节点的索引，使用`IndexListItems`节点。 下面是使用可视化`IndexListItems`节点：  

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">  
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_M_vector._M_index</Item>  
    <IndexListItems>  
      <Size>_M_vector._M_index</Size>  
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>  
    </IndexListItems>  
  </Expand>  
</Type>  
```  

之间的唯一区别`ArrayItems`并`IndexListItems`是`ValueNode`，它应在整个表达式的 i<sup>th</sup>具有隐式元素`$i`参数。  

>[!NOTE]
>可以使用`[]`运算符，例如`vector[i]`，使用任何一维数组可视化效果`IndexListItems`，即使该类型本身 (例如`CATLArray`) 不允许此运算符。  

####  <a name="BKMK_LinkedListItems_expansion"></a> LinkedListItems 展开  

如果可视化类型表示一个链接列表，则调试器可以通过使用 `LinkedListItems` 节点显示其子级。 以下可视化效果`CAtlList`类型使用`LinkedListItems`:  

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">  
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>  
  <Expand>  
    <Item Name="Count">m_nElements</Item>  
    <LinkedListItems>  
      <Size>m_nElements</Size>  
      <HeadPointer>m_pHead</HeadPointer>  
      <NextPointer>m_pNext</NextPointer>  
      <ValueNode>m_element</ValueNode>  
    </LinkedListItems>  
  </Expand>  
</Type>  
```  

`Size` 元素引用该列表的长度。 `HeadPointer` 指向第一个元素， `NextPointer` 引用下一个元素，而 `ValueNode` 引用项的值。  

调试器将计算`NextPointer`并`ValueNode`的上下文中的表达式`LinkedListItems`节点元素中，不是父列表类型。 在前面的示例中，`CAtlList`已`CNode`类 (位于`atlcoll.h`)，它是链接列表的节点。 `m_pNext` 并`m_element`是的字段`CNode`类，不是`CAtlList`类。  

`ValueNode` 可以留空，或使用`this`来指代`LinkedListItems`节点本身。  

#### <a name="customlistitems-expansion"></a>CustomListItems 展开  
`CustomListItems` 展开允许编写自定义逻辑，以遍历数据结构（如哈希表）。 使用`CustomListItems`可视化数据结构，可以使用 c + + 表达式的都需要评估，但不完全适合窗口`ArrayItems`， `IndexListItems`，或`LinkedListItems`。  

以下可视化工具`CAtlMap`是一个极好示例其中`CustomListItems`适用。  

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">  
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>  
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>  
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>  
    <Expand>  
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">  
        <Variable Name="iBucket" InitialValue="-1" />  
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />  
        <Variable Name="iBucketIncrement" InitialValue="-1" />  

        <Size>m_nElements</Size>  
        <Exec>pBucket = nullptr</Exec>  
        <Loop>  
          <If Condition="pBucket == nullptr">  
            <Exec>iBucket++</Exec>  
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>  
            <Break Condition="iBucketIncrement == -1" />  
            <Exec>iBucket += iBucketIncrement</Exec>  
            <Exec>pBucket = m_ppBins[iBucket]</Exec>  
          </If>  
          <Item>pBucket,na</Item>  
          <Exec>pBucket = pBucket->m_pNext</Exec>  
        </Loop>  
      </CustomListItems>  
    </Expand>  
</Type>  
```  

可以使用`Exec`若要执行的内部代码`CustomListItems`扩展，使用变量和扩展中定义的对象。 可以使用逻辑运算符、 算术运算符和赋值运算符与`Exec`。 不能使用`Exec`来计算函数。

`CustomListItems` 支持以下内部函数：

- `strlen`, `wcslen`, `strnlen`, `wcsnlen`, `strcmp`, `wcscmp`, `_stricmp`, `_strcmpi`, `_wcsicmp`, `strncmp`, `wcsncmp`, `_strnicmp`, `_wcsnicmp`, `memcmp`, `memicmp`, `wmemcmp`, `strchr`, `wcschr`, `memchr`, `wmemchr`, `strstr`, `wcsstr`, `__log2`, `__findNonNull`
- `GetLastError`, `TlsGetValue`, `DecodeHString`, `WindowsGetStringLen`, `WindowsGetStringRawBuffer`, `WindowsCompareStringOrdinal`, `RoInspectCapturedStackBackTrace`, `CoDecodeProxy`, `GetEnvBlockLength`, `DecodeWinRTRestrictedException`, `DynamicMemberLookup`, `DecodePointer`, `DynamicCast`
- `ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)`
- `ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)`
- `ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `Stdext_HashMap_Int_OperatorBracket_idx`
- `Std_UnorderedMap_Int_OperatorBracket_idx`
- `TreeTraverse_Init // Initializes a new tree traversal`
- `TreeTraverse_Next // Returns nodes in a tree`
- `TreeTraverse_Skip // Skips nodes in a pending tree traversal`

####  <a name="BKMK_TreeItems_expansion"></a> TreeItems 展开  
 如果可视化类型表示一个树，则调试器可以通过使用 `TreeItems` 节点遍历该树并显示其子级。 下面是用于可视化效果`std::map`类型使用`TreeItems`节点：  

```xml
<Type Name="std::map&lt;*&gt;">  
  <DisplayString>{{size = {_Mysize}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_Mysize</Item>  
    <Item Name="[comp]">comp</Item>  
    <TreeItems>  
      <Size>_Mysize</Size>  
      <HeadPointer>_Myhead->_Parent</HeadPointer>  
      <LeftPointer>_Left</LeftPointer>  
      <RightPointer>_Right</RightPointer>  
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>  
    </TreeItems>  
  </Expand>  
</Type>  
```  

语法是类似于`LinkedListItems`节点。 `LeftPointer``RightPointer`，和`ValueNode`树节点类的上下文中计算。 `ValueNode` 可以保留为空或使用`this`来指代`TreeItems`节点本身。  

####  <a name="BKMK_ExpandedItem_expansion"></a> ExpandedItem 展开  
 `ExpandedItem`元素通过显示基的类或数据成员的属性，就好像该可视化类型的子级生成合成的子视图。 调试器将计算指定的表达式，并将结果的子节点追加到该可视化类型的子列表。 

例如，智能指针类型`auto_ptr<vector<int>>`通常显示为：  

 ![自动&#95;ptr&#60;矢量&#60;int&#62; &#62;默认扩展](../debugger/media/dbg_natvis_expand_expandeditem_default.png "默认扩展")  

 若要查看矢量的值，必须向下钻取两个级别在变量窗口中，通过传递`_Myptr`成员。 通过添加`ExpandedItem`元素，则可以消除`_Myptr`变量，从层次结构，并直接查看矢量元素：  

```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
```  

 ![自动&#95;ptr&#60;矢量&#60;int&#62; &#62; ExpandedItem 扩展](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "ExpandedItem 扩展")  

下面的示例演示如何从派生类中的基类聚合属性。 假定 `CPanel` 类派生自 `CFrameworkElement`。 而不是重复来自基属性`CFrameworkElement`类，`ExpandedItem`节点的可视化效果将这些属性追加到的子列表`CPanel`类。 

```xml
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  
```  

**Nd**格式说明符，这将关闭与匹配的派生类的可视化效果，在此有必要。 否则为表达式`*(CFrameworkElement*)this`会导致`CPanel`可视化效果，以应用，同样，因为默认可视化类型匹配规则认为最适合的选项。 使用**nd**格式说明符指示调试器使用基类可视化效果或默认扩展，如果基类没有可视化效果。  

####  <a name="BKMK_Synthetic_Item_expansion"></a> 综合 item 展开  
 虽然`ExpandedItem`元素通过消除层次结构，提供数据的逼真的内容视图`Synthetic`节点则恰好相反。 它允许你创建人工子元素的不是表达式的结果。 人工元素可以具有其自己的子元素。 在下面的示例中， `Concurrency::array` 类型的可视化效果使用 `Synthetic` 节点向用户显示诊断消息：  

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">  
  <DisplayString>extent = {_M_extent}</DisplayString>  
  <Expand>  
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>  
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">  
      <Rank>$T2</Rank>  
      <Size>_M_extent._M_base[$i]</Size>  
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>  
    </ArrayItems>  
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">  
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>  
    </Synthetic>  
  </Expand>  
</Type>  
```  

 ![通过综合元素扩展的 concurrency:: array](../debugger/media/dbg_natvis_expand_synthetic.png "具有综合元素扩展的 concurrency:: array")  

###  <a name="BKMK_HResult"></a> HResult 元素 
 `HResult`元素可用于自定义显示的信息**HRESULT**调试器窗口中。 `HRValue`元素必须包含的 32 位值**HRESULT**要进行自定义。 `HRDescription`元素包含要在调试器窗口中显示的信息。  

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

###  <a name="BKMK_UIVisualizer"></a> UIVisualizer 元素 
`UIVisualizer` 元素向调试器注册图形可视化工具插件。 图形可视化工具创建对话框或其他变量或对象的方法显示其数据类型与一致的接口。 可视化工具插件必须编写为[VSPackage](../extensibility/internals/vspackages.md)，并且必须公开调试器可以通过使用的服务。 *.Natvis*文件包含注册插件的信息，例如其名称、 公开的服务，以及它可以直观显示的类型的 GUID。  

下面是 UIVisualizer 元素的示例：  

```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"   
        Id="1" MenuName="Vector Visualizer"/>  
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"   
        Id="2" MenuName="List Visualizer"/>  
.  
.  
</AutoVisualizer>  
```  

- 一个`ServiceId`  -  `Id`特性对标识`UIVisualizer`。 `ServiceId`是包公开的服务，可视化工具的 GUID。 `Id` 如果服务提供多个，是可视化工具，用于区分开来的唯一标识符。 在上述示例中，相同的可视化工具服务提供两个可视化工具。  
  
- `MenuName`属性定义要在调试器中的放大镜图标旁边的下拉列表中显示的可视化工具名称。 例如：  

  ![UIVisualizer 菜单快捷方式菜单](../debugger/media/dbg_natvis_vectorvisualizer.png "UIVisualizer 菜单快捷方式菜单")  

每种类型中定义 *.natvis*文件都必须显式列出可以将其显示任何 UI 可视化工具。 调试器会匹配类型条目中的可视化工具引用的已注册的可视化工具。 例如，以下类型条目`std::vector`引用`UIVisualizer`在前面的示例。  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 您可以看到的示例`UIVisualizer`中[图像监视](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.ImageWatch2017)扩展用于查看内存中的位图。 

### <a name="BKMK_CustomVisualizer"></a>CustomVisualizer 元素  
 `CustomVisualizer` 是指定 VSIX 扩展，用于控制在 Visual Studio code 中的可视化效果编写一个扩展点。 有关编写 VSIX 扩展的详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。 

它是要编写 XML Natvis 定义比自定义可视化工具的更多工作，但您可以随时从有关 Natvis 支持或不支持的约束。 自定义可视化工具有权访问调试器扩展性 Api，它可以查询和修改调试对象进程或与 Visual Studio 的其他部分进行通信的完整集。  

 可以使用`Condition`， `IncludeView`，并`ExcludeView`上的特性`CustomVisualizer`元素。
