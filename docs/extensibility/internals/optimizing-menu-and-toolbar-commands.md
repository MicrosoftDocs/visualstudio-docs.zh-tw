---
title: 優化功能表和工具列命令 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706911"
---
# <a name="optimizing-menu-and-toolbar-commands"></a>將功能表和工具列命令最佳化
將 Vspackage 及其對應的命令新增至 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 可能會導致擁擠的 UI。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供可協助將 UI 命令混淆降至最低的方式。

## <a name="in-this-section"></a>本節內容
- [提供可用的命令](../../extensibility/internals/making-commands-available.md)

 提供 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 當您新增 vspackage 時，最小化 UI 根本的一般方針。

- [放置方針](../../extensibility/internals/command-placement-guidelines.md)

 根據命令集的大小，提供執行 VSPackage 的特定指導方針。

## <a name="related-sections"></a>相關章節
- [命令、功能表及工具列](../../extensibility/internals/commands-menus-and-toolbars.md)

 說明如何建立包含功能表、工具列和命令下拉式方塊的 UI。
