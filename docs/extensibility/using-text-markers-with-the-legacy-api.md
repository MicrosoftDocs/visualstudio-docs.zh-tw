---
title: 使用舊版 API 中的文字標記 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6f3662b5107d517f19b4803a37de4ebcf235bc9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353477"
---
# <a name="using-text-markers-with-the-legacy-api"></a>以舊版 API 使用文字標記
文字標記是文字的浮動的一組可能會影響顯示的緩衝區中和文字的區域的行為。 標記包含中斷點、 書籤、 波浪底線和唯讀區域。 文字標記是基本上不同於語法著色。 語法著色是文字的快速的方式進行通訊區域相關聯的語言語法。 當 Windows 在速度都很重要時，會重新繪製畫面中，通常要求語法著色。 語法標色變更文字的色彩。 文字標記可以變更許多其他的文字內容。 文字標記可以 「 浮動 」，並套用特殊的行為和著色。

 由於文字標記相關聯的效能額外負荷的情況下，不會建立許多標記文字緩衝區。 每次使用者編輯緩衝區的內容時，就會更新每個標記。

> [!NOTE]
> 使用者可以變更顯示的標記類型，但其圖案與樣式不使用的色彩。 如需詳細資訊，請參閱 <<c0> [ 字型和色彩、 環境、 選項對話方塊](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)。

## <a name="related-topics"></a>相關主題

| 標題 | 說明 |
| - | - |
| [如何：新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md) | 描述如何將所提供的標準文字標記類型[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器文字檢視。 |
| [如何：實作錯誤標記](../extensibility/how-to-implement-error-markers.md) | 描述如何實作的執行個體[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]用以使用紅色波浪底線指出錯誤的標記。 |
| [如何：建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md) | 描述如何建立並加入文字檢視中的自訂文字標記類型。 |
| [如何：使用文字標記](../extensibility/how-to-use-text-markers.md) | 說明如何新增文字標記。 |
| [深入探索核心編輯器](../extensibility/inside-the-core-editor.md) | 描述核心編輯器的功能，並提供有關如何自訂核心編輯器的詳細資料。 |
| [編輯器功能](https://msdn.microsoft.com/library/bdac940d-1f14-4019-a01f-fd0bb3dc7198) | 描述可用的功能[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器。 |

## <a name="reference"></a>參考資料
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> 提供統一的機制，來取得特定文字標記類型的相關資訊，是否預先定義的編輯器，或登錄的 VSPackage。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker> 提供存取權，並調整文字緩衝區中的文字標記的位置使用二維座標。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> 提供用於管理文字標記的方法。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 提供回呼，以便[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]IDE 和其他用來調整文字標記的程序。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> 擴充功能可透過<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>藉由提供額外的回呼介面。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx> 擴充功能可透過<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>藉由提供額外的回呼介面。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet> 可讓標記類型，以便判斷是否有其他標記類型共用相同色彩組。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> 提供核心編輯器中的文字標記的內容。 針對每個核心編輯器中的文字標記類型，IDE 會建立個別<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>物件。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler> 提供標記的圖像 （glyph） 支援拖放編輯處理常式。 圖像 （glyph） 是以圖示表示標記的位置。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> 傳回<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>介面從其他 Vspackage 的標記提供文字的服務。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker> 提供存取權，並使用一維座標調整文字緩衝區中的文字標記的位置。 如果可能，請勿使用此介面。