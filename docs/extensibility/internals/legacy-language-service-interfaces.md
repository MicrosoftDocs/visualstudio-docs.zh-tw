---
title: 舊版語言服務介面 |Microsoft Docs
description: 瞭解 Visual Studio SDK 提供舊版語言服務功能的介面。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb694389bbf6f913db084dca29f7787c6283d3ad
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205017"
---
# <a name="legacy-language-service-interfaces"></a>舊版語言服務介面
針對任何特定的程式設計語言，一次只能有一個語言服務的實例。 不過，單一語言服務可以提供一個以上的編輯器。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 不會將語言服務與任何特定編輯器產生關聯。 因此，當您要求語言服務作業時，您必須將適當的編輯器識別為參數。

## <a name="common-interfaces-associated-with-language-services"></a>與語言服務相關聯的通用介面
 編輯器會 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 在適當的 VSPackage 上呼叫，以取得您的語言服務。 在此呼叫中傳遞的服務識別碼 (SID) 會識別所要求的語言服務。

 您可以在任意數目的不同類別上執行核心語言服務介面。 不過，常見的方法是在單一類別中執行下列介面：

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (選擇性)

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>介面必須在所有語言服務上執行。 它會提供語言服務的相關資訊，例如語言的當地語系化名稱、與語言服務相關聯的副檔名，以及如何取出著色器。

## <a name="additional-language-service-interfaces"></a>其他語言服務介面
 您可以使用語言服務來提供其他介面。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 針對每個文字緩衝區實例要求這些介面的個別實例。 因此，您應該在它自己的物件上執行這些介面。 下表顯示每個文字緩衝區實例需要一個實例的介面。

|介面|描述|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|管理程式碼視窗裝飾，例如下拉清單欄。 您可以使用方法來取得這個介面 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> 。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>每個程式碼視窗都有一個。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colorizes 語言關鍵字和分隔符號。 您可以使用方法來取得這個介面 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 會在繪製時呼叫。 避免內部需要大量計算的工作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> ，或效能可能會受到影響。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|提供 IntelliSense 參數工具提示。 當語言服務辨識的字元指出應顯示方法資料時（例如左括弧），它會呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> 方法來通知文字視圖，語言服務已準備好顯示參數資訊工具提示。 然後，文字視圖會使用介面的方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 來取得所需資訊，以顯示工具提示，以回呼語言服務。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|提供 IntelliSense 語句完成。 當語言服務已準備好顯示完成清單時，它會 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 在文字視圖上呼叫該方法。 文字視圖接著會使用物件上的方法，回呼回語言服務 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 。|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|允許使用命令處理常式來修改文字視圖。 您在其中執行介面的類別 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 也必須執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面。 文字視圖 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 會藉由查詢 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 傳遞至方法的物件來抓取物件 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 。 每個視圖應該都有一個 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 物件。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|攔截使用者在程式碼視窗中輸入的命令。 監視您的實作為的輸出 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ，以提供自訂完成資訊和修改視圖<br /><br /> 若要將 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 物件傳遞給文字視圖，請呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 。|

## <a name="see-also"></a>請參閱
- [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)
- [檢查清單：建立舊版語言服務](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
