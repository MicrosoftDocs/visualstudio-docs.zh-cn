---
description: 显示允许用户选择端口的指定对话框。
title: IDebugPortPicker：:D isplayPortPicker |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a49c1379d2bb3946f75eddd9d80bdccdb370d3ab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072307"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
显示允许用户选择端口的指定对话框。

## <a name="syntax"></a>语法

```cpp
HRESULT DisplayPortPicker(
   HWND hwndParentDialog,
   BSTR* pbstrPortId
);
```

```csharp
public int DisplayPortPicker(
   int hwndParentDialog,
   out string pbstrPortId
);
```

## <a name="parameters"></a>参数
`hwndParentDialog`\
中父对话框的句柄。

`pbstrPortId`\
弄端口标识符字符串。

## <a name="return-value"></a>返回值
 如果成功， `S_OK` 则返回; 否则返回错误代码。 返回值为 `S_FALSE` (或返回值，其 `S_OK` `BSTR` 设置为 `NULL`) 指示用户单击了 " **取消**"。

## <a name="see-also"></a>另请参阅
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
