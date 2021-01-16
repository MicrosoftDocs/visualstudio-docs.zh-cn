---
title: 演练：发布 Visual Studio 扩展 |Microsoft Docs
description: 了解如何将 Visual Studio 扩展发布到 Visual Studio Marketplace，这允许开发人员浏览新扩展和已更新的扩展。
ms.custom: SEO-VS-2020
ms.date: 01/15/2021
ms.topic: how-to
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01a46f54bfbce6126c16fa418d5c4bef53afd09b
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533889"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>演练：发布 Visual Studio 扩展

本演练演示如何将 Visual Studio 扩展发布到 Visual Studio Marketplace。 将扩展添加到 Visual Studio Marketplace 时，开发人员可以使用 **扩展和更新** 来浏览新的和已更新的扩展。

## <a name="prerequisites"></a>先决条件

 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅 [安装 Visual STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-a-visual-studio-extension"></a>创建 Visual Studio 扩展

本文使用默认的 VSPackage 扩展，但这些步骤对每种类型的扩展都有效。

- 在名为的 c # 中创建一个 `TestPublish` 具有菜单命令的 VSPackage。 有关详细信息，请参阅 [创建第一个扩展： Hello World](../extensibility/extensibility-hello-world.md)。

## <a name="package-your-extension"></a>打包扩展

1. 将 *source.extension.vsixmanifest* 更新为有关产品名称、作者和版本的正确信息。

   ![更新扩展 source.extension.vsixmanifest](media/update-extension-vsixmanifest.png)

2. 在 **发布** 模式下构建扩展。 现在，你的扩展会打包为 \bin\Release 文件夹中的一个 VSIX。

3. 可以双击 VSIX 来验证安装。

## <a name="test-the-extension"></a>测试扩展

 在分发扩展之前，对其进行生成和测试，以确保它已正确安装在 Visual Studio 的实验实例中。

1. 在 Visual Studio 中，启动调试以打开 Visual Studio 的实验实例。

2. 在实验实例中，请单击 " **工具** " 菜单，然后单击 " **扩展和更新**"。 TestPublish 扩展应显示在中心窗格中并启用。

3. 在 " **工具** " 菜单上，确保看到 "测试" 命令。

## <a name="publish-the-extension-to-visual-studio-marketplace"></a>将扩展发布到 Visual Studio Marketplace

1. 请确保已生成扩展的发行版，并且该版本是最新版本。

2. 在 web 浏览器中转到 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)。

3. 在右上角，单击 " **登录**"。

4. 使用您的 Microsoft 帐户登录。 如果没有 Microsoft 帐户，此时可以创建一个。

5. 单击 " **发布扩展**"。 此选项将导航到所有扩展的 "管理" 页。 如果没有发布服务器帐户，此时系统会提示你创建一个。

   ![上传到 Marketplace](media/upload-to-marketplace.png)

6. 选择要用于上传扩展的发布者。 可以通过单击左侧列出的发布者名称来更改发布者。 单击 " **新建扩展** "，然后选择 " **Visual Studio**"。

7. 在 **1：上传扩展** 中，你可以选择将 VSIX 文件直接上载到 Visual Studio Marketplace 或只是将链接添加到你自己的网站。 在此示例中，将上传 *TestPublish* 扩展名。 拖放扩展，或使用 **单击** 链接浏览文件。 在项目的 \bin\Release 文件夹中查找扩展。  单击“继续” 。

