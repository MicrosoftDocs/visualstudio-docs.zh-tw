---
title: IDE 定義的命令，來擴充專案系統 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b5de061449844b87d60d7a700b1e1c22e1e1282
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195028"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>用來擴充專案系統的 IDE 定義的命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

當您想要擴充專案系統時，您可以使用命令和命令所提供的群組[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE。  
  
 下列各節列出命令的項目，來擴充專案系統特別有用。  
  
## <a name="command-menus"></a>命令功能表  
 下表會很有用的位置，您可以叫用專案擴充性的高階命令的命令功能表。  
  
|命令功能表|說明|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|**專案**最上層的功能表。|  
|IDM_VS_TOOL_PROJWIN|**方案總管 中**工具列。|  
  
## <a name="shortcut-menus"></a>快顯功能表  
 下表顯示快顯功能表中選取單一節點時，適用於**方案總管**，或有多個同質性的選取項目中時**方案總管 中**，這是當所有選取的節點都屬於相同的類型。  
  
|快顯功能表|說明|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|適用於選取專案節點時。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|選取檔案時套用。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|適用於選取資料夾時。|  
|IDM_VS_CTXT_WEBREFFOLDER|適用於選取 [Web 參考] 資料夾時。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|適用於選取稱為 「 參考 」 的 [參考] 根節點時。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|適用於選取參考節點; 時這些包括組件、 COM 和僅限專案參考。 不包含 Web 參考。|  
  
 下表顯示時，適用的快顯功能表中的選取項目**方案總管 中**跨越多個階層，  
  
|快顯功能表|描述|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|適用於目前的選取範圍包含在解決方案節點和根專案節點時。|  
|IDM_VS_CTXT_XPROJ_SLNITEM|適用於目前的選取範圍包含方案節點和專案項目時。|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|適用於當目前的選取範圍包含多個專案只限根節點。|  
|IDM_VS_CTXT_XPROJ_PROJITEM|適用於當目前的選取項目包含混合的根專案節點和專案項目。 此外，選取項目可能包含的方案節點。|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|適用於目前的選取範圍包含來自多個專案在方案中，專案項目時，或選取相同的專案中的不同類型的項目時。|  
  
## <a name="command-groups"></a>命令群組  
 下表顯示您可以使用擴充的專案，而您可以透過存取時的命令群組<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>快顯功能表。  
  
|命令群組|說明|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|建置、 重建和部署專案的命令。|  
|IDG_VS_CTXT_COMPILELINK|編譯和連結專案的命令。|  
|IDG_VS_CTXT_PROJECT_CONFIG|設定專案的組態，並建置順序的命令。|  
|IDG_VS_CTXT_PROJECT_ADD|將項目加入至專案的命令。|  
|IDG_VS_CTXT_PROJECT_START|設定啟始 F5 索引鍵相關聯的命令。|  
|IDG_VS_CTXT_PROJECT_SAVE|儲存專案項目命令。|  
|IDG_VS_CTXT_PROJECT_DEBUG|偵錯命令。|  
|IDG_VS_CTXT_PROJECT_SCC|原始檔控制命令。|  
|IDG_VS_CTXT_PROJECT_TRANSFER|命令進行剪下、 複製和貼上作業。|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|提供存取權的命令**專案屬性** 對話方塊。|  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommand 對比OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [建立可重複使用的按鈕群組](../../extensibility/creating-reusable-groups-of-buttons.md)
