---
title: DA0501 - 所分析的进程的平均 CPU 使用率。 | Microsoft Docs
description: 此消息报告处理器忙于执行应用程序指令的时间的百分比。
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 242a3ff10042a53997b17f662af145440df2e95a
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465824"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501：所分析的进程的 CPU 平均消耗量。

|项|“值”|
|-|-|
|规则 ID|DA501|
|类别|资源监控|
|分析方法|全部|
|消息|所分析的进程的 CPU 平均消耗量。|
|规则类型|信息|

 使用采样法、.NET 内存或资源争用方法进行分析时，必须收集至少 10 个样本才能触发此规则。

## <a name="rule-description"></a>规则说明
 此消息报告处理器忙于执行应用程序指令的时间的百分比。 报告的值是所分析的进程处于活动状态的所有测量时间间隔的平均值。 具有多个处理器的计算机上的值可能大于 100%。

## <a name="how-to-use-rule-data"></a>如何使用规则数据
 使用规则值比较程序的不同版本或生成的性能，或了解在不同的测试方案中应用程序的性能。
