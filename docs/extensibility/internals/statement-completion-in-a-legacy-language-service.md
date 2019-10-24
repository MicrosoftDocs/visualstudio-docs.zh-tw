---
title: 舊版語言服務中的語句完成 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4c813052892c21a6a3e04560452b503205df117
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723226"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>舊版語言服務中的陳述式完成
語句完成是語言服務協助使用者完成在核心編輯器中輸入的語言關鍵字或元素的程式。 本主題討論語句完成如何運作，以及如何在您的語言服務中加以執行。

 舊版語言服務會實作為 VSPackage 的一部分，但執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要進一步瞭解執行語句完成的新方式，請參閱[逐步解說：顯示語句完成](../../extensibility/walkthrough-displaying-statement-completion.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將可改善語言服務的效能，並可讓您利用新的編輯器功能。

## <a name="implementing-statement-completion"></a>執行語句完成
 在 [核心編輯器] 中，語句完成會啟動特殊的 UI，以互動方式協助您更輕鬆快速地撰寫程式碼。 語句完成會在需要時顯示相關的物件或類別，這可避免您必須記住特定元素，或必須在說明參考主題中查閱這些專案。

 若要執行語句完成，您的語言必須具有可以剖析的語句完成觸發程式。 例如，[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 使用點（.）運算子，而 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 使用箭號（->）運算子。 語言服務可以使用一個以上的觸發程式來起始語句完成。 這些觸發程式是在命令篩選器中進行程式設計。

## <a name="command-filters-and-triggers"></a>命令篩選和觸發程式
 命令篩選器會攔截觸發程式或觸發程式的出現次數。 若要將命令篩選加入至視圖，請執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面，並藉由呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 方法，將它附加至視圖。 您可以針對語言服務的所有層面（例如語句完成、錯誤標記和方法提示）使用相同的命令篩選器（<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>）。 如需詳細資訊，請參閱[攔截舊版語言服務命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)。

 在編輯器中輸入觸發程式（特別是文字緩衝區）時，您的語言服務會接著呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 方法。 這會導致編輯器顯示 UI，讓使用者可以從語句完成候選項目中選擇。 這個方法會要求您將 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> 旗標當做參數來執行。 完成專案清單會出現在 [捲動方塊] 清單方塊中。 當使用者繼續輸入時，清單方塊內的選取範圍會更新，以反映最接近最近所輸入字元的相符專案。 核心編輯器會實作為語句完成的 UI，但是語言服務必須執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 介面，才能為語句定義一組候選的完成專案。

## <a name="see-also"></a>請參閱
- [攔截舊版語言服務命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)