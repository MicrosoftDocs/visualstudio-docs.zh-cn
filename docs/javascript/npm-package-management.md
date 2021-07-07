---
title: 管理 npm 包
description: Visual Studio 可帮助你使用 Node.js 包管理器 (npm) 来管理包
ms.custom: seodec18
ms.date: 02/23/2021
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 2fcf1bd9e9ef5c3ff0663cf12684e6e638d1e5e4
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729281"
---
# <a name="manage-npm-packages-in-visual-studio"></a>在 Visual Studio 中管理 npm 包

可以使用 npm 来安装和管理要在 Node.js 应用程序中使用的包。 使用 Visual Studio 可轻松地通过 UI 或直接与 npm 交互并发出 npm 命令。 如果不熟悉 npm 并想要详细了解，请转到 [npm 文档](https://docs.npmjs.com/)。

Visual Studio 与 npm 的集成因项目类型而异。
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [打开文件夹 (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> npm 在项目根目录中需要 node_modules 文件夹和 package.json   。 如果应用的文件夹结构不同，并且希望使用 Visual Studio 来管理 npm 包，则可以修改文件夹结构。

## <a name="nodejs-projects"></a>Node.js 项目

对于 Node.js 项目，可以执行下列任务：
* [从解决方案资源管理器安装包](#npmInstallWindow)
* [从解决方案资源管理器管理安装的包](#solutionExplorer)
* [在 Node.js 交互式窗口中使用 `.npm` 命令](#interactive)

这些功能协同工作，并与项目系统和项目中的 package.json  文件同步。

### <a name="prerequisites"></a>先决条件

需要安装“Node.js 开发”工作负载和 Node.js 运行时，以便将 npm 支持添加到项目  。 有关详细步骤，请参阅[创建 Node.js 项目](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json)。

> [!NOTE]
> 对于现有的 Node.js 项目，请使用“基于现有 Node.js 代码”解决方案模板或 [Open folder (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md) 项目类型来在项目中启用 npm  。

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a>从解决方案资源管理器安装包 (Node.js)

对于 Node.js 项目，安装 npm 包的最简单方法是通过 npm 包安装窗口。 若要访问此窗口，右键单击项目中的“npm”节点并选择“安装新的 npm 包”   。

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="从解决方案资源管理器安装新的 npm 包" border="true":::

在此窗口中可以搜索包、指定选项并安装。

![“安装新 npm 包”对话框的屏幕截图。 已选择 azure 2.2.1-preview 包，并显示了该包的详细信息和选项。](../javascript/media/search-package.png)

* 依赖项类型 - 在“标准”、“开发”和“可选”包间进行选择     。 “标准”指定包是一个运行时依赖项，而“开发”指定只在开发过程中需要包。
* **添加到 package.json** - 建议。 此可配置选项已被弃用。
* 所选版本  - 选择你想要安装的包版本。
* 其他 npm 参数  - 指定其他标准参数。 例如，可以输入版本值（如 `@~0.8`），安装版本列表中不可用的特定版本。

可以在“输出”窗口的 npm 输出中查看安装进度（若要打开此窗口，请依次选择“视图” > “输出”，或按 Ctrl + Alt + O）。 这可能需要一些时间。

![npm 输出](../javascript/media/npm-output.png)

> [!TIP]
> 可以在搜索查询前添加感兴趣的范围，进而搜索范围内的包，例如键入 `@types/mocha` 来查找 mocha 的 TypeScript 定义文件。 此外，安装 TypeScript 的类型定义时，可以在 npm 参数字段中添加 `@ts2.6`，指定要面向的 TypeScript 版本。

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>在解决方案资源管理器中管理安装的包 (Node.js)

npm 包显示在解决方案资源管理器中。 “npm”节点下的条目模拟 package.json 文件中的依赖项   。

![解决方案资源管理器中 npm 节点的屏幕截图，其中显示 npm 包的安装状态。](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>包状态

* ![已安装的包](../javascript/media/installed-npm.png) - 已安装并列在 package.json 中
* ![无关包](../javascript/media/extraneous-npm.png) - 已安装但未显式列在 package.json 中
* ![缺失的包](../javascript/media/missing-npm.png) - 未安装，但列在 package.json 中

::: moniker range=">=vs-2019"
右键单击 npm 节点，执行以下操作之一  ：

* **安装新的 npm 包** 打开 UI 以安装新的包。
* **安装 npm 包** 运行 npm 安装命令以安装 package.json 中列出的所有包  。 （运行 `npm install`。）
* “更新 npm 包”根据 package.json 中指定的语义版本控制 (SemVer) 范围，将包更新到最新版本。 （运行 `npm update --save`。）。 通常使用“~”或“^”指定 SemVer 范围。 有关详细信息，请参阅 [package.json 配置](../javascript/configure-packages-with-package-json.md)。

右键单击包节点，执行以下操作之一：

* **安装 npm 包** 运行 npm 安装命令以安装 package.json 中列出的所有包版本  。 （运行 `npm install`。）
* “更新 npm 包”根据 package.json 中指定的 SemVer 范围，将包更新到最新版本。 （运行 `npm update --save`。）通常使用“~”或“^”指定 SemVer 范围。
* **卸载 npm 包** 卸载包并将其从 package.json 中删除（运行 `npm uninstall --save`。） 
::: moniker-end
::: moniker range="vs-2017"
右键单击包节点或“npm”  节点，执行以下操作之一：
* 安装 package.json 中列出的缺失的包  
* 将 npm 包更新到最新版本 
* 卸载包  ，并从 package.json  中删除
::: moniker-end

>[!NOTE]
> 若要帮助解决 npm 包的问题，请参阅[疑难解答](#troubleshooting-npm-packages)。

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>在 Node.js 交互式窗口中使用 .npm 命令 (Node.js)

还可在 Node.js 交互式窗口中使用 `.npm` 命令来执行 npm 命令。 若要打开此窗口，请在“解决方案资源管理器”中右键单击项目，然后选择“打开 Node.js 交互窗口”（或按 Ctrl + K、N）。

在窗口中，可以使用如下命令来安装包：

`.npm install azure@4.2.3`

 > [!Tip]
 > 默认情况下，npm 将在项目的主目录中执行。 如果解决方案中有多个项目，请在方括号中指定项目的名称或路径。
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > 如果项目不包含 package.json 文件，请使用 `.npm init -y` 创建含默认条目的新 package.json 文件。

 ## <a name="aspnet-core-projects"></a>ASP.NET Core 项目

对于 ASP.NET Core 项目之类的项目，可以在项目中集成 npm 支持，并使用 npm 安装包。
* [向项目添加 npm 支持](#npmAdd)
* [使用 package.json 安装包](#npmInstallPackage)

>[!NOTE]
> 对于 ASP.NET Core 项目，还可以使用[库管理器](/aspnet/core/client-side/libman/?view=aspnetcore-3.1&preserve-view=true)或 yarn（而非 npm）来安装客户端 JavaScript 和 CSS 文件。

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a>向项目添加 npm 支持 (ASP.NET Core)

如果你的项目尚未包含 package.json 文件，则可以为其添加一个 package.json 文件以启用 npm 支持   。

1. 如果你尚未安装 Node.js，建议从 [Node.js](https://nodejs.org/en/download/) 网站安装 LTS 版本，以实现与外部框架和库的最佳兼容性。

   npm 需要 Node.js。

1. 若要添加 package.json 文件，请在“解决方案资源管理器”中右键单击项目，然后依次选择“添加” > “新项”（或按 Ctrl + Shift + A）。 选择“npm 配置文件”，使用默认名称，然后单击“添加”   。

   ![将 package.json 添加到项目](../javascript/media/npm-add-package-json.png)

   如果看不到列出的 npm 配置文件，则没有安装 Node.js 开发工具。 可以使用 Visual Studio 安装程序添加“Node.js 开发”工作负载  。 然后重复执行上一步骤。

1. 在 package.json 的 `dependencies` 或 `devDependencies` 部分中添加一个或多个 npm 包  。 例如，可以向文件添加以下内容：

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

保存文件时，Visual Studio 会将包添加到解决方案资源管理器中的“依赖项/npm”节点下  。 如果未显示该节点，请右键单击“package.json”并选择“还原包”   。

>[!NOTE]
> 在某些情况下，解决方案资源管理器可能无法正确显示已安装 npm 包的状态。 有关详细信息，请参阅[疑难解答](#troubleshooting-npm-packages)。

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>使用 package.json 安装包 (ASP.NET Core)

对于包含 npm 的项目，可以使用 `package.json` 配置 npm 包。 右键单击解决方案资源管理器中的 npm 节点，并选择“打开 package.json”  。

![选中 npm 节点的解决方案资源管理器的屏幕截图。 已打开右键单击上下文菜单，并且已选中“打开 package.json”。](../javascript/media/npm-add-package.png)

package.json 中的 IntelliSense 可帮助选择特定版本的 npm 包  。

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="选择 npm 包版本" border="true":::

保存文件时，Visual Studio 会将包添加到解决方案资源管理器中的“依赖项/npm”节点下  。 如果未显示该节点，请右键单击“package.json”并选择“还原包”   。

安装包可能需要几分钟的时间。 通过在“输出”窗口中切换到“npm”输出来查看包的安装进度   。

![npm 输出](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>npm 包疑难解答

* npm 需要 Node.js。如果你尚未安装 Node.js，建议从 [Node.js](https://nodejs.org/en/download/) 网站安装 LTS 版本，以实现与外部框架和库的最佳兼容性。

* 对于 Node.js 项目，必须为 npm 支持安装“Node.js 开发”工作负载  。

* 在某些情况下，由于[此处](https://github.com/aspnet/Tooling/issues/479)所述的已知问题，解决方案资源管理器可能无法正确显示已安装 npm 包的状态。 例如，在安装包时，可能会显示为未安装。 在大多数情况下，可以通过删除 package.json，重启 Visual Studio 并重新添加 package.json 文件来更新解决方案资源管理器，如本文前面所述   。 也可在安装包时使用“npm 输出”窗口来验证安装状态。

* 在某些 ASP.NET Core 方案中，在生成项目后，解决方案资源管理器中的 npm 节点可能不可见。 若要使节点再次可见，请右键单击项目节点，然后选择“卸载项目”。 然后，右键单击项目节点，并选择“重新加载项目”。

* 如果在生成应用或转译 TypeScript 代码时看到任何错误，请检查 npm 包是否由于潜在错误源而不兼容。 若要帮助识别错误，请在安装包时检查“npm 输出”窗口，如本文前面所述。 例如，如果所使用的一个或多个 npm 包版本是已弃用的版本，并导致发生错误，则可能需要安装较新版本以消除错误。 有关使用 package.json  控制 npm 包版本的信息，请参阅 [package.json 配置](../javascript/configure-packages-with-package-json.md)。
