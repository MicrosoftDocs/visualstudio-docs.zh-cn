---
title: CvWriteAlert 函数 | Microsoft Docs
description: 请参阅并发可视化工具 SDK 函数 CvWriteAlert（C 库）的参考信息。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvWriteAlertVA
- cvmarkers/CvWriteAlertVW
- cvmarkers/CvWriteAlertA
- cvmarkers/CvWriteAlertW
helpviewer_keywords:
- CvWriteAlertVW method
- CvWriteAlertA method
- CvWriteAlertVA method
- CvWriteAlertW method
ms.assetid: 937aa9d6-278a-4df3-bef7-151441df16d5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb2cc6f7408fc5d9af0215dbccf166477876ac23
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686436"
---
# <a name="cvwritealert-function"></a>CvWriteAlert 函数
向并发可视化工具跟踪文件写入一个警报。

## <a name="syntax"></a>语法

```C
HRESULT CvWriteAlertW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCWSTR pMessage,
    ...
    );

HRESULT CvWriteAlertA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCSTR pMessage,
    ...
    );

HRESULT CvWriteAlertVW(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCWSTR pMessage,
    _In_ va_list argList);

HRESULT CvWriteAlertVA(
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,
    _In_ PCSTR pMessage,
    _In_ va_list argList);
```

#### <a name="parameters"></a>参数
 `argList` 参数列表。

 `pMarkerSeries` 有效标记系列上下文。 不能为 NULL。

 `pMessage` 消息格式字符串。 不能为 NULL。

## <a name="return-value"></a>返回值
 成功写入消息时返回 S_OK。 出现任何错误时返回错误代码。 使用 SUCCEEDED/FAILED 宏检查错误条件。

## <a name="requirements"></a>要求
 **Header:** cvmarkers.h

 **Unicode：** CvWriteAlertW、CvWriteAlertVW

 **ANSI：** CvWriteAlertA、CvWriteAlertVA

## <a name="see-also"></a>另请参阅
- [C++ 库参考](../profiling/cpp-library-reference.md)