---
title: 實現語法著色 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 83ce66dd6a31e3ef852feb91e2ba304e6688a723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707639"
---
# <a name="implementing-syntax-coloring"></a>實作語法著色
當語言服務提供語法著色時,解析器會將文本行轉換為可著色項陣列,並返回對應於這些可著色項的權杖類型。 解析器應返回屬於可著色項清單的權杖類型。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]根據著色器物件分配給相應權杖類型的屬性,在代碼視窗中顯示每個可著色項。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]不指定解析器介面,解析器實現完全由您決定。 但是,在可視化工作室語言包專案中提供了預設解析器實現。 對於託管代碼,託管包框架 (MPF) 提供對文本著色的完全支援。

 舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解有關實現語法著色的新方法的更多,請參閱[演練:突出顯示文本](../../extensibility/walkthrough-highlighting-text.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將提高語言服務的性能,並允許您利用新的編輯器功能。

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>步驟後跟由編輯器著色文字

1. 編輯器通過在<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A><xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>物件上調用方法來獲取著色器。

2. 編輯器呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>該方法以確定著色器是否需要在著色器外部維護每行的狀態。

3. 如果著色器要求在著色器外部保持狀態,則編輯器調用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>方法以獲取第一行的狀態。

4. 對於緩衝區中的每一行,編輯器調用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法,該方法執行以下步驟:

    1. 文字行將傳遞到掃描器,以將文字轉換為標記。 每個權杖指定權杖和權杖類型。

    2. 令牌類型將轉換為可著色項清單。

    3. 令牌資訊用於填充陣列,以便陣列的每個元素對應於行中的字元。 陣列中儲存的值是可著色項清單中的索引。

    4. 每行返回行末尾的狀態。

5. 如果著色器要求維護狀態,編輯器將緩存該行的狀態。

6. 編輯器使用從<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法返回的資訊呈現文本行。 此時，您需要進行下列步驟：

    1. 對於行中的每個字元,獲取可著色項索引。

    2. 如果使用預設的可著色項,則訪問編輯器的可著色項清單。

    3. 否則,調用語言服務<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>的方法以獲取可著色項。

    4. 使用可著色項中的資訊將文本呈現到顯示幕中。

## <a name="managed-package-framework-colorizer"></a>託管套件框架著色器
 託管包框架 (MPF) 提供實現著色器所需的所有類。 您的語言服務類應繼承該<xref:Microsoft.VisualStudio.Package.LanguageService>類並實現所需的方法。 必須通過實現<xref:Microsoft.VisualStudio.Package.IScanner>介面來提供掃描器和解析器,並<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>從方法返回該介面的實例(必須<xref:Microsoft.VisualStudio.Package.LanguageService>在類中實現的方法之一)。 有關詳細資訊,請參閱[舊語言服務中的語法著色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。

## <a name="see-also"></a>另請參閱
- [如何︰使用內建可設定色彩的項目](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [自訂可設定色彩的項目](../../extensibility/internals/custom-colorable-items.md)
- [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)
- [舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
