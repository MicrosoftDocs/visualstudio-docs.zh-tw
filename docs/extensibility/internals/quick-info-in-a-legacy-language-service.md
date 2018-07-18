---
title: 在舊版語言服務的快速諮詢 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: ffdfe9bfb9063828a90dd9cdf3452ca3684ff0a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132145"
---
# <a name="quick-info-in-a-legacy-language-service"></a>在舊版語言服務的快速諮詢
IntelliSense 快速諮詢 會顯示在來源中的識別項的相關資訊時使用者識別項中將插入號，選取**快速諮詢**從**IntelliSense**功能表或保存滑鼠資料指標的識別碼上方。 這會導致識別項的相關資訊會出現工具提示。 這項資訊通常包含識別項類型。 使用偵錯引擎時，這項資訊可能包含目前的值。 語言服務會處理只有識別碼時，偵錯引擎會提供運算式值。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新方法是使用 MEF 擴充功能。 若要深入了解，請參閱[逐步解說： 顯示 QuickInfo 工具提示](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會提升語言服務的效能，並可讓您充分利用新編輯器功能。  
  
 Managed 的封裝架構 (MPF) 語言服務類別顯示 IntelliSense 快速諮詢工具提示提供完整支援。 您只需要為提供的文字會顯示並啟用 [快速諮詢] 功能。  
  
 要顯示的文字透過呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法剖析器剖析原因值是<xref:Microsoft.VisualStudio.Package.ParseReason>。 因此會告知剖析器，以取得類型資訊 （或任何適合的快速諮詢工具提示中顯示） 中指定的位置識別碼<xref:Microsoft.VisualStudio.Package.ParseRequest>物件。 <xref:Microsoft.VisualStudio.Package.ParseRequest>物件是內容傳遞給<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法。  
  
 剖析器必須剖析所有項目中的位置到<xref:Microsoft.VisualStudio.Package.ParseRequest>物件，以判斷所有識別項的類型。 然後剖析器必須在剖析要求位置取得的識別項。 最後，剖析器必須傳遞至該識別項相關聯的工具提示資料<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件，該物件可傳回從文字以便<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A>方法。  
  
## <a name="enabling-the-quick-info-feature"></a>啟用 [快速諮詢] 功能  
 若要啟用 [快速諮詢] 功能，您必須設定`CodeSense`和`QuickInfo`的具名參數<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>。設定這些屬性<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>和<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A>屬性。  
  
## <a name="implementing-the-quick-info-feature"></a>實作快速諮詢  
 <xref:Microsoft.VisualStudio.Package.ViewFilter>類別處理 IntelliSense 快速諮詢作業。 當<xref:Microsoft.VisualStudio.Package.ViewFilter>類別接收<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>命令，類別會呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法以剖析原因的<xref:Microsoft.VisualStudio.Package.ParseReason>和次插入號位置<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>已傳送命令。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法剖析器必須剖析到指定位置的來源和剖析的識別項來決定要顯示在 快速諮詢工具提示中指定的位置。  
  
 大部分的剖析器的整個原始程式檔的初始剖析作業，並將結果儲存在剖析樹狀目錄。 完整剖析實行時<xref:Microsoft.VisualStudio.Package.ParseReason>傳遞至<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法。 其他類型的剖析然後可以使用剖析樹狀目錄來取得所需的資訊。  
  
 例如，剖析原因值<xref:Microsoft.VisualStudio.Package.ParseReason>才能找到的識別項的來源位置，以及查閱在剖析樹狀目錄中取得類型資訊。 此類型資訊會傳遞至<xref:Microsoft.VisualStudio.Package.AuthoringScope>類別，並傳回<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A>方法。