8. 在 **2：提供扩展详细信息** 时，某些字段是从你的扩展中的 *source.extension.vsixmanifest* 文件自动填充的。 查找以下各项的更多详细信息：

    * **内部名称** 用于扩展的详细信息页的 URL。 例如，在发布服务器名称为 "myname" 的情况下发布一个扩展，并将内部名称指定为 "my extension" 会生成一个 URL，其中 "visualstudio \. com/items = myname" 用于扩展的详细信息页。

    * **显示** 扩展的名称。 此名称是从 *source.extension.vsixmanifest* 文件自动填充的。

    * 要上载的扩展的 **版本号**。 此版本是从 *source.extension.vsixmanifest* 文件自动填充的。

    * **VSIX ID** 是 Visual Studio 用于扩展的唯一标识符。 如果希望自动更新扩展，则需要此标识符。 此标识符是从 *source.extension.vsixmanifest* 文件自动填充的。

    * 用于扩展的 **徽标**。 如果提供了 *source.extension.vsixmanifest* 文件，则会自动填充此徽标。

    * 扩展功能的 **简短说明**。 此说明是从 *source.extension.vsixmanifest* 文件自动填充的。

    * **概述** 非常适合提供屏幕截图以及有关扩展功能的详细信息。

    * **支持的 Visual studio 版本** 允许选择你的扩展将使用的 visual studio 版本。 你的扩展仅安装到这些版本。

    * **支持的 Visual studio 版本** 允许选择你的扩展将使用的 visual studio 版本。 你的扩展仅安装到这些版本。

    * **Type**。 最常见的扩展类型是 **工具**。

    * **类别**。 最多可选择三个最适合你的扩展。

    * **标记** 是帮助用户找到你的扩展的关键字。 标记有助于增加 Visual Studio Marketplace 中的扩展的搜索相关性。

    * **定价类别** 是扩展的费用。

    * **源代码存储库** 允许你使用社区共享到你的源代码的链接。

    * **允许使用 Q&扩展，** 使用户可以在扩展条目页面上提出问题。

9. 单击 " **保存 & 上传**"。 使用此选项可以返回到发布者管理页面。 尚未发布你的扩展。

10. 若要发布扩展，请右键单击扩展，然后选择 " **设为公共**"。 若要查看扩展在 Visual Studio Marketplace 中的显示方式，请选择 " **查看扩展**"。 对于购置号，请单击 " **报表**"。 若要更改扩展，请单击 " **编辑**"。

    ![扩展条目菜单](media/extension-entry-menu.png)

11. 单击 " **公开**"，你的扩展现在是公共的。 搜索扩展的 Visual Studio Marketplace。

## <a name="update-a-published-extension-in-visual-studio-marketplace"></a>在 Visual Studio Marketplace 中更新已发布的扩展

在开始之前，请确保已生成新的扩展版本，并确保其处于最新状态。

1.  在 web 浏览器中转到 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)。

1.  在右上角，单击 " **登录**"，然后用 Microsoft 帐户登录。

    :::image type="content" source="media/marketplace-upload-extension.png" alt-text="显示在文件资源管理器中选择上载的扩展文件的屏幕截图。":::

1.  单击 " **发布扩展**"，然后选择要用于上传更新的扩展的发布服务器。

    :::image type="content" source="media/marketplace-select-extension-version.png" alt-text="突出显示 &quot;发布扩展&quot; 链接的 Visual Studio Marketplace 屏幕截图。":::

1.  在要更新的扩展旁边，将鼠标悬停在三个水平点上，然后选择 " **编辑**"。

    :::image type="content" source="media/marketplace-select-extension.png" alt-text="显示选择要编辑的扩展的屏幕截图。":::

1.  在 **1：上传扩展** 中，在 VSIX 文件名之后，单击铅笔图标以编辑已发布的扩展。

     :::image type="content" source="media/marketplace-edit-extension-details.png" alt-text="显示单击铅笔图标以编辑扩展的屏幕截图。":::

1.  浏览到已更新的扩展 VSIX 文件。 单击该文件，然后单击 " **打开**"。

    更新的扩展上传。

    :::image type="content" source="media/marketplace-upload-extension-notification.png" alt-text="上载已编辑的扩展后上传文件通知的屏幕截图。":::

