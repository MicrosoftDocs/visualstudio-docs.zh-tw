---
title: 舊版語言服務剖析器和掃描器 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b172fee8f6f5cf1c80d306a8a8b154f7316bf8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726730"
---
# <a name="legacy-language-service-parser-and-scanner"></a>舊版語言服務的剖析器和掃描器
剖析器是語言服務的核心。 Managed Package Framework （MPF）語言類別需要語言剖析器，以選取要顯示之程式碼的相關資訊。 剖析器會將文字分隔成詞法標記，然後依類型和功能來識別這些標記。

## <a name="discussion"></a>討論
 下列是C#方法。

```csharp
namespace MyNamespace
{
    class MyClass
    {
        public void MyFunction(int arg1)
        {
            int var1 = arg1;
        }
    }
}
```

 在此範例中，標記為單字和標點符號。 標記的類型如下所示。

|權杖名稱|語彙基元類型|
|----------------|----------------|
|namespace、class、public、void、int|keyword|
|=|運算子|
|{ } ( ) ;|為止|
|MyNamespace、MyClass、MyFunction、arg1、var1|識別碼 (identifier)|
|MyNamespace|namespace|
|MyClass|Class - 類別|
|MyFunction|方法|
|arg1|參數 (parameter)|
|var1|區域變數|

 剖析器的角色是用來識別權杖。 某些權杖可以有一個以上的類型。 剖析器識別出標記之後，語言服務就可以使用此資訊來提供有用的功能，例如語法醒目提示、括弧對稱和 IntelliSense 作業。

## <a name="types-of-parsers"></a>剖析器的類型
 語言服務剖析器與用來做為編譯器一部分的剖析器不同。 不過，這種剖析器必須使用掃描器和剖析器，其方式與編譯器剖析器相同。

- 掃描器是用來識別權杖的類型。 此資訊用於反白顯示語法，以及快速識別可觸發其他作業的 token 類型，例如，括弧對稱。 此掃描器是以 <xref:Microsoft.VisualStudio.Package.IScanner> 介面表示。

- 剖析器是用來描述權杖的函式和範圍。 這項資訊會在 IntelliSense 作業中用來識別語言元素，例如方法、變數、參數和宣告，並根據內容提供成員和方法簽章的清單。 這個剖析器也會用來尋找相符的語言元素組，例如大括弧和括弧。 這個剖析器是透過 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別中的 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法來存取。

  您可以自行決定如何為您的語言服務執行掃描器和剖析器。 有數個資源可用來描述剖析器的運作方式，以及如何撰寫您自己的剖析器。 此外，也提供數個免費和商用產品，協助您建立剖析器。

### <a name="the-parsesource-parser"></a>ParseSource 剖析器
 不同于當做編譯器一部分使用的剖析器（權杖會轉換成某種形式的可執行程式碼），可以針對許多不同的原因和許多不同的內容呼叫語言服務剖析器。 您可自行決定如何在 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別的 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法中執行這種方法。 請務必記住，<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法可能會在背景執行緒上呼叫。

> [!CAUTION]
> @No__t_0 結構包含 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 物件的參考。 這個 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 物件無法在背景執行緒中使用。 事實上，許多基本的 MPF 類別無法用於背景執行緒中。 其中包括 <xref:Microsoft.VisualStudio.Package.Source>、<xref:Microsoft.VisualStudio.Package.ViewFilter>、<xref:Microsoft.VisualStudio.Package.CodeWindowManager> 類別，以及直接或間接與此視圖通訊的任何其他類別。

 此剖析器通常會在第一次呼叫或指定 <xref:Microsoft.VisualStudio.Package.ParseReason> 的剖析原因值時，剖析整個原始程式檔。 後續呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法會處理剖析程式碼的一小部分，而且可以使用先前完整剖析作業的結果，更快速地執行。 @No__t_0 方法會透過 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 和 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 物件來傳達剖析作業的結果。 @No__t_0 物件是用來收集特定剖析原因的資訊，例如，具有參數清單之相符大括弧或方法簽章範圍的相關資訊。 @No__t_0 提供宣告和方法簽章的集合，也支援 [移至] [開始] [編輯] 選項（[**移至定義**]、[**移至**宣告]、[**移至參考**]）。

