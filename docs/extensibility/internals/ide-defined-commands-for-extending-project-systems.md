---
title: IDE 定義的命令，以擴充專案系統 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4941f5d842f311f078594ee9a9deef02219ea05d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>IDE 定義的命令，以擴充專案系統
當您想要擴充的專案系統時，您可以使用命令和命令所提供的群組[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
 下列章節會列出對於擴充的專案系統特別有用的命令項目。  
  
## <a name="command-menus"></a>功能表命令  
 下表顯示有用的位置，讓您將叫用專案擴充性的高層級命令的命令功能表。  
  
|命令功能表|描述|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|**專案**最上層功能表。|  
|IDM_VS_TOOL_PROJWIN|**方案總管 中**工具列。|  
  
## <a name="shortcut-menus"></a>快顯功能表  
 下表顯示快顯功能表中選取單一節點時所要套用**方案總管 中**，或有多個同質性的選取項目中時**方案總管 中**，這是當所有選取的節點都屬於相同的類型。  
  
|快顯功能表|描述|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|適用於選取專案節點時。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|選取檔案時適用。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|適用於選取資料夾時。|  
|IDM_VS_CTXT_WEBREFFOLDER|適用於選取 [Web 參考] 資料夾時。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|適用於選取參考根節點，稱為 [參考] 時。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|適用於當未選取參考節點。這些包括組件、 COM 及僅限專案參考。 不包含 Web 參考。|  
  
 下表顯示時，適用的快顯功能表中的選取範圍**方案總管 中**跨越多個階層，  
  
|快顯功能表|描述|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|適用於目前的選取範圍包含的方案節點和根專案節點時。|  
|IDM_VS_CTXT_XPROJ_SLNITEM|適用於目前的選取範圍包含方案節點和專案項目時。|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|適用於多個根專案節點只包含目前的選取範圍時。|  
|IDM_VS_CTXT_XPROJ_PROJITEM|適用於目前的選取範圍包含混合的根專案節點和專案項目時。 此外，選取項目可能包含的方案節點。|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|適用於目前的選取範圍包含從方案中的多個專案的專案項目時，或相同專案中選取不同類型的項目。|  
  
## <a name="command-groups"></a>命令群組  
 下表顯示當擴充的專案，而且您可以透過存取時，您可以使用的命令群組<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>快顯功能表。  
  
|命令群組|描述|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|建立、 重建和部署專案的命令。|  
|IDG_VS_CTXT_COMPILELINK|編譯及連結專案命令。|  
|IDG_VS_CTXT_PROJECT_CONFIG|設定專案組態設定和建置順序的命令。|  
|IDG_VS_CTXT_PROJECT_ADD|將項目加入至專案的命令。|  
|IDG_VS_CTXT_PROJECT_START|設定啟始專案 F5 索引鍵相關聯的命令。|  
|IDG_VS_CTXT_PROJECT_SAVE|儲存專案項目的命令。|  
|IDG_VS_CTXT_PROJECT_DEBUG|偵錯命令。|  
|IDG_VS_CTXT_PROJECT_SCC|原始檔控制命令。|  
|IDG_VS_CTXT_PROJECT_TRANSFER|命令進行剪下、 複製和貼上作業。|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|命令可提供存取**專案屬性** 對話方塊。|  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommand 對比OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [建立可重複使用的按鈕群組](../../extensibility/creating-reusable-groups-of-buttons.md)