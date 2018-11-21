---
title: "综述：在Visual Studio中报告问题"
description: "Provides an overview of the Report a Problem tool, and includes problem states and definitions"
ms.date: 11/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
author: seaniyer
ms.author: seiyer
manager: douge
ms.workload:
  - "multiple"
---
# 综述：报告问题

报告问题工具使Visual Studio开发者社区可以提交问题。你报告的每个问题都变成我们工程师团队的核心工作项，使你能参与帮助我们产品团队识别和解决有影响力的问题。提交丰富诊断信息的反馈对改善Visual Studio产品系列至关重要。我们感谢您花时间报告问题。

另外，您可以对其他社区成员的反馈进行投票，以便更多地关注问题并帮助您更快地解决问题。

## 问题状态

在你报告问题之后，报告问题的生命周期通过状态表明。当微软团队检查你的反馈时，他们将会设置一个适当的状态。通过参考下面列出的状态来跟踪问题报告的进度，以及它们的含义和颜色标志。

![开发者社区中所报告问题新提交状态](../ide/media/ProblemStates/New.jpg)

**New** 表示bug或者问题是最新报告的，并没有采取任何行动。

- - -

![开发者社区中所报告问题正在筛选状态](../ide/media/ProblemStates/Triaged.jpg)

**Triaged** 表示适度的初级步骤，已完成对翻译和内容重复初始检查。你的工单已经发送给适当的工程师团队审议。

- - -

![开发者社区中所报告问题正在考虑状态](../ide/media/ProblemStates/UnderConsideration.jpg)

**Under Consideration** 表明微软正在审阅你的问题在社区造成的影响并将会给出相应的优先级。如果在社区造成的影响还不明显和显著，我们将会继续监视这种状态下的问题。

- - -

![开发者社区中所报告问题正在调查状态](../ide/media/ProblemStates/UnderInvestigation.jpg)

**Under Investigation** 表明工程师们正在积极调查你的问题，以找到解决方案。

- - -

![开发者社区中所报告问题需要更多信息状态](../ide/media/ProblemStates/NeedMoreInfo.jpg)

**Need More Info** 表明我们需要你提供更多诊断信息使我们继续完成调查。  [学习如何回复需要更多信息请求。](./how-to-report-a-problem-with-visual-studio-2017.md#when-further-information-is-needed-need-more-info)

- - -

![已修复 - 开发者社区中所报告问题待发布状态](../ide/media/ProblemStates/FixedPendingRelease.jpg)

**Fixed - Pending Release** 表面我们针对该问题已经有了一个修复，该修复将进入预览版或者正式版。当该修复进入预览版，问题将在预览版中被标记为'fixed in'标签。

- - -

![已关闭 - 开发者社区中所报告问题已修复状态](../ide/media/ProblemStates/ClosedFixed.jpg) 

**Closed - Fixed** 表明针对该问题将发布一个修复。该问题现在在正式版中同样被标记为"fixed in:"。

- - -

![已关闭 - 开发者社区中所报告问题重复状态](../ide/media/ProblemStates/ClosedDuplicate.jpg)

**Closed - Duplicate** 表面你的问题已通过另一个反馈报告给我们。我们将给你原始报告的链接。

- - -

![已关闭 - 开发者社区中所报告问题次低优先级状态](../ide/media/ProblemStates/ClosedLowerPriority.jpg)

**Closed - Lower Priority** 专注让每一个人加入开发者社区，获得最大价值，我们优先考虑对客户造成最大影响的问题。虽然我们不能立刻处理这个特别的问题，请放心你的所有反馈都很有价值，并有助于改善Visual Studio。

- - -

![已关闭 - 开发者社区中所报告问题不是Bug状态](../ide/media/ProblemStates/ClosedNotaBug.jpg)

**Closed - Not a Bug**  表面我们已经确定所报告的功能是当前设计的。

- - -

![已关闭 - 开发者社区中所报告问题没有足够的信息](../ide/media/ProblemStates/ClosedNotEnoughInfo.jpg)

**Closed - Not Enough Info** 表明我们对于你所报告的问题缺乏足够的信息去进行调查。我们很乐意在得到充足的信息后重新考虑。

- - -

![已关闭 - 开发者社区中所报告问题另一个产品状态](../ide/media/ProblemStates/ClosedOtherProduct.jpg)

**Closed - Other Product** 表明我们决定将你的问题应用到另一个产品。请参阅微软对哪个外部产品和任何相关链接的评论。

- - -

![已关闭 - 开发者社区中所报告问题没有修复状态](../ide/media/ProblemStates/ClosedWontFix.jpg)

**Closed - Won't Fix** 表明由于缺乏产品方向一致性或社区影响等问题，我们没有继续研究这个问题。请参阅提交的微软任何附加条款。虽然我们无法解决这个特别的问题，请放心你的所有反馈都很有价值，并有助于改善Visual Studio。

- - -

## FAQ

### 我如何快速增加解决问题的机会？

我们建议使用搜索来确保您将要报告的问题还没有被报告。如果您发现现有项目符合您的问题，关注并对该问题工单进行投票。

提供您可以提供的所有信息，以帮助我们的团队重现您所遇到的问题。此信息包括必要的重复步骤，代码片段，屏幕截图，重现记录，日志文件和其他工件。这是[如何在Visual Studio中提交一个问题](./how-to-report-a-problem-with-visual-studio-2017.md).

### 如何才能优先考虑我的反馈?

我们从客户那里收到了大量有价值的问题。确保我们为开发人员社区中的每个人带来最大价值，我们优先考虑对社区影响最大的反馈采取行动。

如果我们无法亲自回复您的反馈，我们非常感谢您的意见。请放心，您的所有反馈都会传达给合适的团队。

我们非常重视您在Visual Studio中所投入的时间。

### What actions can I take if I'm not satisfied with the resolution?

Our teams do their best to diagnose and fix any issues you experience, however there may be times when you're not fully satisfied with our recommendation. Comment back on the feedback and let us know exactly what you're not satisfied with, and we'll try our best to ensure that we meet your needs.

### How will I get notified of progress on my feedback?

Microsoft engineering teams will communicate with you by commenting on the feedback ticket and changing the state of your ticket as they make progress. Watch for e-mail notifications that are sent when  ticket state changes or a comment is posted.  You can manage frequency of notifications in Profile and Preferences settings on Developer Community site.

### Why can't I add a problem for Visual Studio IDE on the Developer Community website?

Reporting a problem through Visual Studio allows for diagnostic information to automatically be included in the report. It's essential information that gives our engineers the context they need to fully understand your issue and work to resolve it.

When you report through Visual Studio, you can easily share rich diagnostic information with us, such as large log files, crash information, screenshots, repro recording, and other artifacts that help us deliver higher-quality resolutions faster to you.