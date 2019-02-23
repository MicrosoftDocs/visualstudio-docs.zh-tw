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
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42a3fb7b44f0e21c564bc9bef26d5aa158d43091
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56631506"
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