1. 在 **2：提供扩展详细信息** 时，某些详细信息对于扩展更新是只读的，或者是通过扩展中的 *source.extension.vsixmanifest* 文件自动填充的。 下面是有关扩展详细信息的详细信息：

    - **内部名称** \*用于扩展的详细信息页的 URL。 例如，在发布服务器名称为 "myname" 的情况下发布一个扩展，并将内部名称指定为 "my extension"，会生成一个 URL "marketplace.visualstudio.com/items?itemName=myname.myextension" 作为扩展的详细信息页。

    - **显示名称** \*扩展。 此名称是从 *source.extension.vsixmanifest* 文件自动填充的。

    - **版本** \*要上载的扩展的编号。 此版本是从 *source.extension.vsixmanifest* 文件自动填充的。

    - **VSIX ID** \*是 Visual Studio 用于扩展的唯一标识符。 如果希望自动更新扩展，则需要此标识符。 此标识符是从 *source.extension.vsixmanifest* 文件自动填充的。

    - **徽标** \*用于扩展的。 如果提供了 *source.extension.vsixmanifest* 文件，则会自动填充此徽标。

    - **简短说明** \*扩展的用途。 此说明是从 *source.extension.vsixmanifest* 文件自动填充的。

    - **概述** 非常适合提供屏幕截图以及有关扩展功能的详细信息。

    - **受支持的 Visual Studio 版本** \*允许您选择扩展将使用的 Visual Studio 版本。 你的扩展仅安装到这些版本。

    - **支持的 Visual Studio 版本** \*允许您选择扩展将使用的 Visual Studio 版本。 你的扩展仅在这些版本上安装。

    - **Type**。 最常见的扩展类型是 **工具**。

    - **类别**。 最多可选择三个最适合你的扩展。

    - **标记** 是帮助用户找到你的扩展的关键字。 标记有助于增加 Visual Studio Marketplace 中的扩展的搜索相关性。

    - **定价类别** 是扩展的费用。

    - **源代码存储库** 允许你使用社区共享到你的源代码的链接。

    - **允许使用 Q&扩展，** 使用户可以在扩展条目页面上提出问题。

       \* 此详细信息无法更改扩展更新。

1. 单击 " **保存 & 上传**"。 使用此选项可以返回到发布者管理页面。 尚未发布你的扩展。

1. 若要发布扩展，请右键单击你的扩展，然后选择 " **设为公共**"。 若要查看扩展在 Visual Studio Marketplace 中的显示方式，请选择 " **查看扩展**"。 对于购置号，请单击 " **报表**"。 若要更改扩展，请单击 " **编辑**"。

## <a name="add-additional-users-to-manage-your-publisher-account"></a>添加其他用户来管理你的发布者帐户

Visual Studio Marketplace 支持向其他用户授予访问和管理发布者帐户的权限。

1. 导航到要向其添加其他用户的发布者帐户。

2. 选择 " **成员** "，然后单击 " **添加**"。

   ![添加其他用户](media/add-users.png)

3. 然后，你可以指定要添加的用户的电子邮件地址，并在 " **选择角色**" 下授予正确的访问级别。  可从以下选项中进行选择：

   * **Creator**：用户可以发布扩展，但不能查看或管理由其他用户发布的扩展。

   * **读者**：用户可以查看扩展，但不能发布或管理扩展。

   * **参与者**：用户可以发布和管理扩展，但无法编辑发布服务器设置或管理访问权限。

   * **所有者**：用户可以发布和管理扩展，编辑发布服务器设置，并管理访问权限。

## <a name="install-the-extension-from-visual-studio-marketplace"></a>从 Visual Studio Marketplace 安装扩展

扩展已发布后，请在 Visual Studio 中进行安装，并在其中进行测试。

1. 在 Visual Studio 的 " **工具** " 菜单上，单击 " **扩展和更新**"。

2. 单击 " **联机** "，然后搜索 " **TestPublish**"。

3. 单击“下载”。 然后计划安装该扩展。

4. 若要完成安装，请关闭 Visual Studio 的所有实例。

## <a name="remove-the-extension"></a>删除扩展

可以从 Visual Studio Marketplace 和计算机中删除该扩展。

### <a name="to-remove-the-extension-from-visual-studio-marketplace"></a>删除 Visual Studio Marketplace 的扩展

1. 请参阅 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)。

2. 在右上角，单击 " **发布** 扩展"。 选择发布 **TestPublish** 时所用的发布服务器。 此时将显示 **TestPublish** 的列表。

3. 右键单击该扩展条目，然后单击 " **删除**"。 系统会要求确认是否要删除该扩展。 单击 **“确定”** 。

### <a name="to-remove-the-extension-from-your-computer"></a>从计算机中删除扩展

1. 在 Visual Studio 的 " **工具** " 菜单上，单击 " **扩展和更新**"。

2. 选择 " **TestPublish** "，然后单击 " **卸载**"。 然后，将该扩展计划为卸载。

3. 若要完成卸载，请关闭 Visual Studio 的所有实例。
