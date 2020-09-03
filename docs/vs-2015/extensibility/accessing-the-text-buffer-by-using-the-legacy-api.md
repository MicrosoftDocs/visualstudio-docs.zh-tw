---
title: 使用舊版 API 存取文字緩衝區 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f2cfbd84bc4f9298358a2a2d1ba87f76d6e5303c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184989"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>使用舊版 API 存取文字緩衝區
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

文字負責管理文字資料流程和檔案持續性。 雖然緩衝區可以讀取或寫入其他格式，但使用 Unicode 來執行所有與緩衝區的一般通訊。 在舊版 Api 中，文字緩衝區可以使用一或二維座標系統來識別緩衝區中的字元位置。  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>一維座標系統和二維座標系統  
 一維座標位置是根據緩衝區中第一個字元的字元位置，例如147。 您可以使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> 介面來存取緩衝區中的一維位置。 二維座標系統是以行和索引配對為基礎。 例如，在43的緩衝區中的字元，5會在行43，也就是該行第一個字元右邊的五個字元。 您可以使用介面來存取緩衝區中的二維位置 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>和 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> 介面都是由 () 的文字緩衝區物件所執行 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> ，而且可以使用彼此存取 `QueryInterface` 。 下圖顯示中的這些和其他主要介面 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 。  
  
 ![文字緩衝區物件](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
文字緩衝區物件  
  
 雖然這兩個座標系統在文字緩衝區中都能運作，但它已經過優化，可以使用二維座標。 一維座標系統可能會產生效能負擔。 因此，請盡可能使用二維座標系統。  
  
 文字緩衝區的第二個責任是檔案持續性。 若要這樣做，文字緩衝區物件會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 針對專案專案和其他與持續性相關的環境元件，實作為檔資料物件元件。 如需詳細資訊，請參閱 [開啟和儲存專案專案](../extensibility/internals/opening-and-saving-project-items.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [使用舊版 API 變更檢視設定](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 說明如何使用舊版 API 變更視圖設定。  
  
 [使用文字管理員監視全域設定](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 說明如何使用文字管理員監視全域設定。  
  
## <a name="see-also"></a>另請參閱  
 [深入探索核心編輯器](../extensibility/inside-the-core-editor.md)
