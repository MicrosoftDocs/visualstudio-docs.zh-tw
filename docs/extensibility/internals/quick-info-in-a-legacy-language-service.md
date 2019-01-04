---
title: 舊版語言服務中的快速諮詢 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8bba57c0a069f515f29e02ec712e3cce7d457f95
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53908761"
---
# <a name="quick-info-in-a-legacy-language-service"></a>舊版語言服務中的快速諮詢
IntelliSense 快速諮詢會顯示來源中的識別項的相關資訊時，使用者將插入號放在識別項，並選取**快速諮詢**從**IntelliSense**功能表或保留滑鼠資料指標的識別碼上方。 這會導致識別碼的相關資訊會出現工具提示。 這項資訊通常包括識別項型別。 作用中的偵錯引擎時，這項資訊可能包含目前的值。 語言服務處理只有識別碼項目時，偵錯引擎會提供運算式值。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新的方式是使用 MEF 擴充功能。 若要深入了解，請參閱[逐步解說：顯示 QuickInfo 工具提示](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 盡。 這會改善您的語言服務的效能，並可讓您充分利用新編輯器功能。  
  
 Managed 的封裝架構 (MPF) 語言服務類別會提供完整的支援，顯示 IntelliSense 快速諮詢工具提示。 您必須執行的只是提供文字顯示，並啟用快速諮詢功能。  
  
 要顯示的文字由呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法的剖析器剖析原因值是<xref:Microsoft.VisualStudio.Package.ParseReason>。 因此會告知剖析器來取得類型資訊 （或任何適合的快速諮詢工具提示中顯示） 中指定的位置識別碼<xref:Microsoft.VisualStudio.Package.ParseRequest>物件。 <xref:Microsoft.VisualStudio.Package.ParseRequest>物件是內容傳遞給<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法。  
  
 剖析器必須剖析至的位置中的所有項目<xref:Microsoft.VisualStudio.Package.ParseRequest>物件來判斷所有的識別項的類型。 然後，剖析器必須剖析要求的位置取得的識別碼。 最後，剖析器必須傳遞至該識別項相關聯的工具提示資料<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件，該物件可以傳回從文字以便<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A>方法。  
  
## <a name="enabling-the-quick-info-feature"></a>啟用快速諮詢功能  
 若要啟用快速諮詢功能，您必須設定`CodeSense`並`QuickInfo`具名參數的<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>。設定這些屬性<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>和<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A>屬性。  
  
## <a name="implementing-the-quick-info-feature"></a>實作快速諮詢功能  
 <xref:Microsoft.VisualStudio.Package.ViewFilter>類別處理在 IntelliSense 快速諮詢 」 作業。 時<xref:Microsoft.VisualStudio.Package.ViewFilter>類別會收到<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>命令，類別會呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法的剖析原因<xref:Microsoft.VisualStudio.Package.ParseReason>並在插入號位置<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>已傳送命令。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法的剖析器必須再剖析到指定的位置來源，並再剖析的識別項，以決定要顯示在 快速諮詢工具提示中指定的位置。  
  
 大部分的剖析器會執行整個原始程式檔的初始剖析，並將結果儲存在剖析樹狀結構中。 完整剖析執行時<xref:Microsoft.VisualStudio.Package.ParseReason>傳遞至<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法。 其他種類的剖析然後可以使用剖析樹狀結構，以取得所需的資訊。  
  
 例如，剖析原因值<xref:Microsoft.VisualStudio.Package.ParseReason>可以找到來源位置識別碼和查閱在剖析樹狀目錄中取得類型資訊。 此類型資訊會傳遞至<xref:Microsoft.VisualStudio.Package.AuthoringScope>類別，並傳回<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A>方法。