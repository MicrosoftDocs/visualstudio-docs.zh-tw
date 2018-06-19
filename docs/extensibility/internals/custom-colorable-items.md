---
title: 自訂色彩項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b23ff39abcb9a1354ea28becab3b7df867378ddf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133368"
---
# <a name="custom-colorable-items"></a>自訂色彩項目
您可以覆寫類型的清單上色功能，例如關鍵字以及註解、 實作自訂色彩項目做為語言服務的一部分。  
  
## <a name="user-settings-of-colorable-items"></a>使用者設定的色彩項目  
 您可以顯示**字型和色彩**對話方塊選取**選項**上**工具**] 功能表，然後選取 [**字型和色彩**在下**環境**。 當您選取顯示，例如**文字編輯器**或**命令視窗**、**顯示項目**清單方塊會顯示該顯示的所有色彩項目。 您可以檢視和變更字型、 大小、 前景色彩和每個色彩項目的背景色彩。 您選擇儲存在登錄中快取，然後依色彩項目的名稱存取。  
  
## <a name="presentation-of-colorable-items"></a>展示檔的色彩項目  
 因為 IDE 會處理使用者覆寫中的色彩項目的**字型和色彩**對話方塊，您需要只提供每個自訂色彩項目的名稱。 此名稱都會顯示於**顯示項目**清單。 依字母順序顯示色彩的項目。 語言服務的自訂色彩項目分組，您就可以開始使用您語言的名稱，每個名稱，例如**NewLanguage-註解**和**NewLanguage-關鍵字**。  
  
> [!CAUTION]
>  您應該避免與現有的色彩項目的名稱衝突的色彩項目的名稱包含語言名稱。 如果您在開發期間變更其中一個色彩的項目名稱，您必須重設快取建立您可設定色彩的項目可供存取的第一次。 您可以重設使用 CreateExpInstance 工具，它會隨 Visual Studio SDK，通常在目錄中的實驗性快取  
>   
>  **C:\Program 檔案 (x86) \Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
>  若要重設快取，請呼叫`CreateExpInstance /Reset`。 如需 CreateExpInstance 的詳細資訊，請參閱[CreateExpInstance 公用程式](../../extensibility/internals/createexpinstance-utility.md)。  
  
 永遠不會參考色彩的項目清單中的第一個項目。 第一個項目會對應到色彩項目的索引為 0，和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]一律會提供的預設文字色彩及該項目的屬性。 這個未參考的項目處理的最簡單的方式是提供做為第一個項目清單中的預留位置色彩項目。  
  
## <a name="implementing-custom-colorable-items"></a>實作自訂色彩項目  
  
1.  定義什麼必須會以色彩標示您的語言，例如關鍵字、 運算子和識別項。  
  
2.  建立這些色彩項目的列舉。  
  
3.  建立關聯的剖析器或掃描器的列舉值傳回的權杖類型。  
  
     例如，代表語彙基元類型的值可能是自訂色彩項目列舉中的相同值。  
  
4.  在您實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法在您<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>物件中填入從掃描器或剖析器傳回的權杖型別對應自訂色彩項目列舉值的屬性清單。  
  
5.  在相同類別可實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>介面，實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>介面和其兩個方法，<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>。  
  
6.  實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 介面。  
  
7.  如果您想要支援 24 位元或高色彩值，也會實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>介面。  
  
8.  在您語言的服務物件，會建立清單，其中包含您<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>物件、 一個用於您的剖析器或掃描器可以識別每個色彩的項目。  
  
     您可以使用自訂色彩項目列舉中的對應值，以存取清單中的每個項目。 使用做為索引的列舉值的清單中。 永遠不會存取清單中的第一個項目，因為它會對應至預設的文字設定樣式[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]永遠會處理本身。 您可以藉由在清單的開頭插入預留位置色彩項目的補償這個。  
  
9. 在您實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>方法，傳回自訂色彩項目清單中的項目數。  
  
10. 在您實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>方法，傳回要求的色彩項目從您的清單。  
  
 如需如何實作的範例<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>介面，請參閱<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>。  
  
## <a name="see-also"></a>另請參閱  
 [舊版語言服務模型](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [自訂編輯器中著色的語法](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [使用語法色彩編碼舊版語言服務](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [實作語法著色](../../extensibility/internals/implementing-syntax-coloring.md)   
 [如何︰使用內建可設定色彩的項目](../../extensibility/internals/how-to-use-built-in-colorable-items.md)