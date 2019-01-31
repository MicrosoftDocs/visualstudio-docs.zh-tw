---
title: Help Content Manager 覆寫設定 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9dfd7f7d75a44cb28e2829e38c27b63a329eacaa
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804462"
---
# <a name="help-content-manager-overrides"></a>Help Content Manager 覆寫設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以修改登錄，來變更說明檢視器和 Visual Studio IDE 之說明相關功能的預設行為。  
  
|工作|登錄機碼|值和定義|  
|----------|------------------|--------------------------|  
|定義唯一的服務端點|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|NewContentAndUpdateService--*HTTPValueForTheServiceEndpoint*。|  
|定義線上/離線預設值|HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help|UseOnlineHelp - 輸入 `0` 可指定本機說明，輸入 `1` 可指定線上說明。|  
|定義唯一的 F1 端點|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|OnlineBaseUrl--*HTTPValueForTheServiceEndpoint*|  
|覆寫 BITS 工作優先權|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (在 64 位元電腦上)\Microsoft\Help\v2.2|BITSPriority - 使用下列其中一個值：**前景**、**高**、**正常**或**低**。|  
|停用線上 (和 IDE Online 選項)|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (在 64 位元電腦上)\Microsoft\VisualStudio\14.0\Help|OnlineHelpPreferenceDisabled - 設為 1 可停用線上說明內容的存取。|  
|停用管理內容|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (在 64 位元電腦上)\Microsoft\VisualStudio\14.0\Help|ContentManagementDisabled - 設為 1 可停用 Help Viewer 中的 [管理內容] 索引標籤。|  
|指向網路共用上的本機內容存放區|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio11|LocationPath=”內容存放區網路共用”|  
|停用第一次啟動 Visual Studio 功能時所安裝的內容。|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (在 64 位元電腦上)\Microsoft\VisualStudio\14.0\Help|DisableFirstRunHelpSelection - 設為 1 可停用第一次啟動 Visual Studio 時所設定的說明功能。|  
  
## <a name="see-also"></a>請參閱  
 [說明檢視器系統管理員指南](../ide/help-viewer-administrator-guide.md)
