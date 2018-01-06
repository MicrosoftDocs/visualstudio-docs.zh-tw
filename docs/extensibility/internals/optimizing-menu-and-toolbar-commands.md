---
title: "功能表和工具列命令的最佳化 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f95675f420284b9d67a6d36ac30b3e71f085e565
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="optimizing-menu-and-toolbar-commands"></a>最佳化功能表和工具列命令
Vspackage 和其對應的命令來新增[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可能會造成太過擁擠的 UI。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供方法來協助降低 UI 命令產生混淆。  
  
## <a name="in-this-section"></a>本節內容  
 [提供可用的命令](../../extensibility/internals/making-commands-available.md)  
 提供一般指導方針降到最低的過度擁擠[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]UI，當您將加入 Vspackage。  
  
 [放置指導方針](../../extensibility/internals/command-placement-guidelines.md)  
 提供特定指導方針實作 VSPackage 根據命令集的大小。  
  
## <a name="related-sections"></a>相關章節  
 [命令、功能表及工具列](../../extensibility/internals/commands-menus-and-toolbars.md)  
 說明如何建立包含功能表、工具列和命令下拉式方塊的 UI。