---
title: 创建多实例工具窗口 |微软文档
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33585f623f846e16200d430ad2c886fe0874b537
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739623"
---
# <a name="create-a-multi-instance-tool-window"></a>创建多实例工具窗口
您可以对工具窗口进行编程，以便可以同时打开该工具窗口的多个实例。 默认情况下，工具窗口只能打开一个实例。

使用多实例工具窗口时，可以同时显示多个相关信息源。 例如，您可以将多行<xref:System.Windows.Forms.TextBox>控件放在多实例工具窗口中，以便在编程会话期间同时提供多个代码段。 此外，例如，您可以将<xref:System.Windows.Forms.DataGrid>控件和下拉列表框放在多实例工具窗口中，以便可以同时跟踪多个实时数据源。

## <a name="create-a-basic-single-instance-tool-window"></a>创建基本（单实例）工具窗口

1. 使用 VSIX 模板创建名为 **"多实例工具窗口**"的项目，并添加名为**MIToolWindow**的自定义工具窗口项模板。

    > [!NOTE]
    > 有关使用工具窗口创建扩展的详细信息，请参阅[使用工具窗口创建扩展](../extensibility/creating-an-extension-with-a-tool-window.md)。

## <a name="make-a-tool-window-multi-instance"></a>使工具窗口多实例

1. 打开*MIToolWindowPackage.cs*文件并找到该`ProvideToolWindow`属性。 和`MultiInstances=true`参数，如以下示例所示：

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. 在*MIToolWindowCommand.cs*文件中，查找方法`ShowToolWindow()`。 在此方法中，调用<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>方法并将其`create`标志设置为`false`，以便它将遍接现有工具窗口实例，直到找到可用实例。 `id`

3. 要创建工具窗口实例，请调用<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>方法并将其`id`设置为可用值，其`create`标志设置为`true`。

    默认情况下，`id`<xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>方法的参数的值为`0`。 此值创建一个单实例工具窗口。 要托管多个实例，每个实例都必须有自己的唯一`id`。

4. 调用<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>工具窗口实例<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame><xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A>的属性返回的对象上的方法。

5. 默认情况下，`ShowToolWindow`由工具窗口项模板创建的方法将创建一个单实例工具窗口。 下面的示例演示如何修改`ShowToolWindow`方法以创建多个实例。

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        for (int i = 0; i < 10; i++)
        {
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);
            if (window == null)
            {
                // Create the window with the first free ID.
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);
                if ((null == window) || (null == window.Frame))
                {
                    throw new NotSupportedException("Cannot create tool window");
                }

            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());
            break;
            }
        }
    }
    ```
