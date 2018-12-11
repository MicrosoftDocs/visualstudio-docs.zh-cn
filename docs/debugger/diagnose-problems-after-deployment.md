---
title: 在部署后诊断问题 |Microsoft Docs
ms.custom: ''
ms.date: 04/10/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a3463eab-a352-4d17-8551-adbaad526db0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b10635c1aefedf7af83a1c884717b80b442e8998
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219908"
---
# <a name="diagnose-problems-after-deployment-using-intellitrace"></a>使用 IntelliTrace 在部署后诊断问题

要在使用 IntelliTrace 部署后诊断 ASP.NET Web 应用中的问题，请加入发行版本信息，以便 Visual Studio 自动查找调试 IntelliTrace 日志所需的正确源文件及符号文件。

 如果正使用 Microsoft Monitoring Agent 控制 IntelliTrace，则你还需在 Web 服务器上设置应用程序性能监视。 这将在应用运行时记录诊断事件，并将这些事件保存到 IntelliTrace 日志文件。 然后你可以在 Visual Studio 企业版（但不是 专业版 或 社区版）中查看事件，转到发生事件的代码，查看在该时间点记录的值，然后在已运行的代码中向前或向后移动。 在找到并解决问题后，重复生成、发布和监控发布这一循环，以便可以更早更快地解决将来的潜在问题。

 ![代码、 生成、 发布、 监视、 诊断和修复](../debugger/media/ffr_cycle.png "FFR_Cycle")

 **你将需要：**

-   Visual Studio、 Azure DevOps 或 Team Foundation Server 2017、 2015年、 2013年、 2012年或 2010 来设置您的生成

-   用于监视应用和记录诊断数据的 Microsoft Monitoring Agent

-   用于查看诊断数据并使用 IntelliTrace 调试代码的 Visual Studio 企业版（但不是 专业版 或 社区版）

##  <a name="SetUpBuild"></a> 步骤 1： 包含发布的生成信息
 设置你的生成过程以创建生成清单 (*BuildInfo.config*文件) 的 web 项目，并包含在发布此清单。 此清单包含有关项目、源代码管理和用于创建特定生成的生成系统的信息。 在你打开 IntelliTrace 日志以查看记录的事件时，此信息可帮助 Visual Studio 查找匹配的源和符号。

###  <a name="AutomatedBuild"></a> 创建使用 Team Foundation Server 自动生成的生成清单

 无论你使用 Team Foundation 版本控制还是 Git，请按照这些步骤进行操作。

####  <a name="TFS2017"></a> Azure DevOps 和 Team Foundation Server 2017

Visual Studio 2017 不包括*BuildInfo.config*文件，它已不推荐使用，之后将被删除。 若要在部署后调试 ASP.NET web 应用程序，请使用以下方法之一：

