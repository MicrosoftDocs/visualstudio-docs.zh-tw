---
title: 舊版語言服務中的語句完成 |Microsoft Docs
description: 瞭解語句完成的運作方式，以及如何在 VSPackage 的舊版語言服務中加以執行。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 63a784c850f4c88ecf17a978a2943577eb988a7b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080771"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>舊版語言服務中的陳述式完成
語句完成是語言服務協助使用者完成其在核心編輯器中開始輸入的語言關鍵字或元素的程式。 本主題討論語句完成的運作方式，以及如何在您的語言服務中加以執行。

 舊版語言服務會實作為 VSPackage 的一部分，但是執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解如何執行語句完成的新方法，請參閱 [逐步解說：顯示語句完成](../../extensibility/walkthrough-displaying-statement-completion.md)。

> [!NOTE]
> 建議您儘快開始使用新的編輯器 API。 這可改善您的語言服務效能，並讓您利用新的編輯器功能。

## <a name="implementing-statement-completion"></a>執行語句完成
 在核心編輯器中，語句完成會啟動特殊的 UI，以互動方式協助您更輕鬆快速地撰寫程式碼。 語句完成可協助您在需要時顯示相關的物件或類別，這可避免您必須記住特定的元素，或必須在說明參考主題中查閱。

 若要執行語句完成，您的語言必須有可剖析的語句完成觸發程式。 例如， [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 使用點 (. ) 運算子，但 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 使用箭號 ( >) 運算子。 語言服務可以使用一個以上的觸發程式來起始語句完成。 這些觸發程式是在命令篩選器中進行程式設計。

## <a name="command-filters-and-triggers"></a>命令篩選器和觸發程式
 命令篩選器會攔截觸發程式或觸發程式的出現次數。 若要將命令篩選加入至視圖，請透過 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 呼叫方法來執行介面，並將它附加至 view <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 。 您可以 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 針對語言服務的所有層面（例如語句完成、錯誤標記和方法提示），使用相同的命令篩選器 () 。 如需詳細資訊，請參閱 [攔截舊版語言服務命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)。

 在編輯器中輸入觸發程式（尤其是文字緩衝區）時，您的語言服務就會呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 方法。 這會導致編輯器顯示 UI，讓使用者可以從語句完成候選項目中選擇。 這個方法會要求您將 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 和 <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> 旗標作為參數來執行。 完成專案的清單會出現在滾動清單方塊中。 當使用者繼續鍵入時，清單方塊內的選取專案會更新，以反映最接近輸入最新字元的相符專案。 核心編輯器會執行語句完成的 UI，但語言服務必須執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 介面，以定義語句的一組候選完成專案。

## <a name="see-also"></a>另請參閱
- [攔截舊版語言服務命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
