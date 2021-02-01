---
title: CvCreateMarkerSeries 函数 | Microsoft Docs
description: 请参阅并发可视化工具 SDK 函数 CvCreateMarkerSeries（C 库）的参考信息。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a80d833396644fa6c2a025dc24b6db473b2b393
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686163"
---
# <a name="cvcreatemarkerseries-function"></a>CvCreateMarkerSeries 函数
为给定提供程序创建标记系列。

## <a name="syntax"></a>语法

```C
_Check_return_ HRESULT CvCreateMarkerSeriesW(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCWSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);

_Check_return_ HRESULT CvCreateMarkerSeriesA(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);
```

#### <a name="parameters"></a>参数
 `pProvider` 先前由 CvInitProvider 初始化的提供程序对象。 不能为 NULL。

 `pSeriesName` 标记系列名称。 不能为 NULL，但允许空字符串。

 `ppMarkerSeries` 输出变量的地址，用于存储标记系列上下文。 不能为 NULL。

## <a name="return-value"></a>返回值
 成功创建标记系列时返回 S_OK，出现任何错误时返回错误代码。 使用 SUCCEEDED/FAILED 宏检查错误条件。

## <a name="requirements"></a>要求
 **Header:** cvmarkers.h

 **Unicode：** CvCreateMarkerSeriesW

 **ANSI：** CvCreateMarkerSeriesA

## <a name="see-also"></a>另请参阅
- [C++ 库参考](../profiling/cpp-library-reference.md)