---
title: 搭配舊版 API 使用文字標記 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dff5e6ecf60d389730841e99b87db584465e020
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695483"
---
# <a name="using-text-markers-with-the-legacy-api"></a>以舊版 API 使用文字標記
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

文字標記是緩衝區中的浮動文字範圍，可能會影響文字區域的顯示和行為。 標記包括中斷點、書簽、波浪底線和唯讀區域。 文字標記基本上與語法色彩不同。 語法著色是一種快速的方法，可傳達與文字區域相關聯的語言語法。 當 Windows 重新繪製畫面時，通常會要求語法著色（當速度很重要時）。 語法著色只會變更文字色彩。 文字標記可以變更許多其他文字屬性。 文字標記可「浮動」並套用特殊行為和著色。  
  
 由於與文字標記相關聯的效能負荷，因此請勿為您的文字緩衝區建立多個標記。 每次使用者編輯緩衝區內容時，會更新每個標記。  
  
> [!NOTE]
> 使用者可以變更可見標記類型的色彩，但不能變更其圖形和樣式。 如需詳細資訊，請參閱 [字型 [和色彩]、[環境]、[選項] 對話方塊](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)。  
  
## <a name="related-topics"></a>[相關主題]  
  
|標題|描述|  
|-----------|-----------------|  
|[如何：新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)|描述如何將核心編輯器提供的標準文字標記類型加入 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 至文字視圖。|  
|[如何：實作錯誤標記](../extensibility/how-to-implement-error-markers.md)|描述如何使用紅色波浪底線來執行 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 用來指出錯誤的標記實例。|  
|[如何：建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)|描述如何建立自訂文字標記類型，並將其加入至文字視圖。|  
|[如何：使用文字標記](../extensibility/how-to-use-text-markers.md)|說明如何新增文字標記。|  
|[深入探索核心編輯器](../extensibility/inside-the-core-editor.md)|描述核心編輯器的功能，並提供如何自訂核心編輯器的詳細資料。|  
|[編輯器功能](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|描述核心編輯器中的可用功能 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。|  
  
## <a name="reference"></a>參考  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 提供統一的機制，以取得特定文字標記類型的相關資訊，無論是由編輯器預先定義或由 VSPackage 註冊。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 使用二維座標，提供存取並調整文字緩衝區中文字標記的位置。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 提供管理文字標記的方法。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 提供 IDE 的回呼 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，以及用來調整文字標記的其他處理常式。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 藉由提供額外的回呼，擴充可透過介面取得的功能 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 藉由提供額外的回呼，擴充可透過介面取得的功能 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 啟用標記類型，以判斷其他標記類型是否共用同一組色彩。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 提供核心編輯器中文字標記的內容。 針對核心編輯器中的每個文字標記類型，IDE 會建立個別的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> 物件。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 針對符號支援拖放編輯的標記提供的處理常式。 圖像是指出標記位置的圖示。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>從提供文字標記給其他 vspackage 的服務傳回介面。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 使用一維座標，提供存取並調整文字緩衝區中文字標記的位置。 如果可能，請不要使用此介面。
