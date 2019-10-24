---
title: 舊版語言服務介面 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 065ef972709ca78b516a9acc5f4a737d2963e4b7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726851"
---
# <a name="legacy-language-service-interfaces"></a>舊版語言服務介面
針對任何特定的程式設計語言，一次只能有一個語言服務的實例。 不過，單一語言服務可以提供一個以上的編輯器。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 不會使語言服務與任何特定編輯器產生關聯。 因此，當您要求語言服務作業時，您必須將適當的編輯器識別為參數。

## <a name="common-interfaces-associated-with-language-services"></a>與語言服務相關聯的通用介面
 編輯器會藉由在適當的 VSPackage 上呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>，來取得您的語言服務。 傳入此呼叫的服務識別碼（SID）會識別所要求的語言服務。

 您可以在任意數目的個別類別上，執行核心語言服務介面。 不過，常見的方法是在單一類別中執行下列介面：

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (選擇性)

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 介面必須在所有語言服務上執行。 它會提供您語言服務的相關資訊，例如語言的當地語系化名稱、與語言服務相關聯的副檔名，以及如何取出著色器。

## <a name="additional-language-service-interfaces"></a>其他語言服務介面
 其他介面可與您的語言服務一起提供。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會針對每個文本緩衝區實例，要求這些介面的個別實例。 因此，您應該在自己的物件上，執行每個介面。 下表顯示每個文字緩衝區實例需要一個實例的介面。

|介面|描述|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|管理程式碼視窗裝飾，例如下拉式列。 您可以使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> 方法來取得此介面。 每個程式碼視窗都有一個 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colorizes 語言關鍵字和分隔符號。 您可以使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 方法來取得此介面。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 會在繪製時呼叫。 避免在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 或效能可能造成的計算密集型工作。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|提供 IntelliSense 參數工具提示。 當語言服務辨識出指出應該顯示方法資料的字元（例如左括弧）時，它會呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> 方法，以通知文本視圖語言服務已準備好顯示參數資訊工具提示。 然後，文字視圖會使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 介面的方法來取得顯示工具提示所需的資訊，然後再呼叫語言服務。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|提供 IntelliSense 語句完成。 當語言服務準備好要顯示完成清單時，它會在文字視圖上呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 方法。 然後，文字視圖會使用 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 物件上的方法來回呼語言服務。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|允許使用命令處理常式修改文本視圖。 您在其中執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 介面的類別，也必須執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面。 文字視圖會藉由查詢傳遞至 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 方法的 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 物件，來抓取 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 物件。 每個視圖應該都有一個 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 物件。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|攔截使用者在程式碼視窗中輸入的命令。 監視 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 執行的輸出，以提供自訂完成資訊和修改視圖<br /><br /> 若要將您的 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 物件傳遞至文字視圖，請呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>。|

## <a name="see-also"></a>請參閱
- [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)
- [檢查清單︰建立舊版語言服務](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)