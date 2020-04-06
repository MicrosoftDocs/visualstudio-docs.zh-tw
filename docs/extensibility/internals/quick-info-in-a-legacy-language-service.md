---
title: 傳統語言服務中的快速資訊 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d070c607313b406f036a5b6f071eaa371070408
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705936"
---
# <a name="quick-info-in-a-legacy-language-service"></a>舊版語言服務中的快速諮詢
IntelliSense 快速資訊顯示有關源中識別符的資訊,當使用者將圖子放在識別符中並從**IntelliSense**選單中選擇 **「快速資訊」** 或將滑鼠游標放在標識符上時。 這將導致工具提示顯示與標識符的資訊。 此資訊通常由標識符類型組成。 當調試引擎處於活動狀態時,此資訊可能包含當前值。 調試引擎提供表達式值,而語言服務僅處理標識碼。

 舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解更多資訊,請參閱[演練:顯示快速資訊工具提示](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將提高語言服務的性能,並允許您利用新的編輯器功能。

 託管包框架 (MPF) 語言服務類為顯示 IntelliSense 快速資訊工具提示提供完全支援。 所有你需要做的是提供要顯示的文本,並啟用快速資訊功能。

 要顯示的文字是透過呼叫具有分析原因值<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>的方法解析器取得<xref:Microsoft.VisualStudio.Package.ParseReason>的 。 此原因告訴解析器在<xref:Microsoft.VisualStudio.Package.ParseRequest>物件中指定的位置獲取標識符的類型資訊(或任何適合顯示在"快速資訊"工具提示中顯示的資訊)。 對<xref:Microsoft.VisualStudio.Package.ParseRequest>象是傳遞給方法<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>的內容 。

 解析器必須解析到<xref:Microsoft.VisualStudio.Package.ParseRequest>物件中位置的所有內容,以確定所有標識符的類型。 然後,解析器必須在解析請求位置獲取標識符。 最後,解析器必須將與此識別符關聯的工具提示數據傳遞給<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件,以便物件可以<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A>從 方法返回文本。

## <a name="enabling-the-quick-info-feature"></a>開啟快速資訊功能
 要啟用「快速資訊」功能,必須設定`CodeSense`與`QuickInfo`命名的參數<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>。這些屬性設置<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>和<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A>屬性。

## <a name="implementing-the-quick-info-feature"></a>實現快速資訊功能
 該<xref:Microsoft.VisualStudio.Package.ViewFilter>類處理"IntelliSense 快速資訊"操作。 <xref:Microsoft.VisualStudio.Package.ViewFilter>當類<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>接收命令時,類調<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>用 方法時具有<xref:Microsoft.VisualStudio.Package.ParseReason>解析的原因 和<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>命令發送時 的 caret 的位置。 然後<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>,方法解析器必須將源解析為給定位置,然後在給定位置解析標識符,以確定在"快速資訊"工具提示中顯示的內容。

 大多數解析器對整個源檔進行初始分析,並將結果存儲在解析樹中。 當傳遞給<xref:Microsoft.VisualStudio.Package.ParseReason><xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法時,將執行完整的分析。 然後,其他類型的分析可以使用解析樹來獲取所需的資訊。

 例如,的<xref:Microsoft.VisualStudio.Package.ParseReason>解析原因值可以在源位置找到標識符,並在解析樹中查找它以獲取類型資訊。 然後,將此類型信息傳遞給<xref:Microsoft.VisualStudio.Package.AuthoringScope>類,並由<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A>方法返回。
