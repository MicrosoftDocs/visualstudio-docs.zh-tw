---
title: 舊版語言服務模型 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 943f0f013045e3082af3069ed4d45aaed1096869
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131572"
---
# <a name="model-of-a-legacy-language-service"></a>舊版語言服務模型
語言服務定義的項目和功能特定的語言，並用來提供該語言的特定資訊的編輯器。 例如，編輯器必須知道的項目和語言的關鍵字，以支援的語法著色。  
  
 語言服務密切管理編輯器和檢視，其中包含編輯器 中的文字緩衝區。 Microsoft IntelliSense**快速諮詢**選項是語言服務所提供之功能的範例。  
  
## <a name="a-minimal-language-service"></a>基本語言服務  
 最基本的語言服務包含下列兩個物件：  
  
-   *語言服務*實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>介面。 語言服務的語言，包括其名稱、 副檔名的檔案、 程式碼視窗管理員和色彩標示器資訊。  
  
-   *色彩標示器*實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>介面。  
  
 概念圖將顯示模型的基本語言服務。  
  
 ![語言服務模型圖形](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
基本語言服務模型  
  
 文件視窗主機*文件檢視*編輯器，在此情況下的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]核心編輯器。 編輯器 中所擁有的文件檢視和文字緩衝區。 這些物件運作的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]透過特製化的文件視窗呼叫*程式碼視窗*。 程式碼視窗中<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>建立和由 IDE 所控制的物件。  
  
 載入指定的副檔名的檔案時，編輯器會找出與該副檔名相關聯之語言服務並將傳遞給它的程式碼視窗藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>方法。 語言服務傳回*程式碼視窗管理員*，它會實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>介面。  
  
 下表提供模型中物件的概觀。  
  
|元件|Object|功能|  
|---------------|------------|--------------|  
|文字緩衝區|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Unicode 讀取/寫入文字資料流。 您可使用其他編碼的文字。|  
|程式碼視窗|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|文件視窗包含一個或多個文字檢視。 當[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是在多重文件介面 (MDI) 模式中，程式碼視窗是 MDI 子系。|  
|文字檢視|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|可讓使用者瀏覽，並使用鍵盤和滑鼠來檢視文字視窗中。 做為編輯器，對使用者顯示的文字檢視。 您可以使用一般的編輯器視窗、 [輸出] 視窗和即時運算視窗中的文字檢視。 此外，您可以設定程式碼視窗中的一個或多個文字檢視。|  
|文字管理員|受<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>服務，而從中您取得<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>指標|維護常用資訊先前所述的所有元件都共用的元件。|  
|語言服務|實作而定;實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|物件，提供特定語言資訊，例如語法反白顯示、 陳述式完成和大括號比對的編輯器。|  
  
## <a name="see-also"></a>另請參閱  
 [自訂編輯器中的文件資料和文件檢視](../../extensibility/document-data-and-document-view-in-custom-editors.md)