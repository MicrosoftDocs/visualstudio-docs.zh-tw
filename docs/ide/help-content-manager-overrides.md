---
title: "Help Content Manager 覆寫設定 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-help-viewer
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: c4889d40e9ca53cccf7de384e609eb959d8981f5
ms.contentlocale: zh-tw
ms.lasthandoff: 05/13/2017

---
# <a name="help-content-manager-overrides"></a>Help Content Manager 覆寫設定
您可以修改登錄，來變更說明檢視器和 Visual Studio IDE 之說明相關功能的預設行為。  
  
|工作|登錄機碼|值和定義|  
|----------|------------------|--------------------------|  
|定義唯一的服務端點|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|NewContentAndUpdateService--*HTTPValueForTheServiceEndpoint*。|  
|定義線上/離線預設值|HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help|UseOnlineHelp - 輸入 `0` 可指定本機說明，輸入 `1` 可指定線上說明。|  
|定義唯一的 F1 端點|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|OnlineBaseUrl--*HTTPValueForTheServiceEndpoint*|  
|覆寫 BITS 工作優先權|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (在 64 位元電腦上)\Microsoft\Help\v2.2|BITSPriority - 使用下列其中一個值：**前景**、**高**、**正常**或**低**。|  
|停用線上 (和 IDE Online 選項)|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (在 64 位元電腦上)\Microsoft\VisualStudio\14.0\Help|OnlineHelpPreferenceDisabled - 設為 1 可停用線上說明內容的存取。|  
|停用管理內容|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (在 64 位元電腦上)\Microsoft\VisualStudio\14.0\Help|ContentManagementDisabled - 設為 1 可停用 Help Viewer 中的 [管理內容] 索引標籤。|  
|指向網路共用上的本機內容存放區|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio11|LocationPath="*ContentStoreNetworkShare*"|  
|停用第一次啟動 Visual Studio 功能時所安裝的內容。|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (在 64 位元電腦上)\Microsoft\VisualStudio\14.0\Help|DisableFirstRunHelpSelection - 設為 1 可停用第一次啟動 Visual Studio 時所設定的說明功能。|  
  
## <a name="see-also"></a>另請參閱  
 [說明檢視器系統管理員指南](../ide/help-viewer-administrator-guide.md)
