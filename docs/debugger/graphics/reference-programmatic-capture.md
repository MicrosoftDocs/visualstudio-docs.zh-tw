---
title: "參考 （程式設計擷取） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 899211452a776931e3d0d9742e499ed8ba78a652
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="reference-programmatic-capture"></a>參考 (程式設計擷取)
透過程式設計擷取應用程式開發介面，圖形診斷支援以程式設計方式控制其擷取功能。 您可以使用這個應用程式開發介面，在圖形診斷抬頭顯示器 (HUD) 切換並加入訊息、初始化和建立圖形記錄檔，以及擷取圖形資訊。  
  
## <a name="programmatic-capture-apis"></a>程式設計擷取應用程式開發介面  
  
### <a name="classes"></a>類別  
  
|名稱|說明|  
|----------|-----------------|  
|[VsgDbg 類別](vsgdbg-class.md)|表示以程式設計方式控制圖形診斷應用程式內部元件的介面。|  
  
### <a name="preprocessor-symbols"></a>前置處理器符號  
  
|名稱|說明|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|出現時，定義圖形記錄檔是否儲存到使用者的暫存檔目錄。|  
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|定義圖形記錄檔的預設檔案名稱。|  
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|出現時，定義是否提供 `VsgDbg` 類別的預設執行個體。|  
  
## <a name="related-articles"></a>相關文章  
  
|標題|說明|  
|-----------|-----------------|  
|[Capturing Graphics Information](capturing-graphics-information.md)|示範如何從 DirectX 應用程式擷取圖形資訊，以便使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 圖形診斷工具來診斷轉譯問題。|  
|[概觀](overview-of-visual-studio-graphics-diagnostics.md)|示範圖形診斷如何協助您偵錯 DirectX 遊戲和應用程式的轉譯錯誤。|