### <a name="the-iscanner-scanner"></a>IScanner 掃描器
 您也必須執行可實行 <xref:Microsoft.VisualStudio.Package.IScanner> 的掃描器。 不過，由於此掃描器會逐一執行 <xref:Microsoft.VisualStudio.Package.Colorizer> 類別的程式碼，因此通常會比較容易執行。 在每一行的開頭，MPF 會為 <xref:Microsoft.VisualStudio.Package.Colorizer> 類別提供一個值，做為傳遞至掃描器的狀態變數。 在每一行的結尾，掃描器會傳回已更新的狀態變數。 MPF 會快取每一行的此狀態資訊，如此一來，掃描器就可以從任何一行開始剖析，而不需要從原始程式檔的開頭開始。 這一行快速掃描可讓編輯器提供快速的意見反應給使用者。

## <a name="parsing-for-matching-braces"></a>剖析成對的大括弧
 這個範例會顯示與使用者所輸入的右大括弧相符的控制流程。 在此程式中，用於顏色標示的掃描器也會用來判斷權杖的類型，以及權杖是否可以觸發符合括弧的運算。 如果找到觸發程式，則會呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法來尋找相符的大括弧。 最後，這兩個大括弧會反白顯示。

 即使觸發程式的名稱和剖析原因使用了大括弧，這個進程並不限於實際的大括弧。 支援指定為相符配對的任何一對字元。 範例包括（和）、\< 和 >，以及 [和]。

 假設語言服務支援成對的大括弧。

1. 使用者輸入右大括弧（}）。

2. 大括弧會插入至原始程式檔中的游標處，而資料指標則會前移一。

3. 使用具類型的右大括弧呼叫 <xref:Microsoft.VisualStudio.Package.Source> 類別中的 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 方法。

4. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 方法會在 <xref:Microsoft.VisualStudio.Package.Source> 類別中呼叫 <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 方法，以在目前資料指標位置之前的位置取得 token。 此標記對應至具類型的右大括弧）。

    1. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 方法會在 <xref:Microsoft.VisualStudio.Package.Colorizer> 物件上呼叫 <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 方法，以取得目前行上的所有標記。

    2. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 方法會使用目前行的文字，在 <xref:Microsoft.VisualStudio.Package.IScanner> 物件上呼叫 <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> 方法。

    3. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 方法會在 <xref:Microsoft.VisualStudio.Package.IScanner> 物件上重複呼叫 <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> 方法，以收集目前這一行的所有標記。

    4. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 方法會呼叫 <xref:Microsoft.VisualStudio.Package.Source> 類別中的私用方法，以取得包含所需位置的權杖，並傳入從 <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 方法取得的權杖清單。

5. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 方法會在從 <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 方法傳回的權杖上尋找 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 的 token 觸發旗標。也就是代表右大括弧的 token）。

6. 如果找到 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 的觸發程式旗標，則會呼叫 <xref:Microsoft.VisualStudio.Package.Source> 類別中的 <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> 方法。

7. <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> 方法會使用 <xref:Microsoft.VisualStudio.Package.ParseReason>的剖析原因值來啟動剖析作業。 這種作業最後會在 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別上呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法。 如果啟用非同步剖析，則會在背景執行緒上呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法。

8. 當剖析作業完成時，會在 <xref:Microsoft.VisualStudio.Package.Source> 類別中呼叫名為 `HandleMatchBracesResponse` 的內部完成處理常式（也稱為回呼方法）。 這個呼叫是由 <xref:Microsoft.VisualStudio.Package.LanguageService> 基類自動進行，而不是由剖析器所建立。

9. @No__t_0 方法會從儲存在 <xref:Microsoft.VisualStudio.Package.ParseRequest> 物件中的 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 物件，取得範圍的清單。 （Span 是 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> 結構，可指定原始程式檔中的行和字元範圍）。這份範圍清單通常包含兩個範圍，分別用於左和右大括弧。

10. @No__t_0 方法會針對儲存在 <xref:Microsoft.VisualStudio.Package.ParseRequest> 物件中的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 物件，呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> 方法。 這會反白顯示指定的範圍。

11. 如果已啟用 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 屬性 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>，`HandleBracesResponse` 方法會取得符合的範圍所包含的文字，並在狀態列中顯示該範圍的前80個字元。 如果 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法包含比對配對的語言元素，這就是最佳效果。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> 屬性 (Property)。

12. 即可.

