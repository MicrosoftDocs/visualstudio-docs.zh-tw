---
title: 延伸項目系統的 IDE 定義指令 ( 2) ( 2)微軟文件
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
ms.openlocfilehash: 61c0b2924548f50ad650389e3ad81759be1986a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707728"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>用來擴充專案系統的 IDE 定義的命令
如果要擴展項目系統,可以使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 提供的命令和命令組。

 以下各節列出了對擴展項目系統特別有用的命令項。

## <a name="command-menus"></a>命令選單
 下表顯示了用於放置調用專案擴展器的高級命令的有用位置的命令功能表。

|命令選單|描述|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|**項目**頂級功能表。|
|IDM_VS_TOOL_PROJWIN|**解決方案資源管理員**工具列。|

## <a name="shortcut-menus"></a>快顯功能表
 下表顯示了**在解決方案資源管理器**中選擇單個節點時應用的快捷功能表,或者**解決方案資源管理器**中有多個同質選擇時應用的快捷功能表,即所有選定節點的類型相同時。

|捷徑功能表|描述|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|在選擇專案節點時應用。|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|在選擇檔時應用。|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|在選擇資料夾時應用。|
|IDM_VS_CTXT_WEBREFFOLDER|選擇 Web 參考資料夾時應用。|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|當選擇名為"引用"的引用根節點時應用。|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|在選擇引用節點時應用;這些僅包括程式集、COM 和專案引用。 不包括 Web 引用。|

 下表顯示了**解決方案資源管理器**中選區跨越多個層次結構時應用的快捷功能表,

|捷徑功能表|描述|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|當當前選擇包含解決方案節點和根專案節點時應用。|
|IDM_VS_CTXT_XPROJ_SLNITEM|當當前選擇包含解決方案節點和專案項時應用。|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|當當前選擇僅由多個根專案節點組成時應用。|
|IDM_VS_CTXT_XPROJ_PROJITEM|當當前選擇包含根專案節點和專案項的組合時,將應用。 此外,所選內容可能包含解決方案節點。|
|IDM_VS_CTXT_XPROJ_MULTIITEM|當當前選擇包含解決方案中多個專案中的專案項,或者在同一專案中選擇不同類型的項時,應用。|

## <a name="command-groups"></a>命令群組
 下表顯示了在擴展專案時可以使用的命令組,並且可以<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>通過 快捷菜單訪問。

|命令群組|描述|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|用於生成、重建和部署專案的命令。|
|IDG_VS_CTXT_COMPILELINK|用於編譯和連結專案的命令。|
|IDG_VS_CTXT_PROJECT_CONFIG|設置專案配置和生成順序的命令。|
|IDG_VS_CTXT_PROJECT_ADD|向專案添加項的命令。|
|IDG_VS_CTXT_PROJECT_START|設置與 F5 金鑰關聯的啟動專案的命令。|
|IDG_VS_CTXT_PROJECT_SAVE|用於保存專案項的命令。|
|IDG_VS_CTXT_PROJECT_DEBUG|用於調試的命令。|
|IDG_VS_CTXT_PROJECT_SCC|源控制的命令。|
|IDG_VS_CTXT_PROJECT_TRANSFER|剪下、複製和貼上操作的命令。|
|IDG_VS_CTXT_PROJECT_PROPERTIES|提供對「**項目屬性**」對話框的訪問的命令。|

## <a name="see-also"></a>另請參閱

- [VSPackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [建立可重複使用的按鈕群組](../../extensibility/creating-reusable-groups-of-buttons.md)
