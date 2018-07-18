---
title: 實作語法著色 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5502bd30378130e5977d427acb9df5b73226a05b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131851"
---
# <a name="implementing-syntax-coloring"></a>實作語法著色
當語言服務提供語法顏色標示時，剖析器將一行文字轉換成色彩項目的陣列，並傳回語彙基元的型別對應至這些色彩的項目。 剖析器應傳回語彙基元的型別屬於色彩的項目清單。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 在程式碼視窗中，根據指派給適當的權杖類型的色彩標示器物件的屬性，會顯示每個色彩的項目。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 未指定的剖析器介面，和剖析器實作是完全由您決定。 不過，預設的剖析器實作是專案所提供的 Visual Studio 語言套件。 Managed 程式碼，managed 的封裝架構 (MPF) 提供完整支援文字的色彩標示。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新方法是使用 MEF 擴充功能。 若要了解有關實作語法著色的新方法的詳細資訊，請參閱[逐步解說： 反白顯示文字](../../extensibility/walkthrough-highlighting-text.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會提升語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>步驟後面來標示的文字編輯器  
  
1.  編輯器 中取得的色彩標示器藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>物件。  
  
2.  編輯器呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>方法，以判斷是否色彩標示器需要的每一行以外的色彩標示器維護狀態。  
  
3.  如果色彩標示器需要以外的色彩標示器維護狀態，編輯器就會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>方法來取得第一個線路的狀態。  
  
4.  緩衝區中的每一行，編輯器會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法，執行下列步驟：  
  
    1.  一行文字會傳遞給掃描器，將文字轉換權杖。 每個語彙基元指定權杖的文字和語彙基元的型別。  
  
    2.  Token 類型會轉換成色彩的項目清單中的索引。  
  
    3.  語彙基元資訊用於填入陣列的陣列的每個項目對應至的行中的字元。 儲存在陣列中的值是為色彩的項目清單中的索引。  
  
    4.  在行結尾處的狀態就會傳回每一行。  
  
5.  如果色彩標示器需要維護狀態，編輯器會快取該線路的狀態。  
  
6.  編輯器 中呈現的文字時，使用從傳回的資訊列<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法。 此時，您需要進行下列步驟：  
  
    1.  取得的行中每個字元，色彩項目的索引。  
  
    2.  如果使用預設的色彩項目，來存取編輯器色彩的項目清單。  
  
    3.  否則，呼叫語言服務<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>方法，以取得色彩的項目。  
  
    4.  使用色彩的項目中的資訊來呈現為顯示的文字。  
  
## <a name="managed-package-framework-colorizer"></a>Managed 的封裝架構色彩標示器  
 Managed 的 package framework (MPF) 提供實作的色彩標示器所需的所有類別。 您的語言服務類別應該繼承<xref:Microsoft.VisualStudio.Package.LanguageService>類別並實作需要的方法。 您必須提供掃描器和剖析器藉由實作<xref:Microsoft.VisualStudio.Package.IScanner>介面，並傳回該介面從執行個體<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法 (其中一個方法中必須實作<xref:Microsoft.VisualStudio.Package.LanguageService>類別)。 如需詳細資訊，請參閱[語法色彩標示在舊版語言服務](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 使用內建的色彩項目](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [自訂色彩項目](../../extensibility/internals/custom-colorable-items.md)   
 [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)