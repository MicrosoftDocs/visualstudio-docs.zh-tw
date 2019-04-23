---
title: 實作語法著色 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d2b47598e4102eefaa671fd5f362975aae0f4d53
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059809"
---
# <a name="implementing-syntax-coloring"></a>實作語法著色
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

當語言服務會提供語法顏色標示時、 剖析器將一行文字轉換成陣列的可設定色彩的項目，並傳回語彙基元的型別對應至這些色彩的項目。 剖析器應該會傳回屬於可設定色彩的項目清單的語彙基元型別。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 根據色彩標示器物件指派給適當的語彙基元型別屬性的程式碼 視窗中顯示每個可設定色彩的項目。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 未指定剖析器介面，和剖析器實作是完全由您決定。 不過，Visual Studio 語言套件專案提供預設的剖析器實作。 Managed 程式碼，managed 的封裝架構 (MPF) 提供了完整支援以色彩標示文字。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新的方式是使用 MEF 擴充功能。 若要深入了解實作語法著色的新方式，請參閱[逐步解說：反白顯示文字](../../extensibility/walkthrough-highlighting-text.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 盡。 這會改善您的語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>若要以色彩標示文字編輯器所遵循步驟  
  
1. 編輯器取得色彩標示器藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>物件。  
  
2. 編輯器呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A>方法，以判斷色彩標示器是否需要在每個線條的色彩標示器外部維護的狀態。  
  
3. 如果色彩標示器需要外部的色彩標示器維護狀態，編輯器便會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A>方法來取得狀態的第一行。  
  
4. 緩衝區中每一行，編輯器會呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法，執行下列步驟：  
  
    1. 文字的一行會傳遞至掃描器，將文字轉換成語彙基元。 每個語彙基元指定權杖的文字與語彙基元的型別。  
  
    2. 語彙基元的型別會轉換成可設定色彩的項目 清單中的索引。  
  
    3. 權杖的資訊用來填入陣列，陣列的每個項目對應至的行中的字元。 儲存在陣列中的值是可設定色彩的項目清單索引。  
  
    4. 在行結尾處的狀態就會傳回每一行。  
  
5. 如果色彩標示器需要維護狀態，編輯器會快取該線路的狀態。  
  
6. 編輯器會呈現的文字時，使用從傳回的資訊列<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>方法。 此時，您需要進行下列步驟：  
  
    1. 取得行中每個字元，可設定色彩的項目索引。  
  
    2. 如果使用的預設色彩的項目，來存取編輯器色彩的項目清單。  
  
    3. 否則，呼叫的語言服務的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>方法，以取得可設定色彩的項目。  
  
    4. 使用可設定色彩的項目中的資訊來呈現文字的顯示畫面。  
  
## <a name="managed-package-framework-colorizer"></a>Managed 的 Package Framework 色彩標示器  
 Managed 的 package framework (MPF) 提供實作的色彩標示器所需的所有類別。 您的語言服務類別應該繼承<xref:Microsoft.VisualStudio.Package.LanguageService>類別並實作所需的方法。 您必須提供掃描器和剖析器藉由實作<xref:Microsoft.VisualStudio.Package.IScanner>介面，並傳回該介面的執行個體<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法 (其中一個方法必須實作在<xref:Microsoft.VisualStudio.Package.LanguageService>類別)。 如需詳細資訊，請參閱 <<c0> [ 舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何：使用內建可設定色彩的項目](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [自訂色彩的項目](../../extensibility/internals/custom-colorable-items.md)   
 [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
