---
title: 使用舊版 API 存取的文字緩衝 |Microsoft Docs
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940132"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>使用舊版 API 存取的文字緩衝區
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

負責管理文字資料流和檔案持續性的文字。 雖然緩衝區可以讀取或寫入其他格式中，使用 Unicode 來執行所有一般的通訊緩衝區。 在舊版的 Api 中，文字緩衝區可以使用一段或二維的座標系統識別緩衝區中的字元位置。  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>一個和兩個維度座標系統  
 一維座標位置為基礎的第一個字元緩衝區，例如 147 中的字元的位置。 您使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>介面，以存取緩衝區中的一維的位置。 二維的座標系統根據行和索引的配對。 比方說，43 緩衝區中的字元，5 會在行 43，該行的第一個字元右邊的五個字元。 您存取在緩衝區中使用的二維位置<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>介面。 同時<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>而<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>介面由文字緩衝區物件 (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>)，而且可以使用存取彼此`QueryInterface`。 下圖顯示這些和其他重要的介面上<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>。  
  
 ![文字緩衝區物件](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
文字緩衝區物件  
  
 雖然兩個座標系統的運作方式的文字緩衝區中，最好使用二維座標。 一維的座標系統造成的效能負擔。 因此，使用盡可能二維座標系統。  
  
 文字緩衝區的第二個責任就檔案持續性。 若要這樣做，文字緩衝區物件會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>，做為專案項目的文件資料物件的元件和其他參與持續性的環境元件。 如需詳細資訊，請參閱 <<c0> [ 開啟和儲存專案項目](../extensibility/internals/opening-and-saving-project-items.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [使用舊版 API 變更檢視設定](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 說明如何變更檢視設定使用舊版 API。  
  
 [使用文字管理員監視全域設定](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 說明如何使用文字管理員監視全域設定...  
  
## <a name="see-also"></a>另請參閱  
 [深入探索核心編輯器](../extensibility/inside-the-core-editor.md)