### <a name="summary"></a>總結
 成對的大括弧運算通常僅限於一組簡單的語言專案。 更複雜的元素，例如比對三合一（"`if(...)`"、"`{`" 和 "`}`"，或 "`else`"、"`{`" 和 "`}`"），可以反白顯示為字完成作業的一部分。 例如，當「else」單字完成時，可以反白顯示相符的「`if`」語句。 如果有一系列的 `if` / `else if` 的語句，則可以使用與相符大括弧相同的機制來反白顯示所有專案。 @No__t_0 基類已支援此動作，如下所示：掃描器必須傳回標記觸發程式值，<xref:Microsoft.VisualStudio.Package.TokenTriggers> 與游標位置前面標記的觸發值 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 結合。

 如需詳細資訊，請參閱[舊版語言服務中的括弧](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)對稱。

## <a name="parsing-for-colorization"></a>顏色標示的剖析
 上色原始程式碼很簡單，只需識別 token 的類型，並傳回該類型的色彩資訊。 @No__t_0 類別會作為編輯器與掃描器之間的媒介，以提供每個權杖的色彩資訊。 @No__t_0 類別會使用 <xref:Microsoft.VisualStudio.Package.IScanner> 物件來協助上色一行，也會收集原始程式檔中所有行的狀態資訊。 在 MPF 語言服務類別中，不需要覆寫 <xref:Microsoft.VisualStudio.Package.Colorizer> 類別，因為它只會透過 <xref:Microsoft.VisualStudio.Package.IScanner> 介面與掃描器通訊。 您可以藉由覆寫 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別上的 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 方法，來提供可執行 <xref:Microsoft.VisualStudio.Package.IScanner> 介面的物件。

 @No__t_0 掃描器會透過 <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> 方法提供原始程式碼的一行程式碼。 系統會重複呼叫 <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> 方法，以取得行中的下一個 token，直到程式程式碼用完標記為止。 針對顏色標示，MPF 會將所有原始程式碼視為一連串的程式程式碼。 因此，掃描器必須能夠處理線路中的來源。 此外，任何一行都可以隨時傳遞至掃描器，而唯一的保證是掃描器會從要掃描的那一行前面的那一行接收狀態變數。

 @No__t_0 類別也會用來識別權杖觸發程式。 這些觸發程式會告訴 MPF，特定權杖可以起始更複雜的作業，例如文字完成或成對的大括弧。 因為識別這類觸發程式必須快速且必須在任何位置執行，所以掃描器最適合用於這項工作。

 如需詳細資訊，請參閱[舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。

## <a name="parsing-for-functionality-and-scope"></a>功能和範圍的剖析
 剖析功能和範圍需要比只識別所遇到的權杖類型更多。 剖析器不僅可以識別 token 的類型，也必須找出使用權杖的功能。 例如，識別碼只是名稱，但在您的語言中，識別碼可以是類別、命名空間、方法或變數的名稱（視內容而定）。 Token 的一般類型可以是識別碼，但識別碼也可能有其他意義，視其本身和定義位置而定。 此識別要求剖析器必須擁有更廣泛的剖析語言相關知識。 這是 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 類別的來源位置。 @No__t_0 類別會收集有關識別碼、方法、相符語言組（例如大括弧和括弧）和語言三合一的資訊（類似于語言組，但有三個部分，例如 "`foreach()`" "`{`" 和 "`}`"）. 此外，您可以覆寫 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 類別，以支援程式碼識別，這會在早期驗證中斷點時使用，因此不需要載入偵錯工具，以及顯示區域變數和參數**的 [自動**變數] [自動變數] 視窗。當程式正在進行調試時，會自動要求剖析器識別適當的區域變數和參數，以及偵錯工具所呈現的變數和參數。

 @No__t_0 物件會當做 <xref:Microsoft.VisualStudio.Package.ParseRequest> 物件的一部分傳遞至剖析器，而且每次建立新的 <xref:Microsoft.VisualStudio.Package.ParseRequest> 物件時，都會建立新的 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 物件。 此外，<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法必須傳回 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 物件，用來處理各種 IntelliSense 作業。 @No__t_0 物件會維護宣告的清單，以及方法的清單（根據剖析的原因而定）。 必須實作為 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 類別。

## <a name="see-also"></a>請參閱
- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [舊版語言服務概觀](../../extensibility/internals/legacy-language-service-overview.md)
- [舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [舊版語言服務中的括號對稱](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)