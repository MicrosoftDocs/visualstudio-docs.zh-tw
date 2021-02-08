---
title: 執行語法著色 |Microsoft Docs
description: 瞭解如何使用 managed package framework (MPF) 的 language service 功能，在 Visual Studio 中執行語法著色。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0ee94326aca31c72ed6c07342707365d16ea57bb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839868"
---
# <a name="implementing-syntax-coloring"></a>實作語法著色
當語言服務提供語法顏色標示時，剖析器會將文字行轉換成可設定色彩專案的陣列，並傳回對應于這些可設定色彩專案的標記類型。 剖析器應該傳回屬於可設定色彩專案清單的 token 類型。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 根據著色器物件指派給適當標記類型的屬性，顯示程式碼視窗中的每個可設定色彩專案。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 不會指定剖析器介面，而且剖析器會完全由您完成。 不過，Visual Studio 語言套件專案中會提供預設的剖析器實作為。 針對 managed 程式碼，受管理的封裝架構 (MPF) 提供標示文字的完整支援。

 舊版語言服務會實作為 VSPackage 的一部分，但是執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解如何執行語法著色的新方法，請參閱 [逐步解說：](../../extensibility/walkthrough-highlighting-text.md)醒目提示文字。

> [!NOTE]
> 建議您儘快開始使用新的編輯器 API。 這可改善您的語言服務效能，並讓您利用新的編輯器功能。

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>步驟，後面接著編輯器來將文字著色

1. 編輯器會 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 在物件上呼叫方法，以取得著色器 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 。

2. 編輯器 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> 會呼叫方法來判斷著色器是否需要在著色器以外維護每一行的狀態。

3. 如果著色器需要在著色器外部維護狀態，編輯器就會呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> 方法以取得第一行的狀態。

4. 編輯器會針對緩衝區中的每一行，呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 方法，執行下列步驟：

    1. 文字行會傳遞至掃描器，以將文字轉換成標記。 每個權杖都會指定標記文字和權杖類型。

    2. Token 型別會轉換成可設定色彩 items 清單中的索引。

    3. 權杖資訊是用來填入陣列，讓陣列的每個元素都對應到該行中的字元。 儲存在陣列中的值是可設定色彩 items 清單中的索引。

    4. 每一行都會傳回該行結尾的狀態。

5. 如果著色器需要維護狀態，編輯器就會快取該行的狀態。

6. 編輯器會使用從方法傳回的資訊來呈現文字行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 。 此時，您需要進行下列步驟：

    1. 針對該行中的每個字元，取得可設定色彩專案索引。

    2. 如果使用預設的可設定色彩專案，請存取編輯器的 [可設定色彩專案] 清單。

    3. 否則，請呼叫語言服務的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 方法來取得可設定色彩專案。

    4. 使用可設定色彩專案中的資訊，將文字轉譯成顯示畫面。

## <a name="managed-package-framework-colorizer"></a>Managed 封裝架構著色器
 受控封裝架構 (MPF) 提供執行著色器所需的所有類別。 您的語言服務類別應該繼承 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別，並執行必要的方法。 您必須藉由執行介面來提供掃描器和剖析器 <xref:Microsoft.VisualStudio.Package.IScanner> ，並從方法傳回該介面的實例， <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> (必須在類別) 中執行的其中一個方法 <xref:Microsoft.VisualStudio.Package.LanguageService> 。 如需詳細資訊，請參閱 [舊版語言服務中的語法標示](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。

## <a name="see-also"></a>另請參閱
- [如何︰使用內建可設定色彩的項目](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [自訂可設定色彩的項目](../../extensibility/internals/custom-colorable-items.md)
- [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)
- [舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
