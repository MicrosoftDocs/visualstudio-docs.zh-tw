---
title: 在舊版語言服務中的陳述式完成 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d76face8f43bcb428a9c3b997083f8299d332cc8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="statement-completion-in-a-legacy-language-service"></a>在舊版語言服務中的陳述式完成
陳述式完成是語言服務用來協助完成語言關鍵字或項目，在開始核心編輯器中輸入使用者的程序。 本主題討論陳述式完成的運作方式，以及如何實作語言服務中。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新方法是使用 MEF 擴充功能。 若要了解有關實作陳述式完成的新方法的詳細資訊，請參閱[逐步解說： 顯示陳述式完成](../../extensibility/walkthrough-displaying-statement-completion.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會提升語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="implementing-statement-completion"></a>實作陳述式完成  
 在核心編輯器中，陳述式完成啟動特殊的 UI 以互動方式可幫助您更輕鬆且快速地撰寫程式碼。 陳述式完成可協助藉由顯示相關的物件或類別在需要時，以避免您在需要記住的特定項目或無它們查閱說明參考主題。  
  
 若要實作陳述式完成，您的語言必須有陳述式完成觸發程序，可以剖析的。 例如，[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]會使用點 （.） 運算子，而[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]使用箭號 (->) 運算子。 語言服務可以使用多個觸發程序來起始陳述式完成。 這些觸發程序進行程式設計命令篩選器中。  
  
## <a name="command-filters-and-triggers"></a>命令篩選器和觸發程序  
 命令的篩選條件攔截您的觸發程序或觸發程序的次數。 若要將命令篩選器加入至檢視中，實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面，並將它附加到檢視中，藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法。 您可以使用相同的命令篩選器 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) 之語言服務，例如陳述式完成、 錯誤的標記，以及方法提示的所有層面。 如需詳細資訊，請參閱[攔截舊版語言服務命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)。  
  
 在編輯器中輸入該觸發程序時，特別是，文字緩衝區 — 語言服務然後呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>方法。 這會導致啟動 UI，讓使用者可以選擇從陳述式完成的候選項目編輯器。 此方法需要您實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>和<xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags>做為參數的旗標。 捲動清單方塊中顯示的完成項目清單。 當使用者繼續輸入，在清單方塊選取項目會更新以反映最符合的最新的字元類型。 核心編輯器實作陳述式完成的 UI，但語言服務必須實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>介面來定義一組候選陳述式的完成項目。  
  
## <a name="see-also"></a>另請參閱  
 [攔截舊版語言服務命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)