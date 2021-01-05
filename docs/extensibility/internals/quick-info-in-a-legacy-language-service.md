---
title: 舊版語言服務中的快速諮詢 |Microsoft Docs
description: 深入瞭解 IntelliSense 快速諮詢作業的支援，以便顯示識別碼的相關資訊。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 255022c2722104d3790d1c417eee644730ddc1e8
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875072"
---
# <a name="quick-info-in-a-legacy-language-service"></a>舊版語言服務中的快速諮詢
當使用者將插入號放在識別碼中，並從 **IntelliSense** 功能表中選取 [**快速** 諮詢] 或將滑鼠游標停留在識別碼上時，IntelliSense 快速諮詢會顯示來源識別碼的相關資訊。 這會導致工具提示出現，並顯示識別碼的相關資訊。 這項資訊通常包含識別碼類型。 當偵錯工具引擎為使用中時，這項資訊可能會包含目前的值。 Debug engine 提供運算式值，而語言服務只會處理識別碼。

 舊版語言服務會實作為 VSPackage 的一部分，但是執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解，請參閱 [逐步解說：顯示 QuickInfo 工具提示](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md)。

> [!NOTE]
> 建議您儘快開始使用新的編輯器 API。 這可改善您的語言服務效能，並讓您利用新的編輯器功能。

 受控封裝架構 (MPF) 語言服務類別提供完整的支援，以顯示 IntelliSense Quick Info 工具提示。 您只需要提供要顯示的文字，並啟用 [快速諮詢] 功能即可。

 藉由呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 具有剖析原因值的方法剖析器，即可取得要顯示的文字 <xref:Microsoft.VisualStudio.Package.ParseReason> 。 這項原因會指示剖析器取得 (的類型資訊，或是在 [快速諮詢] 工具提示中顯示的內容，在物件中指定之位置的識別碼) <xref:Microsoft.VisualStudio.Package.ParseRequest> 。 <xref:Microsoft.VisualStudio.Package.ParseRequest>物件是傳遞給方法的物件 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 。

 剖析器必須將所有專案剖析到物件中的位置，才能 <xref:Microsoft.VisualStudio.Package.ParseRequest> 判斷所有識別碼的類型。 然後剖析器必須在剖析要求位置取得識別碼。 最後，剖析器必須將與該識別碼相關聯的工具提示資料傳遞給 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 物件，讓物件可以從方法傳回文字 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> 。

## <a name="enabling-the-quick-info-feature"></a>啟用快速諮詢功能
 若要啟用 [快速諮詢] 功能，您必須設定的 `CodeSense` 和 `QuickInfo` 具名引數 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 。這些屬性會設定 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 和 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> 屬性。

## <a name="implementing-the-quick-info-feature"></a>執行快速諮詢功能
 <xref:Microsoft.VisualStudio.Package.ViewFilter>類別會處理 IntelliSense 快速資訊作業。 當 <xref:Microsoft.VisualStudio.Package.ViewFilter> 類別收到命令時 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> ，類別會在 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 命令傳送時，使用的剖析原因 <xref:Microsoft.VisualStudio.Package.ParseReason> 和插入號的位置來呼叫方法 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法剖析器接著必須將來源剖析到指定的位置，然後在指定的位置剖析識別碼，以判斷要在快速諮詢工具提示中顯示的內容。

 大部分的剖析器都會初始剖析整個原始程式檔，並將結果儲存在剖析樹狀結構中。 當傳遞至方法時，就會執行完整的剖析 <xref:Microsoft.VisualStudio.Package.ParseReason> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 。 其他類型的剖析則可以使用剖析樹狀結構來取得所需的資訊。

 例如，的剖析原因值 <xref:Microsoft.VisualStudio.Package.ParseReason> 可以尋找來源位置的識別碼，並在剖析樹狀結構中進行查詢以取得型別資訊。 然後，此型別資訊會傳遞至 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 類別，並由方法傳回 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> 。
