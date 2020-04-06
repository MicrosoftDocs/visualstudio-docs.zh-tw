---
title: 傳統語言服務中的語句完成 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbeb360cf5bc0f74d6b2d9b93086382dd35da988
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704935"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>舊版語言服務中的陳述式完成
語句完成是語言服務幫助使用者完成他們已開始在核心編輯器中鍵入的語言關鍵字或元素的過程。 本主題討論語句完成的工作原理以及如何在語言服務中實現它。

 舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解有關實現語句完成的新方法的更多,請參閱[演練:顯示語句完成](../../extensibility/walkthrough-displaying-statement-completion.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將提高語言服務的性能,並允許您利用新的編輯器功能。

## <a name="implementing-statement-completion"></a>執行宣告
 在核心編輯器中,語句完成啟動了一個特殊的 UI,該 UI 以互動方式説明您更輕鬆、更快速地編寫代碼。 語句完成有助於在需要時顯示相關物件或類,從而避免記住特定元素或在幫助參考主題中查找它們。

 要實現語句完成,您的語言必須具有語句完成觸發器,可以對其進行分析。 例如,[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]使用點 (.) 運算符[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)],而使用箭頭 (->) 運算符。 語言服務可以使用多個觸發器啟動語句完成。 這些觸發器在命令篩選器中程式設計。

## <a name="command-filters-and-triggers"></a>命令篩選器與觸發器
 命令篩選器可攔截觸發器或觸發器的發生。 要將命令篩選器添加到檢視,請<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>實現介面並通過調用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法將其附加到檢視。 可以對語言服務的所有方面使用相同的命令篩選器<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>( , 例如語句完成、錯誤標記和方法提示)。 有關詳細資訊,請參閱[攔截舊語言服務命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)。

 在編輯器中輸入觸發器時(特別是文本緩衝區),您的語言服務將調用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>該方法。 這將導致編輯器打開 UI,以便用戶可以從語句完成候選項中進行選擇。 此方法要求您實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>和<xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags>標誌作為參數。 完成項目清單會顯示在捲軸清單框中。 當用戶繼續鍵入時,清單框中的選擇將更新以反映與鍵入的最新字元最接近的匹配項。 核心編輯器實現 UI 以完成語句,但語言服務<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>必須實現 介面,為語句定義一組候選完成項。

## <a name="see-also"></a>另請參閱
- [攔截舊版語言服務命令](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
