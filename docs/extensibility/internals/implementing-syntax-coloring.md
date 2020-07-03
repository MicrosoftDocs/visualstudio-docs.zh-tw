---
title: 執行語法著色 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb3f26f59d7cbc994da1d2537e0ab352ce12205e
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905200"
---
# <a name="implementing-syntax-coloring"></a>實作語法著色
當語言服務提供語法顏色標示時，剖析器會將一行文字轉換成可設定色彩專案的陣列，並傳回對應至這些可設定色彩專案的 token 類型。 剖析器應傳回屬於可設定色彩專案清單的 token 類型。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]根據著色器物件指派給適當 token 類型的屬性，在程式碼視窗中顯示每個可設定色彩專案。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]不指定剖析器介面，而且剖析器的實作為完全由您負責。 不過，Visual Studio 語言套件專案中會提供預設剖析器實。 針對 managed 程式碼，managed package framework （MPF）提供上色文字的完整支援。

 舊版語言服務會實作為 VSPackage 的一部分，但執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解如何執行語法著色的新方法，請參閱[逐步解說：反白顯示文字](../../extensibility/walkthrough-highlighting-text.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將可改善語言服務的效能，並可讓您利用新的編輯器功能。

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>後面接著編輯器以著色文字的步驟

1. 編輯器會藉由呼叫物件上的方法來取得著色器 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 。

2. 編輯器 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> 會呼叫方法，以判斷著色器是否需要在著色器外維護每一行的狀態。

3. 如果著色器需要在著色器以外維護狀態，則編輯器會呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> 方法來取得第一行的狀態。

4. 針對緩衝區中的每一行，編輯器會呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 方法，其會執行下列步驟：

    1. 這一行文字會傳遞給掃描器，以將文字轉換為標記。 每個權杖都會指定權杖文字和權杖類型。

    2. Token 類型會轉換成可設定色彩專案清單中的索引。

    3. Token 資訊是用來填入陣列，讓陣列中的每個元素都對應到行中的字元。 儲存在陣列中的值是 [可設定色彩專案] 清單中的索引。

    4. 每一行都會傳回一行結尾的狀態。

5. 如果著色器需要維護狀態，則編輯器會快取該行的狀態。

6. 編輯器會使用從方法傳回的資訊來呈現文字行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 。 此時，您需要進行下列步驟：

    1. 針對一行中的每個字元，取得可設定色彩專案索引。

    2. 如果使用預設的可設定色彩專案，請存取編輯器的 [可設定色彩專案] 清單。

    3. 否則，請呼叫語言服務的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 方法，以取得可設定色彩專案。

    4. 使用可設定色彩專案中的資訊，將文字轉譯成顯示畫面。

## <a name="managed-package-framework-colorizer"></a>Managed Package Framework 著色器
 Managed package framework （MPF）提供了執行著色器所需的所有類別。 您的語言服務類別應該繼承 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別，並執行必要的方法。 您必須藉由執行介面來提供掃描器和剖析器 <xref:Microsoft.VisualStudio.Package.IScanner> ，並從方法傳回該介面的實例 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> （其中一個必須在類別中實作為的方法 <xref:Microsoft.VisualStudio.Package.LanguageService> ）。 如需詳細資訊，請參閱[舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。

## <a name="see-also"></a>另請參閱
- [如何︰使用內建可設定色彩的項目](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [自訂可設定色彩的項目](../../extensibility/internals/custom-colorable-items.md)
- [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)
- [舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
