---
title: 舊版語言服務模型 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ccea832f1979601a764c0b979b0f7d4d72bd796
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487146"
---
# <a name="model-of-a-legacy-language-service"></a>舊版語言服務模型
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[舊版語言服務模型](https://docs.microsoft.com/visualstudio/extensibility/internals/model-of-a-legacy-language-service)。  
  
語言服務定義的項目和功能特定的語言，並用來提供該語言的特定資訊的編輯器。 比方說，編輯器必須知道的項目和語言的關鍵字，以支援語法著色。  
  
 語言服務密切搭配受編輯器和檢視，其中包含編輯器的文字緩衝。 Microsoft IntelliSense**快速諮詢**選項是語言服務所提供的功能的範例。  
  
## <a name="a-minimal-language-service"></a>最小語言服務  
 最基本的語言服務包含下列兩個物件：  
  
-   *語言服務*實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>介面。 語言服務具有語言，包括其名稱、 副檔名的檔案、 程式碼視窗管理員，以及色彩標示器的相關資訊。  
  
-   *色彩標示器*實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>介面。  
  
 以下概念圖會顯示基本語言服務的模型。  
  
 ![語言服務模型圖形](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
基本語言服務模型  
  
 文件視窗主機*文件檢視*編輯器，在此情況下的[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]核心編輯器。 編輯器所擁有的文件檢視和文字緩衝區。 這些物件搭配[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]透過特殊文件視窗中，呼叫*程式碼視窗*。 程式碼 視窗內<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>建立並由 IDE 所控制的物件。  
  
 載入具有指定副檔名的檔案時，編輯器會尋找該延伸模組相關聯的語言服務，並傳遞給它的程式碼視窗呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>方法。 語言服務會傳回*程式碼視窗管理員*，它會實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>介面。  
  
 下表中的物件模型概觀。  
  
|元件|Object|功能|  
|---------------|------------|--------------|  
|文字緩衝區|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Unicode 讀取/寫入文字資料流。 可以使用其他編碼的文字。|  
|程式碼視窗|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|文件視窗，其中包含一或多個文字檢視。 當[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]是在多重文件介面 (MDI) 模式中，程式碼視窗會是 MDI 子表單。|  
|文字檢視|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|可讓使用者瀏覽，以及使用鍵盤和滑鼠來檢視文字視窗。 對使用者顯示做為編輯器文字檢視。 您可以使用一般的編輯器視窗、 [輸出] 視窗中和即時運算視窗中的文字檢視。 此外，您可以設定程式碼視窗中的一或多個文字檢視。|  
|文字管理員|受<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>服務，而從中您取得<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>指標|此元件可維護由先前所述的所有元件共用的一般資訊。|  
|語言服務|實作而定;實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|物件，提供語言特定資訊，例如語法醒目提示、 陳述式完成和大括號比對的編輯器。|  
  
## <a name="see-also"></a>另請參閱  
 [自訂編輯器中的文件資料和文件檢視](../../extensibility/document-data-and-document-view-in-custom-editors.md)

