---
title: 自訂色彩的項目 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 690770c2091d3c0a983b91b9a25afc3d3eb4b348
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54974015"
---
# <a name="custom-colorable-items"></a>自訂色彩的項目
您可以覆寫型別的清單標示色彩，例如關鍵字和註解，以及在您的語言服務中實作自訂色彩的項目。  
  
## <a name="user-settings-of-colorable-items"></a>使用者設定的可設定色彩的項目  
 您可以顯示**字型和色彩**對話方塊中，選取**選項**上**工具** 功能表，然後選取**字型和色彩**底下**環境**。 當您選取顯示器，例如**文字編輯器**或是**命令視窗**，則**顯示項目**清單方塊會顯示可顯示的所有色彩項目。 您可以檢視和變更字型、 大小、 前景色彩和每個色彩項目的背景色彩。 您的選擇會儲存在登錄中的快取，然後以可設定色彩的項目名稱存取。  
  
## <a name="presentation-of-colorable-items"></a>可設定色彩的項目呈現方式  
 因為 IDE 會處理的可設定色彩的項目中的使用者覆寫**字型和色彩**對話方塊，您需要只提供每個自訂色彩項目的名稱。 這個名稱是在顯示的內容**顯示的項目**清單。 可設定色彩的項目會依字母順序顯示。 若要將您的語言服務的自訂色彩項目，就可以使用您語言的名稱，每個名稱，例如**NewLanguage-註解**並**NewLanguage-關鍵字**。  
  
> [!CAUTION]
>  您應該避免與現有的色彩項目的名稱發生衝突的色彩項目的名稱包含語言名稱。 如果您變更其中一個您可設定色彩的項目名稱，在開發期間，您必須重設快取建立第一次存取您可設定色彩的項目。 您可以重設實驗性的快取**CreateExpInstance**工具，它會隨 Visual Studio SDK，通常在目錄中：  
>   
>  *C:\Program Files (x86)\Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin*
>   
>  若要重設快取，請輸入**CreateExpInstance /Reset**。 如需詳細資訊**CreateExpInstance**，請參閱[CreateExpInstance utility](../../extensibility/internals/createexpinstance-utility.md)。  
  
 永遠不會參考可設定色彩的項目清單中第一個項目。 第一個項目對應至 0，色彩項目的索引和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]一律會提供預設文字色彩和該項目的屬性。 此未參考的項目處理的最簡單的方式是提供為第一個項目清單中的預留位置色彩項目。  
  
## <a name="implement-custom-colorable-items"></a>實作自訂色彩的項目  
  
1. 定義項目必須以色彩標示您的語言，例如關鍵字、 運算子和識別碼。  
  
2. 建立這些色彩的項目列舉型別。  
  
3. 建立從剖析器或掃描器的列舉值傳回的權杖類型的關聯。  
  
    例如，值，表示語彙基元的型別可能是自訂色彩的項目列舉中的相同值。  
  
4. 在您實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法中的您<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>物件中填入從剖析器或掃描器所傳回的語彙基元型別來對應您自訂色彩的項目列舉值的屬性清單。  
  
5. 在相同的類別可實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>介面，請實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>介面和其兩個方法，<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>。  
  
6. 實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 介面。  
  
7. 如果您想要支援 24 位元或高的色彩值，也會實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>介面。  
  
8. 在您的語言服務物件，會建立清單，其中包含您<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>物件，一個用於您的剖析器或掃描器可以識別每個可設定色彩的項目。  
  
    您可以使用自訂色彩的項目列舉中的對應值，以存取清單中的每個項目。 使用做為索引的列舉值清單。 在清單中的第一個項目永遠不會被存取時，因為它會對應至預設的文字樣式[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]永遠會處理本身。 您可以彌補這一點您清單的開頭插入的預留位置色彩的項目。  
  
9. 在您實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>方法，傳回您自訂色彩的項目清單中的項目數目。  
  
10. 在您實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>方法，傳回要求的色彩項目，從您的清單。  
  
    如需如何實作的範例<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>並<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>介面，請參閱<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>。  
  
## <a name="see-also"></a>另請參閱  
 [舊版語言服務的模型](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [自訂編輯器中的語法著色](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [舊版語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [實作語法著色](../../extensibility/internals/implementing-syntax-coloring.md)   
 [如何：使用內建可設定色彩的項目](../../extensibility/internals/how-to-use-built-in-colorable-items.md)