---
title: 取得文字顏色標示的字型和色彩資訊 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8724c31accb26e478c2726dfe791256994fc95ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696849"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>取得文字顏色標示的字型和色彩資訊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在使用者介面中呈現或顯示以色彩標示文字的程式 (UI) 元素取決於專案類型、其技術和開發人員喜好設定。 [字型 **和色彩** ] 屬性頁會儲存設定。  
  
 顯示以色彩標示文字的大部分執行都需要 `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` 和相關聯的介面，以呈現、取得和儲存文字顯示設定。  
  
> [!NOTE]
> 自訂支援 **文字 EditorCategory**) 的核心編輯器 (時，強烈建議您在 language service 中使用著色技術。 如需詳細資訊，請參閱 [字型和色彩總覽](../extensibility/font-and-color-overview.md)。  
  
## <a name="getting-default-font-and-color-information"></a>取得預設字型和色彩資訊  
 任何顯示文字之視窗的字型**和色彩**設定都應該在一個**類別目錄**的**顯示專案**中指定。 如需詳細資訊，請參閱 [字型 [和色彩]、[環境]、[選項] 對話方塊](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)。  
  
 若要著色，VSPackage 必須取得目前的字型 **和色彩** 設定。 VSPackage 可透過下列方式完成這項工作，視其需求而定：  
  
- 使用字型和色彩持續性機制來取得已儲存或目前的狀態。 如需詳細資訊，請參閱 [存取預存字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> 如果 VSPackage 也不是字型和色彩提供者，請使用提供字型和色彩資料的服務介面來取得的實例。  
  
- 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> 介面。  
  
  為了確保輪詢所取得的結果是最新的，使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> 介面判斷介面的抓取方法之前是否需要更新，可能會很有用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 。  
  
  取得字型和色彩資訊之後，請剖析要顯示的文字，以找出需要顏色標示的元素，然後使用適當的字型和色彩在視窗中顯示文字。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [使用字型和文字](https://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [使用色彩](https://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (圖形裝置介面) ](https://msdn.microsoft.com/7e1d4540-bb2e-4257-8eee-eee376acba83)
