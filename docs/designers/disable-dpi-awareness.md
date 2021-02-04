---
title: 在 Visual Studio 中禁用 DPI 感知
description: 讨论 HDPI 监视器上 Windows 窗体设计器的限制，以及如何以非 DPI 感知进程的形式运行 Visual Studio。
ms.date: 09/28/2020
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.topic: conceptual
ms.openlocfilehash: 08eb15914ad381fd81a838f5e09a1350bedff4fd
ms.sourcegitcommit: 31f216b5f7491d5558de5b7ea4ebb0eb1faa3b9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91493304"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>在 Visual Studio 中禁用 DPI 感知

Visual Studio 是一个每英寸点数 (DPI) 感知应用程序，因此其显示可以自动缩放。 如果某个应用程序声明自己是非 DPI 感知应用程序，则操作系统将该应用程序作为位图缩放。 此行为也称为 DPI 虚拟化。 应用程序仍会认为它以 100% 缩放比例（即 96 dpi）运行。

本文讨论 HDPI 监视器上 Windows 窗体设计器的限制，以及如何以非 DPI 感知进程的形式运行 Visual Studio。

## <a name="windows-forms-designer-on-hdpi-monitors"></a>HDPI 监视器上的 Windows 窗体设计器

Visual Studio 中的 Windows 窗体设计器不支持缩放  。 因此，在高每英寸点数 (HDPI ) 监视器上，在 Windows 窗体设计器中打开某些窗体时，会出现显示问题  。 例如，控件可能会出现重叠，如下图所示：

![HDPI 监视器上的 Windows 窗体设计器](./media/win-forms-designer-hdpi.png)

在 HDPI 监视器上，在 Visual Studio 中从 Windows 窗体设计器打开窗体时，Visual Studio 将在设计器的顶部显示一个黄色的信息栏  ：

![Visual Studio 中的信息栏，要求以非 DPI 感知模式重启](./media/scaling-gold-bar.png)

消息为“主显示器上的缩放比例设置为 200% (192 dpi)。  这可能会导致设计器窗口中出现呈现问题”。

> [!NOTE]
> 此信息栏是在 Visual Studio 2017 版本 15.8 中引入的。

如果不在设计器中工作，并且无需调整窗体的布局，可以忽略该信息栏，在代码编辑器或其他类型的设计器中继续工作。 （还可以[禁用通知](#disable-notifications)，以便信息栏不会继续显示。）只有 Windows 窗体设计器才会受到影响  。 如果确实需要在 Windows 窗体设计器中工作，下一部分将帮助你[解决问题](#to-resolve-the-display-problem)  。

## <a name="to-resolve-the-display-problem"></a>解决显示问题

有三个选项可解决显示问题：

- [以非 DPI 感知进程的形式重启 Visual Studio](#restart-visual-studio-as-a-dpi-unaware-process)
- [添加注册表项](#add-a-registry-entry)
- [将显示缩放比例设置为 100%](#set-your-display-scaling-setting-to-100)

> [!TIP]
> 如果更希望通过命令行管理设置，可使用 [`devenv.exe`](../ide/reference/devenv-command-line-switches.md) 将 `/noscale` 作为命令行参数，在 100% 缩放模式下运行。

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>以非 DPI 感知进程的形式重启 Visual Studio

在黄色信息栏上选择该选项，可以非 DPI 感知进程的形式重启 Visual Studio。 这是解决问题的首选方法。

以非 DPI 感知进程的形式运行 Visual Studio 时，设计器布局问题会得到解决，但字体可能会变得模糊。 以非 DPI 感知进程的形式运行 Visual Studio 时，Visual Studio 将显示另一条黄色信息性消息，表示“Visual Studio 正在以非 DPI 感知进程的形式运行。  WPF 和 XAML 设计器可能无法正确显示。” 此信息栏还提供了一个选项，“以非 DPI 感知进程的形式重启 Visual Studio”  。

> [!NOTE]
> - 选择以非 DPI 感知进程的形式重启 Visual Studio 的选项时，如果 Visual Studio 中有未停靠的工具窗口，则这些工具窗口的位置可能会发生更改。
> - 如果使用默认的 Visual Basic 配置文件，或者在“工具” > “选项” > “项目和解决方案”中取消选择了“创建时保存新项目”选项，则 Visual Studio 以非 DPI 感知进程的形式重启时无法重新打开该项目     。 但是，可以通过在“文件” > “最近使用的项目和解决方案”下选择该项目将其打开   。

在 Windows 窗体设计器中完成操作后，必须以 DPI 感知进程的形式重启 Visual Studio  。 当 Visual Studio 以非 DPI 感知进程的形式运行时，字体可能看起来模糊不清，XAML 设计器等其他设计器中也可能出现显示问题  。 如果在 Visual Studio 以非 DPI 感知模式运行时，将其关闭并重新打开，它会再次变为 DPI 感知。 还可以在信息栏中选择“以 DPI 感知进程的形式重启 Visual Studio”选项。

### <a name="add-a-registry-entry"></a>添加注册表项

可以通过修改注册表将 Visual Studio 标记为非 DPI 感知。 打开注册表编辑器并向 HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers 子项添加项   ：

**项**：根据所使用的是 Visual Studio 2017 还是 2019，请使用以下值之一：

- C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> 如果你正在使用 Visual Studio Professional 或 Enterprise Edition，请将该项中的“Community”替换为“Professional”或“Enterprise”    。 还可根据需要替换驱动器号。

**类型**：REG_SZ

**值**：DPIUNAWARE

> [!NOTE]
> 在删除注册表项之前，Visual Studio 将保持非 DPI 感知模式。

### <a name="set-your-display-scaling-setting-to-100"></a>将显示缩放比例设置为 100%

若要在 Windows 10 中将显示缩放比例设置为 100%，请在任务栏的搜索框中键入“显示设置”，然后选择“更改显示设置”   。 在“设置”窗口中，将“更改文本、应用和其他项的大小”设置为“100%”    。

将显示缩放比例设置为 100% 可能不太理想，因为这可能会使用户界面太小而无法使用。

## <a name="disable-notifications"></a>禁用通知

可以在 Visual Studio 中选择不接收 DPI 缩放问题的通知。 例如，如果不在设计器中工作，可能需要禁用通知。

若要禁用通知，请选择“工具” > “选项”，打开“选项”对话框    。 然后选择“Windows 窗体设计器” > “常规”，然后将“DPI 缩放通知”设置为“False”     。

![Visual Studio 中的 DPI 缩放通知选项](./media/notifications-option.png)

如果稍后要重新启用缩放通知，请将此属性设置为“True”  。

## <a name="troubleshoot"></a>疑难解答

如果 DPI 感知转换在 Visual Studio 中未按预期方式工作，请检查注册表编辑器中的 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe 子项中是否有 `dpiAwareness` 值  。 如果存在该值，请将其删除。

## <a name="see-also"></a>请参阅

- [Windows 窗体中的自动缩放](/dotnet/framework/winforms/automatic-scaling-in-windows-forms)
