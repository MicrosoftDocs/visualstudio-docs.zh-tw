---
title: 優化選單和工具列指令 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4932a4404c3d76b089468864f84d011524e9cfa0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706911"
---
# <a name="optimizing-menu-and-toolbar-commands"></a>將功能表和工具列命令最佳化
VSPackages 及其相應的命令的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]添加 可能會導致 UI 擁擠。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供了説明最小化 UI 命令混淆的方法。

## <a name="in-this-section"></a>本節內容
- [提供可用的命令](../../extensibility/internals/making-commands-available.md)

 提供添加 VS 包時[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]最小化 UI 擠擁的一般準則。

- [放置方針](../../extensibility/internals/command-placement-guidelines.md)

 提供根據命令集的大小實現 VSPackage 的特定準則。

## <a name="related-sections"></a>相關章節
- [命令、功能表及工具列](../../extensibility/internals/commands-menus-and-toolbars.md)

 說明如何建立包含功能表、工具列和命令下拉式方塊的 UI。
