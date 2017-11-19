---
title: "使用舊版應用程式開發介面中的文字標記 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 64f4d7f7e4a71c1d304bfa5045175fd613bcb539
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="using-text-markers-with-the-legacy-api"></a>使用文字標記與舊版應用程式開發介面
文字標記是文字的浮動範圍中的緩衝區，可能會影響顯示和文字的區域的行為。 標記包含中斷點、 書籤，波浪底線和唯讀區域。 文字標記會基本上不同的語法著色。 語法著色是文字的快速的方式進行通訊區域相關聯的語言語法。 當 Windows 在速度都很重要時，會重新繪製畫面上，通常被要求語法著色。 語法著色可變更文字的色彩。 文字標記可以變更許多其他的文字內容。 文字標記可以 「 浮動 」，並在套用特殊的行為和著色。  
  
 文字標記相關聯的效能負擔，因為不會建立多個標記文字緩衝區。 每個標記會更新每次使用者編輯緩衝區內容。  
  
> [!NOTE]
>  使用者可以變更顯示的標記類型，但其圖形和樣式不使用的色彩。 如需詳細資訊，請參閱[字型和色彩、 環境、 選項對話方塊](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[如何： 加入標準文字標記](../extensibility/how-to-add-standard-text-markers.md)|描述如何將所提供的標準文字標記類型[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]文字檢視核心編輯器。|  
|[如何： 實作錯誤標記](../extensibility/how-to-implement-error-markers.md)|描述如何實作的執行個體[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]用於使用紅色波浪底線指出錯誤的標記。|  
|[如何： 建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)|描述如何建立和自訂文字標記類型將文字檢視。|  
|[如何： 使用文字標記](../extensibility/how-to-use-text-markers.md)|說明如何新增文字標記。|  
|[核心編輯器內](../extensibility/inside-the-core-editor.md)|描述核心編輯器的功能並提供有關如何自訂核心編輯器的詳細資料。|  
|[編輯器功能](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|描述可用的功能[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器。|  
  
## <a name="reference"></a>參考資料  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 提供統一的機制，來取得特定的文字標記類型的相關資訊，是否由編輯器 中預先定義或登錄的 VSPackage。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 提供存取權，並調整文字標記中的文字緩衝區的位置使用二維座標。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 提供管理文字標記的方法。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 提供回呼[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]IDE 和其他用來調整文字標記的處理序。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 擴充功能，可透過<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>藉由提供額外的回呼介面。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 擴充功能，可透過<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>藉由提供額外的回呼介面。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 可讓標記類型，以便判斷是否有其他標記類型共用相同的色彩集。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 提供的核心編輯器中的文字標記內容。 IDE 會針對每個核心編輯器中的文字標記類型，建立個別<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>物件。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 提供標記的圖像 （glyph） 支援拖放編輯處理常式。 圖像是以圖示表示標記的位置。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 傳回<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>介面從其他 vspackage 標記提供文字的服務。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 提供存取，並使用一維座標調整文字標記中的文字緩衝區的位置。 如果可能的話，請勿使用這個介面。