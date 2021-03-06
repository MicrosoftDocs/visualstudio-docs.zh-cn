---
title: 更新形状和连接线以反映模型
description: 了解，在 Visual Studio 中的域特定语言中，可以使形状的外观反映基础模型的状态。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6439a01de2a02361914ce227c43d903f1b24b405
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388563"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>更新形状和连接线以反映模型

在 Visual Studio 中的域特定语言中，你可以使形状的外观反映基础模型的状态。

应将本主题中的代码示例添加到 `.cs` 项目中的文件 `Dsl` 。 你需要在每个文件中执行以下指令：

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>设置形状映射属性以控制修饰器的可见性

您可以通过配置 DSL 定义中形状和域类之间的映射来控制修饰器的可见性，而无需编写程序代码。 有关详细信息，请参阅 [如何定义 Domain-Specific 语言](../modeling/how-to-define-a-domain-specific-language.md)。

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>以属性的形式公开形状的颜色和样式

在 DSL 定义中，右键单击该形状类，指向 "添加" " **公开**"，然后单击其中一个项（如 " **填充颜色**"）。

该形状现在具有可在程序代码或用户中设置的域属性。 例如，若要在命令或规则的程序代码中设置它，可以编写：

`shape.FillColor = System.Drawing.Color.Red;`

如果要仅在 "程序控制" （而不是用户）下设置属性变量，请在 DSL 定义关系图中选择新的域属性，如 **填充颜色** 。 然后，在属性窗口中，set 可 **浏览** 到， `false` 或设置 **为的 UI Readonly** `true` 。

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>定义更改规则以使颜色、样式或位置依赖于模型元素属性
 您可以定义规则，以便更新形状依赖于模型的其他部分的外观。 例如，您可以对模型元素定义一个更改规则，该规则元素根据模型元素的属性更新其形状的颜色。 有关更改规则的详细信息，请参阅 [规则在模型内部传播更改](../modeling/rules-propagate-changes-within-the-model.md)。

 只应使用规则来更新存储区中维护的属性，因为在执行 Undo 命令时不会调用规则。 这不包括一些图形功能，如形状的大小和可见性。 若要更新形状的这些功能，请参阅 [更新非存储图形功能](#OnAssociatedProperty)。

 下面的示例假定你已 `FillColor` 作为域属性公开，如前一部分中所述。

```csharp
[RuleOn(typeof(ExampleElement))]
  class ExampleElementPropertyRule : ChangeRule
  {
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)
    {
      base.ElementPropertyChanged(e);
      ExampleElement element = e.ModelElement as ExampleElement;
      // The rule is called for every property that is updated.
      // Therefore, verify which property changed:
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)
      {
        // There is usually only one shape:
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))
        {
          ExampleShape shape = pel as ExampleShape;
          // Replace this with a useful condition:
          shape.FillColor = element.Name.EndsWith("3")
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;
        }
      }
    }
  }
  // The rule must be registered:
  public partial class OnAssociatedPropertyExptDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(ExampleElementPropertyRule));
      // If you add more rules, list them here.
      return types.ToArray();
    }
  }
```

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>使用 OnChildConfigured 初始化形状的属性

若要在第一次创建时设置形状的属性，请 `OnChildConfigured()` 在关系图类的分部定义中进行重写。 关系图类在 DSL 定义中指定，生成的代码在 **Dsl\Generated Code\Diagram.cs** 中。 例如：

```csharp
partial class MyLanguageDiagram
{
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)
  {
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);
    ExampleShape shape = child as ExampleShape;
    if (shape != null)
    {
      if (!createdDuringViewFixup) return; // Ignore load from file.
      ExampleElement element = shape.ModelElement as ExampleElement;
      // Replace with a useful condition:
      shape.FillColor = element.Name.EndsWith("3")
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;
    }
    // else deal with other types of shapes and connectors.
  }
}
```

此方法可用于域属性和非存储功能，如形状的大小。

## <a name="use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a> 使用 AssociateValueWith () 更新形状的其他功能

对于某个形状的某些功能，例如，如果它具有阴影，或连接符的箭头样式，则没有将该功能作为域属性公开的内置方法。  对此类功能所做的更改不受事务系统控制。 因此，不适合使用规则对其进行更新，因为当用户执行撤消命令时不会调用规则。

相反，可以使用更新此类功能 <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A> 。 在下面的示例中，连接器的箭头样式是由连接器显示的关系中的域属性值控制的：

```csharp
public partial class ArrowConnector // My connector class.
{
    /// <summary>
    /// Called whenever a registered property changes in the associated model element.
    /// </summary>
    /// <param name="e"></param>
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)
    {
      base.OnAssociatedPropertyChanged(e);
      // Can be called for any property change. Therefore,
      // Verify that this is the property we're interested in:
      if ("IsDirected".Equals(e.PropertyName))
      {
        if (e.NewValue.Equals(true))
        { // Update the shape's built-in Decorator feature:
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;
        }
        else
        {
          this.DecoratorTo = null; // No arrowhead.
        }
      }
    }

    // OnAssociatedPropertyChanged is called only for properties
    // that have been registered using AssociateValueWith().
    // InitializeResources is a convenient place to call this.
    // This method is invoked only once per class, even though
    // it is an instance method.
    protected override void InitializeResources(StyleSet classStyleSet)
    {
      base.InitializeResources(classStyleSet);
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);
      // Add other properties here.
    }
}
```

`AssociateValueWith()` 对于要注册的每个域属性，应调用一次。 调用后，对指定属性所做的任何更改都将 `OnAssociatedPropertyChanged()` 在显示该属性的模型元素的任何形状中调用。

不需要 `AssociateValueWith()` 为每个实例调用。 尽管 InitializeResources 是一个实例方法，但对于每个 shape 类只调用一次。
