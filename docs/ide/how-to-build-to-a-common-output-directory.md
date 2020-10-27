---
title: 如何：生成到公共输出目录
description: 了解如何通过更改项目的生成输出路径来强制将所有输出都放到相同的文件夹中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a39dae210c2cb9afe3e4b77962b75ddb3be4baeb
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136961"
---
# <a name="how-to-build-to-a-common-output-directory"></a>如何：生成到公共输出目录

默认情况下，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 将解决方案中的每个项目生成到其在解决方案中自己的文件夹中。 可以通过更改项目的生成输出路径来强制将所有输出都放到相同的文件夹中。

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>将所有解决方案输出都放到一个共同目录中

1. 单击解决方案中的项目。

2. 在 **“项目”** 菜单上，单击 **“属性”** 。

3. 根据项目的类型，单击“编译”选项卡或“生成”选项卡，并将“输出路径”设置为适用于解决方案中所有项目的文件夹  。

4. 为解决方案中的所有项目重复 1-3 步骤。

## <a name="see-also"></a>另请参阅

- [编译和生成](../ide/compiling-and-building-in-visual-studio.md)
- [如何：更改生成输出目录](../ide/how-to-change-the-build-output-directory.md)