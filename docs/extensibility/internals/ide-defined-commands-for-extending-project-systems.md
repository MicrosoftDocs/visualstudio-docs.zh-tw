---
title: 擴充專案系統的 IDE-Defined 命令 |Microsoft Docs
description: 瞭解用來擴充專案系統的 Visual Studio 整合式開發環境 (IDE) 中定義的命令和命令群組。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d5147f4e03b019b083613a77afe95b95e9e033a
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761162"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>用來擴充專案系統的 IDE 定義的命令
當您想要擴充專案系統時，可以使用 IDE 所提供的命令和命令群組 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

 下列各節列出特別適用于擴充專案系統的命令專案。

## <a name="command-menus"></a>命令功能表
 下表顯示的命令功能表是很實用的位置，可讓您放置高階命令以叫用專案擴充項。

|命令功能表|描述|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|**專案** 最上層功能表。|
|IDM_VS_TOOL_PROJWIN|**方案總管** 的工具列。|

## <a name="shortcut-menus"></a>快顯功能表
 下表顯示在 **方案總管** 中選取單一節點時，或當 **方案總管** 中有多個同質選取時（當所有選取的節點都屬於相同類型時）適用的快捷方式功能表。

|捷徑功能表|描述|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|適用于選取專案節點時。|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|當選取檔案時套用。|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|當選取資料夾時套用。|
|IDM_VS_CTXT_WEBREFFOLDER|適用于選取 [Web 參考] 資料夾時。|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|當已選取參考名為 "References" 的參考根節點時套用。|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|適用于選取參考節點時：這些只包括元件、COM 和專案參考。 不包含 Web 參考。|

 下表顯示當 **方案總管** 中的選取範圍跨越多個階層時適用的快捷方式功能表。

|捷徑功能表|描述|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|當目前的選取範圍包含方案節點和根專案節點時套用。|
|IDM_VS_CTXT_XPROJ_SLNITEM|當目前的選取範圍包含方案節點和專案專案時套用。|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|當目前的選取範圍只包含多個根專案節點時適用。|
|IDM_VS_CTXT_XPROJ_PROJITEM|當目前的選取範圍包含根專案節點和專案專案的混合時套用。 此外，選取專案可能包含方案節點。|
|IDM_VS_CTXT_XPROJ_MULTIITEM|當目前的選取範圍包含方案中的多個專案的專案專案，或在相同專案中選取不同類型的專案時套用。|

## <a name="command-groups"></a>命令群組
 下表顯示您可以在擴充專案時使用的命令群組，以及可透過快捷方式功能表存取的命令群組 <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> 。

|命令群組|描述|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|用來建立、重建和部署專案的命令。|
|IDG_VS_CTXT_COMPILELINK|用來編譯和連結專案的命令。|
|IDG_VS_CTXT_PROJECT_CONFIG|設定專案設定和建立順序的命令。|
|IDG_VS_CTXT_PROJECT_ADD|將專案新增至專案的命令。|
|IDG_VS_CTXT_PROJECT_START|設定與 F5 鍵關聯之啟始專案的命令。|
|IDG_VS_CTXT_PROJECT_SAVE|儲存專案專案的命令。|
|IDG_VS_CTXT_PROJECT_DEBUG|用於偵錯工具的命令。|
|IDG_VS_CTXT_PROJECT_SCC|原始檔控制的命令。|
|IDG_VS_CTXT_PROJECT_TRANSFER|剪下、複製和貼上作業的命令。|
|IDG_VS_CTXT_PROJECT_PROPERTIES|提供 [ **專案屬性** ] 對話方塊存取權的命令。|

## <a name="see-also"></a>另請參閱

- [VSPackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [建立可重複使用的按鈕群組](../../extensibility/creating-reusable-groups-of-buttons.md)
