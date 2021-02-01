---
title: CvLeaveSpan 函数 | Microsoft Docs
description: 请参阅并发可视化工具 SDK 函数 CvLeaveSpan（C 库）的参考信息。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvLeaveSpan
helpviewer_keywords:
- CvLeaveSpan method
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1dcd98a8233f8080d03650c3989805ee9ec7289
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686579"
---
# <a name="cvleavespan-function"></a>CvLeaveSpan 函数
标记范围的结束位置。

## <a name="syntax"></a>语法

```C
HRESULT CvLeaveSpan(
   _In_ PCV_SPAN pSpan
);
```

#### <a name="parameters"></a>参数
 `pSpan` 上一 CvEnterSpan* 调用返回的范围对象。 不能为 NULL。

## <a name="return-value"></a>返回值
 成功写入消息时返回 S_OK。 出现任何错误时返回错误代码。 使用 SUCCEEDED/FAILED 宏检查错误条件。

## <a name="requirements"></a>要求
 **Header:** cvmarkers.h

## <a name="see-also"></a>另请参阅
- [C++ 库参考](../profiling/cpp-library-reference.md)