* 对于部署到 Azure，请使用[Application Insights](https://docs.microsoft.com/azure/application-insights/)。

* 如果需要使用 IntelliTrace，在 Visual Studio 中打开项目，并在匹配后加载符号文件。 您可以从**模块**窗口中或通过 **工具** > **选项** > **调试**  > **符号** 配置中的符号，加载符号文件。


####  <a name="TFS2013"></a> Team Foundation Server 2013
 设置生成管道以将源代码、 生成的文件和符号文件的位置添加到生成清单 （BuildInfo.config 文件）。 Team Foundation Build 自动创建此文件并将其放置在项目的输出文件夹中。

1.  [编辑生成管道或创建新的生成管道。](/azure/devops/pipelines/get-started-designer?view=vsts)

     ![查看在 TFS 2013 中的生成管道](../debugger/media/ffr_tfs2013viewbuilddefinition.png "FFR_TFS2013ViewBuildDefinition")

2.  选择默认模板 (TfvcTemplate.12.xaml) 或自己的自定义模板。

     ![选择生成过程模板&#45;TFS 2013](../debugger/media/ffr_tfs2013buildprocesstemplate.png "FFR_TFS2013BuildProcessTemplate")

3.  指定保存符号 (PDB) 文件的位置，以便自动为你的源编制索引。

     如果使用自定义模板，请确保该模板具有用于为源编制索引的活动。 之后你将添加 MSBuild 参数以指定保存符号文件的位置。

     ![设置符号路径中生成管道 TFS 2013](../debugger/media/ffr_tfs2013builddefsymbolspath.png "FFR_TFS2013BuildDefSymbolsPath")

     有关符号的详细信息，请参阅 [发布符号数据](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols?view=vsts)。

4.  在生成清单文件中添加此 MSBuild 参数以包含 TFS 和符号位置：

     **/p:IncludeServerNameInBuildInfo = true**

     任何可访问你的 Web 服务器的人都可以在生成清单中看见这些位置。 请确保你的源服务器是安全的。

5.  如果使用自定义模板，请添加此 MSBuild 参数，以指定保存符号文件的位置：

     **/p: buildsymbolstorepath =**\<*符号的路径*>

     ![在生成定义 TFS 2013 中包括生成服务器信息](../debugger/media/ffr_tfs2013builddefincludeserverinfo.png "FFR_TFS2013BuildDefIncludeServerInfo")

     将这些行添加到你的 Web 项目文件（.csproj、.vbproj）中：

    ```xml
    <!-- Import the targets file. Change the folder location as necessary. -->
       <Import Project=""$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\BuildInfo\Microsoft.VisualStudio.ReleaseManagement.BuildInfo.targets" />

    ```

     任何可访问你的 Web 服务器的人都可以在生成清单中看见这些位置。 请确保你的源服务器是安全的。

6.  运行新的生成。

    转到[步骤 2： 发布你的应用](#DeployRelease)

####  <a name="TFS2012_2010"></a> Team Foundation Server 2012 或 2010
 若要为项目自动创建生成清单（BuildInfo.config 文件）并将其置于你的项目的输出文件夹中，请执行以下步骤。 此文件在输出文件夹中显示为“*ProjectName*.BuildInfo.config”，但是在你发布应用后将在部署文件夹中重命名为“BuildInfo.config”。

1.  在你的 Team Foundation Build 服务器上安装 Visual Studio 2013（任意版本）。

2.  在生成管道中，指定保存符号，以便您的源自动编制索引的位置。

     如果使用自定义模板，请确保该模板具有用于为源编制索引的活动。

3.  将这些 MSBuild 参数添加到你的生成管道：

    -   **/p:VisualStudioVersion = 12.0**

    -   **/p:MSBuildAssemblyVersion = 12.0**

    -   **/tv:12.0**

    -   **/p:IncludeServerNameInBuildInfo = true**

    -   **/p: buildsymbolstorepath =**\<*符号的路径*>

4.  运行新的生成。

    转到[步骤 2： 发布你的应用](#DeployRelease)

###  <a name="ManualBuild"></a> 手动创建使用 Visual Studio 的生成清单
 若要为项目自动创建生成清单（BuildInfo.config 文件）并将其置于你的项目的输出文件夹中，请执行以下步骤。 此文件在输出文件夹中显示为“*ProjectName*.BuildInfo.config”，但是在你发布应用后将在部署文件夹中重命名为“BuildInfo.config”。

1.  在“解决方案资源管理器” 中，卸载 Web 项目。

2.  打开项目文件（.csproj、.vbproj）。 添加这些行：

    ```xml
    <!-- **************************************************** -->
    <!-- Build info -->
    <PropertyGroup>
       <!-- Generate the BuildInfo.config file -->
       <GenerateBuildInfoConfigFile>True</GenerateBuildInfoConfigFile>
       <!-- Include server name in build info -->
       <IncludeServerNameInBuildInfo>True</IncludeServerNameInBuildInfo>
       <!-- Include the symbols path so Visual Studio can find the matching deployed code when you start debugging. -->
       <BuildSymbolStorePath><path to symbols></BuildSymbolStorePath>
    </PropertyGroup>
    <!-- **************************************************** -->
    ```

3.  签入更新的项目文件。

4.  运行新的生成。

    转到[步骤 2： 发布你的应用](#DeployRelease)

###  <a name="MSBuild"></a> 手动创建使用 MSBuild.exe 的生成清单
 运行生成时添加这些生成参数：

 **/p:GenerateBuildInfoConfigFile = true**

 **/p:IncludeServerNameInBuildInfo = true**

 **/p: buildsymbolstorepath =**\<*符号的路径*>

##  <a name="DeployRelease"></a> 步骤 2： 发布你的应用
 如果使用生成过程创建的 [Web.Deploy 包](https://msdn.microsoft.com/library/dd394698.aspx) 来部署你的应用，则生成清单从“*ProjectName*.BuildInfo.config”自动重命名为“BuildInfo.config”，并在 Web 服务器上与应用的 Web.config 文件一起放在相同的文件夹中。

 如果你使用其他方法部署应用，请确保生成清单从“*ProjectName*.BuildInfo.config”重命名为“BuildInfo.config”，并且在 Web 服务器上与应用的 Web.config 文件一起放在相同的文件夹中。

## <a name="step-3-monitor-your-app"></a>步骤 3：监视你的应用
 在 Web 服务器上设置应用程序性能监视，以便可以监视应用程序中的问题、记录诊断事件并将这些事件保存到 IntelliTrace 日志文件中。 请参阅 [监视你的发布的部署问题](../debugger/using-the-intellitrace-stand-alone-collector.md)。

##  <a name="InvestigateEvents"></a> 步骤 4： 找出问题
 你的开发计算机或另一台计算机上需要使用 Visual Studio 企业版，以查看记录的事件并使用 IntelliTrace 调试代码。 你还可以使用诸如 CodeLens、调试器映射和代码映射等工具帮助你诊断问题。

### <a name="open-the-intellitrace-log-and-matching-solution"></a>打开 IntelliTrace 日志和匹配的解决方案

1.  从 Visual Studio 企业版中打开 IntelliTrace 日志（.iTrace 文件）。 或者，如果在同一台计算机上装有 Visual Studio 企业版，则只需双击该文件。

2.  如果该项目没有作为解决方案的一部分而生成，请选择“打开解决方案”  以让 Visual Studio 自动打开匹配的解决方案或项目。 [问： IntelliTrace 日志缺少有关部署的应用程序的信息。为何发生这种情况？我该怎么办？](#InvalidConfigFile)

     Visual Studio 在打开匹配的解决方案或项目时自动搁置挂起的更改。 若要获取有关搁置集的更多详细信息，请在“输出”  窗口或“团队资源管理器” 中查找。

     在进行任何更改之前，请确认你的源代码正确。 如果你使用分支，你可能在不同于 Visual Studio 找到匹配源的分支中工作，例如你的发布分支。

     ![从 IntelliTrace 日志打开解决方案](../debugger/media/ffr_itsummarypageopensolution.png "FFR_ITSummaryPageOpenSolution")

     如果你有映射到此解决方案或项目的现有工作区，Visual Studio 会选择用于放置找到的源的工作区。

     ![从源代码管理打开到映射的工作区](../debugger/media/ffr_openprojectfromsourcecontrol_mapped.png "FFR_OpenProjectFromSourceControl_Mapped")

     否则，请选择其他工作区或创建新的工作区。 Visual Studio 会将整个分支映射到此工作区。

     ![源代码管理中打开&#45;创建新的工作区](../debugger/media/ffr_openprojectfromsourcecontrol_createnewworkspace.png "FFR_OpenProjectFromSourceControl_CreateNewWorkspace")

     若要创建具有特定映射的工作区或不是计算机名称的名称，请选择“管理” 。

     [问： Visual Studio 为何提示我所选的工作区是不合格？](#IneligibleWorkspace)

     [问： 为什么无法继续之前选择团队集合或不同的集合？](#ChooseTeamProject)

### <a name="diagnose-a-performance-problem"></a>诊断性能问题

1.  在“性能冲突” 下，查看记录的性能事件、其总执行时间以及其他事件信息。 然后，深入查看在特定性能事件期间调用的方法。

     ![查看性能事件详细信息](../debugger/media/ffr_itsummarypageperformance.png "FFR_ITSummaryPagePerformance")

     也可以直接双击事件。

2.  在事件页上，查看这些调用的执行时间。 在执行树中查找缓慢调用。

     当你有多个调用（嵌套调用或其他调用）时，最慢的调用将显示在它们自己的部分中。

     展开调用以查看在该时间点记录的所有嵌套调用和值。 然后，从该调用开始调试。

     ![从方法调用开始调试](../debugger/media/ffr_itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")

     你也可以双击调用。

     如果方法在应用程序代码中，Visual Studio 将转到该方法。

     ![转到应用程序代码在性能事件](../debugger/media/ffr_itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")

     现在你可以查看其他记录的值和调用堆栈、单步执行代码，或者使用“IntelliTrace”  窗口在此性能事件期间调用的 [其他方法之间“及时”前后移动](../debugger/intellitrace.md) 。

    - [所有这些其他事件和 IntelliTrace 日志中的信息是什么？](../debugger/using-saved-intellitrace-data.md)
    - [做些什么可以我在这里？](#WhatElse)
    - [要了解有关性能事件的详细信息？](https://blogs.msdn.microsoft.com/devops/2013/09/20/performance-details-in-intellitrace/)

### <a name="diagnose-an-exception"></a>诊断异常

1.  在“异常数据” 下，查看记录的异常事件，它们的类型、消息以及异常发生的时间。 若要深入查看代码，请从异常组中的最近事件开始调试。

     ![从异常事件开始调试](../debugger/media/ffr_itsummarypageexception.png "FFR_ITSummaryPageException")

     也可以直接双击事件。

     如果应用程序代码发生异常，Visual Studio 将转到发生异常的位置。

     ![转到应用程序代码在异常事件](../debugger/media/ffr_itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")

     现在你可以查看其他记录的值和调用堆栈，或者使用“IntelliTrace”  窗口 [在其他记录的事件、相关代码和在这些时间点记录的值之间“及时”前后移动](../debugger/intellitrace.md)。

     [所有这些其他事件和 IntelliTrace 日志中的信息是什么？](../debugger/using-saved-intellitrace-data.md)

###  <a name="WhatElse"></a> 做些什么可以我在这里？

-   [获取有关此代码的详细信息](../ide/find-code-changes-and-other-history-with-codelens.md)。 若要查找对此代码的引用，其更改历史记录、 相关的 bug、 工作项、 代码审阅或单元测试-全部而无需离开编辑器-使用 CodeLens 指示器在编辑器中。

     ![CodeLens&#45;查看对此代码的引用](../debugger/media/ffr_itsummarypageperformancecodelensreferences.png "FFR_ITSummaryPagePerformanceCodeLensReferences")

     ![CodeLens&#45;查看更改此代码的历史记录](../debugger/media/ffr_itsummarypageperformancecodelensauthors.png "FFR_ITSummaryPagePerformanceCodeLensAuthors")

-   [在进行调试时映射在代码中的位置。](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) 要直观地跟踪在你的调试会话期间调用的方法，请映射调用堆栈。

     ![调试时映射调用堆栈](../debugger/media/ffr_itsummarypageperformancedebuggermap.png "FFR_ITSummaryPagePerformanceDebuggerMap")

###  <a name="FAQ"></a> 问题解答

####  <a name="WhyInclude"></a> 问： 为什么都包含有关我的项目、 源代码管理、 生成和符号与我的发布？
 Visual Studio 使用此信息针对你尝试调试的发布查找匹配的解决方案和源。 在你打开 IntelliTrace 日志并选择要开始调试的事件后，Visual Studio 使用符号查找并向你显示发生事件的代码。 然后你可以查看记录的值，并在代码的执行中向前或向后移动。

 如果你使用 TFS，而且此信息不在生成清单 （BuildInfo.config 文件）、 Visual Studio 查找匹配的源和当前连接的 TFS 上的符号。 如果 Visual Studio 找不到正确的 TFS 或匹配的源，将提示你选择不同的 TFS。

####  <a name="InvalidConfigFile"></a> 问： IntelliTrace 日志缺少有关部署的应用程序的信息。 为何发生这种情况？ 我该怎么办？
 当你从开发计算机部署或在部署期间未连接到 TFS 时，可能发生此情况。

1.  转到项目的部署文件夹。

2.  查找并打开生成清单（BuildInfo.config 文件）。

3.  确保此文件包含必需的信息：

- **ProjectName**

   Visual Studio 中你的项目的名称。 例如：

  ```xml
  <ProjectName>FabrikamFiber.Extranet.Web</ProjectName>
  ```

- **SourceControl**

- 有关你的源代码管理系统以及以下必需属性的信息：

  - **TFS**

    - **ProjectCollectionUri**：用于 Team Foundation Server 和项目集合的 URI

    - **ProjectItemSpec**：应用的项目文件（.csproj 或 .vbproj）的路径

    - **ProjectVersionSpec**：项目的版本

      例如：

    ```xml
    <SourceControl type="TFS">
       <TfsSourceControl>
          <ProjectCollectionUri>http://fabrikamfiber:8080/tfs/FabrikamFiber</ProjectCollectionUri>
          <ProjectItemSpec>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectItemSpec>
          <ProjectVersionSpec>LFabrikamFiber_BuildAndPublish_20130813@$/WorkInProgress</ProjectVersionSpec>
       </TfsSourceControl>
    </SourceControl>
    ```

  - **Git**

    - **GitSourceControl**： **GitSourceControl** 架构的位置

    - **RepositoryUrl**：用于 Team Foundation Server、项目集合和 Git 存储库的 URI

    - **ProjectPath**：应用的项目文件（.csproj 或 .vbproj）的路径

    - **CommitId**：你的提交的 ID

      例如：

    ```xml
    <SourceControl type="Git">
       <GitSourceControl xmlns="http://schemas.microsoft.com/visualstudio/deploymentevent_git/2013/09">
          <RepositoryUrl>http://gittf:8080/tfs/defaultcollection/_git/FabrikamFiber</RepositoryUrl>
          <ProjectPath>/FabrikamFiber.CallCenter/FabrikamFiber.Web/FabrikamFiber.Web.csproj</ProjectPath>
          <CommitId>50662c96502dddaae5cd5ced962d9f14ec5bc64d</CommitId>
       </GitSourceControl>
    </SourceControl>
    ```

- **生成**

   有关生成系统（ `"TeamBuild"` 或 `"MSBuild"`）以及以下所需属性的信息：

  - **BuildLabel** （对于 TeamBuild）：生成名称和号码。 此标签也用作部署事件的名称。 有关生成号的详细信息，请参阅 [使用生成号为已完成的生成提供有意义的名称](/azure/devops/pipelines/build/options?view=vsts)。

  - **SymbolPath** （推荐）：你的符号（PDB 文件）位置的 URI 列表，采用分号分隔。 这些 URI 可以是 URL 或 UNC。 它使 Visual Studio 更易于查找匹配的符号以帮助你进行调试。

  - **BuildReportUrl** （对于 TeamBuild）：TFS 中的生成报告的位置

  - **BuildId** （对于 TeamBuild）：TFS 中生成详细信息的 URI。 此 URI 也用作部署事件的 ID。 如果不使用 TeamBuild，则它必须是唯一的 ID。

  - **BuiltSolution**：Visual Studio 用于查找和打开匹配的解决方案的解决方案文件的路径。 这是 **SolutionPath** MsBuild 属性的内容。

    例如：

  - **TFS**

    ```xml
    <Build type="TeamBuild">
       <MsBuild>
          <BuildLabel kind="label">FabrikamFiber_BuildAndPublish_20130813.1</BuildLabel>
          <SymbolPath>\\fabrikamfiber\FabrikamFiber.CallCenter\Symbols</SymbolPath>
          <BuildReportUrl kind="informative, url" url="http://fabrikamfiber:8080/tfs/FabrikamFiber/_releasePipeline/FindRelease?buildUri=fabrikamfiber%3a%2f%2f%2fBuild%2fBuild%2f448">Build Report Url</BuildReportUrl>
          <BuildId kind="id">1c4444d2-518d-4673-a590-dce2773c7744,fabrikamfiber:///Build/Build/448</BuildId>
          <BuiltSolution>$/WorkInProgress/FabrikamFiber/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>
       </MsBuild>
    </Build>
    ```

  - **Git**

    ```xml
    <Build type="MSBuild">
       <MSBuild>
          <SymbolPath>\\gittf\FabrikamFiber.CallCenter\Symbols</SymbolPath>
          <BuiltSolution>/FabrikamFiber.CallCenter/FabrikamFiber.CallCenter.sln</BuiltSolution>
       </MSBuild>
    </Build>
    ```

####  <a name="IneligibleWorkspace"></a> 问： Visual Studio 为何提示我所选的工作区是不合格？
 **答：** 选中的工作区域没有源代码管理文件夹和本地文件夹之间的任何映射。 若要为此工作区创建映射，请选择“管理” 。 否则，请选择已映射的工作区或创建新的工作区。

 ![没有映射工作区的源代码管理中打开](../debugger/media/ffr_openprojectfromsourcecontrol_notmapped.png "FFR_OpenProjectFromSourceControl_NotMapped")

####  <a name="ChooseTeamProject"></a> 问： 为什么无法继续之前选择团队集合或不同的集合？
 **答：** 这种情况可能是由于以下原因导致的：

-   Visual Studio 未连接到 TFS。

     ![源代码管理中打开&#45;未连接](../debugger/media/ffr_openprojectfromsourcecontrol_notconnected.png "FFR_OpenProjectFromSourceControl_NotConnected")

-   Visual Studio 未在你的当前团队集合中找到解决方案或项目。

     当生成清单文件 (\<*ProjectName*>。BuildInfo.config) 未指定 Visual Studio 可以在何处找到匹配的源时，Visual Studio 将使用当前连接的 TFS 查找匹配的解决方案或项目。 如果当前团队集合没有匹配的源，Visual Studio 将会提示你连接到不同的团队集合。

-   Visual Studio 未找到解决方案或项目中指定生成清单文件的集合 (\<*ProjectName*>。BuildInfo.config)。

     指定的 TFS 可能不再具有匹配的源，甚至不存在（可能是因为你已迁移到新的 TFS）。 如果指定的 TFS 不存在，Visual Studio 在一分钟后可能会超时，然后会提示你连接到不同的集合。 若要继续，请连接到正确的 TFS 服务器。

     ![源代码管理中打开&#45;迁移](../debugger/media/ffr_openprojectfromsourcecontrol_migrated.png "FFR_OpenProjectFromSourceControl_Migrated")

####  <a name="WhatWorkspace"></a> 问： 什么是工作区？
 **答：** 你的 [工作区存储源的副本](/azure/devops/repos/tfvc/create-work-workspaces?view=vsts) ，因此在签入工作之前，你可以对其进行单独开发和测试。 如果尚未具备专门映射到找到的解决方案或项目的工作区，那么 Visual Studio 会提示你选择一个可用的工作区，或以你的计算机名称作为默认工作区名称创建新的工作区。

####  <a name="UntrustedSymbols"></a> 问： 为什么收到有关不受信任的符号的此消息？
 ![使用不受信任的符号路径进行调试？] (../debugger/media/ffr_ituntrustedsymbolpaths.png "FFR_ITUntrustedSymbolPaths")

 **答：** 何时会出现此消息中生成清单文件的符号路径 (\<*ProjectName*>。中的受信任的符号路径列表不包含 BuildInfo.config)。 你可将路径添加到调试器选项中的符号路径列表。
