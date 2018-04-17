---
title: 使用舊版 API 存取文字緩衝區 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 15
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 77002e095690da85e73f1a79d405cb5174b96851
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>使用舊版 API 存取文字緩衝區
文字是負責管理文字資料流和檔案的持續性。 雖然緩衝區可以讀取或寫入其他格式，使用 Unicode 來執行所有一般與緩衝區通訊。 在舊版的 Api，文字緩衝區可以使用一段或二維座標系統來找出緩衝區中的字元位置。  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>其中一個，而兩個維度座標系統  
 一維座標位置根據緩衝區，例如 147 中從第一個字元的字元位置。 您使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>介面，以存取緩衝區中的一維的位置。 二維座標系統為基礎行和索引組。 例如，43 緩衝區中的字元，5 會在行 43，該行的第一個字元右邊的五個字元。 您存取在緩衝區中使用的二維位置<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>介面。 同時<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>文字緩衝區物件會實作介面 (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) 而且可以使用來存取彼此`QueryInterface`。 下圖顯示這些和其他索引鍵的介面上<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>。  
  
 ![文字緩衝區物件](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
文字緩衝區物件  
  
 其中一個座標系統的運作方式的文字緩衝區中，雖然它被最佳化使用二維座標。 一維座標系統，可以建立的效能負擔。 因此，使用盡可能二維座標系統。  
  
 文字緩衝區的第二個責任是檔案的持續性。 若要這樣做，文字緩衝區物件會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>和做為專案項目的文件資料物件的元件和其他參與持續性的環境元件。 如需詳細資訊，請參閱[開啟和儲存的專案項目](../extensibility/internals/opening-and-saving-project-items.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [變更檢視設定，以使用舊版 API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 說明如何變更檢視設定使用舊版 API。  
  
 [使用文字管理員監控全域設定](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 說明如何使用文字管理員監視通用設定...  
  
## <a name="see-also"></a>另請參閱  
 [核心編輯器內](../extensibility/inside-the-core-editor.md)