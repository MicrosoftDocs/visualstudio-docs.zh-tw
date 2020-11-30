---
title: 自訂可設定色彩專案 |Microsoft Docs
description: 瞭解如何藉由覆寫 [字型和色彩] 對話方塊中的專案（例如關鍵字和批註）來建立自訂可設定色彩專案做為語言服務的一部分。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 648a8e45b5b472ccc1a37cd69e2043f0bb5b9aa3
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328531"
---
# <a name="custom-colorable-items"></a>自訂可設定色彩專案
您可以藉由將自訂可設定色彩專案實作為語言服務的一部分，來覆寫標示的類型清單，例如關鍵字和批註。

## <a name="user-settings-of-colorable-items"></a>可設定色彩專案的使用者設定
 您可以藉由選取 [**工具**] 功能表上的 **[選項**]，然後選取 [**環境**] 下的 [字型 **和色彩**]，來顯示 [字型 **和色彩**] 對話方塊。 當您選取顯示（例如 **文字編輯器** 或 **命令視窗**）時，[ **顯示專案** ] 清單方塊會顯示該顯示專案的所有可設定色彩專案。 您可以針對每個可設定色彩專案來查看和變更字型、大小、前景色彩和背景色彩。 您的選擇會儲存在登錄中的快取中，並由可設定色彩專案名稱存取。

## <a name="presentation-of-colorable-items"></a>可設定色彩專案的簡報
 因為 IDE 會在 [字型 **和色彩** ] 對話方塊中處理可設定色彩專案的使用者覆寫，所以您只需要為每個自訂可設定色彩專案提供名稱。 此名稱會顯示在 [ **顯示專案** ] 清單中。 可設定色彩專案會依字母順序顯示。 若要將語言服務的自訂可設定色彩專案分組，您可以使用您的語言名稱來開始每個名稱，例如 **NewLanguage-Comment** 和 **NewLanguage 關鍵字**。

> [!CAUTION]
> 您應在可設定色彩專案名稱中包含語言名稱，以避免與現有的可設定色彩專案名稱發生衝突。 如果您在開發期間變更其中一個可設定色彩專案的名稱，則必須重設第一次存取可設定色彩專案時所建立的快取。 您可以使用 **CreateExpInstance** 工具（通常是在目錄中）來重設實驗性快取，該工具會隨 Visual Studio SDK 一起安裝：
>
> *C:\Program Files (x86) \Microsoft Visual Studio 14.0 \ VSSDK\VisualStudioIntegration\Tools\Bin*
>
> 若要重設快取，請輸入 **CreateExpInstance/Reset**。 如需 **CreateExpInstance** 的詳細資訊，請參閱 [CreateExpInstance 公用程式](../../extensibility/internals/createexpinstance-utility.md)。

 永遠不會參考可設定色彩專案清單中的第一個專案。 第一個專案對應至可設定色彩專案索引0，而且 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 一律會提供該專案的預設文字色彩和屬性。 處理這個未參考專案的最簡單方式，就是在清單中提供預留位置可設定色彩專案做為第一個專案。

## <a name="implement-custom-colorable-items"></a>執行自訂可設定色彩專案

1. 定義必須以您的語言以色彩標示的內容，例如關鍵字、運算子和識別碼。

2. 建立這些可設定色彩專案的列舉。

3. 將從剖析器或掃描器傳回的 token 類型與列舉值產生關聯。

    例如，代表標記類型的值可能是自訂可設定色彩專案列舉中的相同值。

4. 在您 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 物件的方法中 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> ，使用自訂可設定色彩專案列舉中的值，將對應至剖析器或掃描器所傳回之 token 類型的值填入屬性清單。

5. 在與介面相同的類別中 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> ，執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 介面和它的兩個方法， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> 以及 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 。

6. 實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 介面。

7. 如果您想要支援24位或高彩值，也請執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 介面。

8. 在您的語言服務物件中，建立包含您物件的清單 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> ，您的剖析器或掃描器可以識別的每個可設定色彩專案各一個。

    您可以使用自訂可設定色彩專案列舉中的對應值，來存取清單中的每個專案。 使用列舉值做為清單中的索引。 清單中的第一個專案永遠不會被存取，因為它會對應至一律處理本身的預設文字樣式 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 您可以在清單的開頭插入預留位置可設定色彩專案來彌補這一點。

9. 在方法的執行中 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> ，傳回自訂可設定色彩專案清單中的專案數。

10. 在方法的執行中 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> ，從您的清單傳回要求的可設定色彩專案。

    如需如何執行和介面的範例 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> ，請參閱 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 。

## <a name="see-also"></a>另請參閱
- [舊版語言服務的模型](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [自訂編輯器中的語法著色](../../extensibility/syntax-coloring-in-custom-editors.md)
- [舊版語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [執行語法著色](../../extensibility/internals/implementing-syntax-coloring.md)
- [如何：使用內建的可設定色彩專案](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
