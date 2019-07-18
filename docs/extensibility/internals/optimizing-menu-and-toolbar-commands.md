---
title: 將功能表和工具列命令最佳化 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c76e4f37fd77bd35526153bd86d419417a6cdb6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333119"
---
# <a name="optimizing-menu-and-toolbar-commands"></a>將功能表和工具列命令最佳化
Vspackage 和其對應的命令，以新增[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可能會造成太過擁擠的 UI。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供方法來協助減少 UI 命令產生混淆。

## <a name="in-this-section"></a>本節內容
- [提供可用的命令](../../extensibility/internals/making-commands-available.md)

 提供一般指導方針降至最低的過度擁擠[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]UI，當您將加入 Vspackage。

- [放置方針](../../extensibility/internals/command-placement-guidelines.md)

 實作 VSPackage 的命令集的大小根據提供的特定指導方針。

## <a name="related-sections"></a>相關章節
- [命令、功能表及工具列](../../extensibility/internals/commands-menus-and-toolbars.md)

 說明如何建立包含功能表、工具列和命令下拉式方塊的 UI。