---
title: 舊版語言服務剖析器和掃描器 |Microsoft Docs
description: 深入瞭解舊版語言服務剖析器和掃描器，以選取要顯示之程式碼的相關資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c4c9ee6cfec35804d7e60675342f3961dfb90c6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839556"
---
# <a name="legacy-language-service-parser-and-scanner"></a>舊版語言服務的剖析器和掃描器
剖析器是語言服務的核心。 受管理的封裝架構 (MPF) 語言類別需要語言剖析器來選取要顯示之程式碼的相關資訊。 剖析器會將文字分隔為詞法標記，然後根據類型和功能來識別這些權杖。

## <a name="discussion"></a>討論
 以下是 c # 方法。

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

 在此範例中，標記為單字和標點符號。 權杖的種類如下所示。

|權杖名稱|權杖類型|
|----------------|----------------|
|namespace、class、public、void、int|關鍵字 (keyword)|
|=|運算子|
|{ } ( ) ;|分隔符號|
|MyNamespace、MyClass、MyFunction、arg1、var1|識別碼 (identifier)|
|MyNamespace|命名空間|
|MyClass|Class - 類別|
|MyFunction|method|
|arg1|參數|
|var1|區域變數 (local variable)|

 剖析器的角色是用來識別標記。 某些權杖可以有一種以上的類型。 剖析器識別出標記之後，語言服務可以使用此資訊來提供有用的功能，例如語法醒目提示、括弧對稱和 IntelliSense 作業。

## <a name="types-of-parsers"></a>剖析器的類型
 語言服務剖析器與當做編譯器一部分使用的剖析器不同。 不過，這種剖析器需要同時使用掃描器和剖析器，就像編譯器剖析器一樣。

- 掃描器可用來識別權杖的類型。 這項資訊可用於反白顯示語法及快速識別可以觸發其他作業 (例如括號對稱) 的 Token 類型。 此掃描器由 <xref:Microsoft.VisualStudio.Package.IScanner> 介面表示。

- 剖析器用來描述權杖的函式和範圍。 這項資訊會在 IntelliSense 作業中用來識別語言元素，例如方法、變數、參數和宣告，以及根據內容提供成員和方法簽章的清單。 此剖析器也可用來尋找相符的語言專案組，例如大括弧和括弧。 此剖析器可透過 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 類別中的方法來存取 <xref:Microsoft.VisualStudio.Package.LanguageService> 。

  您可以自行決定如何為您的語言服務執行掃描器和剖析器。 有幾個資源可描述剖析器的運作方式，以及如何撰寫您自己的剖析器。 此外，有數個免費和商用產品可協助建立剖析器。

### <a name="the-parsesource-parser"></a>ParseSource 剖析器
 不同于當做編譯器一部分使用的剖析器 (其中的標記會轉換成某種可執行程式碼) ，語言服務剖析器可基於許多不同的原因和在許多不同的內容中呼叫。 在類別的方法中，您可以自行決定如何執行此方法 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> 。 請務必記住， <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法可能會在背景執行緒上呼叫。

> [!CAUTION]
> <xref:Microsoft.VisualStudio.Package.ParseRequest>結構包含物件的參考 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 。 這個 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 物件不能用在背景執行緒中。 事實上，許多基礎紙器類別都不能用在背景執行緒中。 其中包括 <xref:Microsoft.VisualStudio.Package.Source> 、 <xref:Microsoft.VisualStudio.Package.ViewFilter> 、 <xref:Microsoft.VisualStudio.Package.CodeWindowManager> 類別，以及直接或間接與視圖通訊的其他任何類別。

 此剖析器通常會在第一次呼叫時剖析整個來源檔案，或在指定的剖析原因值時剖析 <xref:Microsoft.VisualStudio.Package.ParseReason> 。 後續的方法呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 會處理剖析程式碼的一小部分，而且可以使用先前的完整剖析作業結果更快速地執行。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法會透過和物件來傳達剖析作業的結果 <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.AuthoringScope> 。 <xref:Microsoft.VisualStudio.Package.AuthoringSink>物件是用來收集特定剖析原因的資訊，例如，具有參數清單的相符大括弧或方法簽章範圍的相關資訊。 <xref:Microsoft.VisualStudio.Package.AuthoringScope>提供宣告和方法簽章的集合，也支援 [移至 advanced] 編輯選項 (**移至 [定義**]、[**移至** 宣告]、[**移至參考**]) 。

### <a name="the-iscanner-scanner"></a>IScanner 掃描器
 您也必須執行可執行檔掃描器 <xref:Microsoft.VisualStudio.Package.IScanner> 。 不過，因為此掃描器會透過類別逐行執行 <xref:Microsoft.VisualStudio.Package.Colorizer> ，所以通常更容易執行。 在每一行的開頭，MPF 會為類別提供 <xref:Microsoft.VisualStudio.Package.Colorizer> 一個值，以作為傳遞給掃描器的狀態變數使用。 在每一行的結尾，掃描器會傳回更新的狀態變數。 MPF 會快取每一行的這項狀態資訊，讓掃描器可以從任何一行開始剖析，而不需要從原始程式檔的開頭開始剖析。 這一行快速掃描，可讓編輯器為使用者提供快速的意見反應。

## <a name="parsing-for-matching-braces"></a>剖析成對的大括弧
 這個範例會顯示控制項的流程，以比對使用者所輸入的右大括弧。 在此程式中，用於顏色標示的掃描器也會用來判斷權杖的類型，以及標記是否可以觸發符合括弧的作業。 如果找到觸發程式，則 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 會呼叫方法來尋找相符的括弧。 最後，會反白顯示兩個大括弧。

 即使在觸發程式的名稱和剖析原因中使用大括弧，此程式並不限於實際的大括弧。 支援指定為相符配對的任何字元對。 範例包括 ( 和 ) 、 \< and > 和 [和]。

 假設語言服務支援相符的大括弧。

1. 使用者輸入右大括弧 (} ) 。

2. 大括弧會插入至原始程式檔中的資料指標，且資料指標會以一開始。

3. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>類別中的方法 <xref:Microsoft.VisualStudio.Package.Source> 會以具類型的右大括弧來呼叫。

4. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法會呼叫 <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 類別中的方法 <xref:Microsoft.VisualStudio.Package.Source> ，以在目前的資料指標位置之前的位置取得權杖。 此標記對應至) 的輸入右大括弧。

    1. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>方法會 <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 在物件上呼叫方法 <xref:Microsoft.VisualStudio.Package.Colorizer> ，以取得目前行上的所有標記。

    2. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>方法會 <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> <xref:Microsoft.VisualStudio.Package.IScanner> 使用目前行的文字來呼叫物件上的方法。

    3. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>方法會重複呼叫 <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> 物件上的方法 <xref:Microsoft.VisualStudio.Package.IScanner> ，以收集目前這一行的所有標記。

    4. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>方法會呼叫類別中的私用方法 <xref:Microsoft.VisualStudio.Package.Source> ，以取得包含所需位置的權杖，並在從方法取得的標記清單中傳遞 <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 。

5. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法會在從方法傳回的標記上尋找 token 觸發旗標， <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 也就是代表右括弧) 的標記。

6. 如果找到的觸發旗標 <xref:Microsoft.VisualStudio.Package.TokenTriggers> ，則 <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> <xref:Microsoft.VisualStudio.Package.Source> 會呼叫類別中的方法。

7. <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>方法會使用的剖析原因值來啟動剖析作業 <xref:Microsoft.VisualStudio.Package.ParseReason> 。 這種作業最後會呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 類別上的方法 <xref:Microsoft.VisualStudio.Package.LanguageService> 。 如果已啟用非同步剖析，則這個方法的呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 會在背景執行緒上發生。

8. 當剖析作業完成時， `HandleMatchBracesResponse` 會在類別中呼叫內部完成處理常式 (也稱為回呼方法) 名為 <xref:Microsoft.VisualStudio.Package.Source> 。 此呼叫是由基類自動進行 <xref:Microsoft.VisualStudio.Package.LanguageService> ，而不是由剖析器所建立。

9. `HandleMatchBracesResponse`方法 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 會從儲存在物件中的物件取得範圍清單 <xref:Microsoft.VisualStudio.Package.ParseRequest> 。  (範圍是一種 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> 結構，可指定原始程式檔中的行和字元範圍。 ) 此範圍清單通常包含兩個範圍，每個範圍都是左右大括弧。

10. `HandleBracesResponse`方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 會在儲存于物件中的物件上呼叫方法 <xref:Microsoft.VisualStudio.Package.ParseRequest> 。 這會反白顯示指定的範圍。

11. 如果 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> 已啟用屬性，方法會取得 `HandleBracesResponse` 相符範圍所包含的文字，並在狀態列中顯示該範圍的前80個字元。 如果 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法包含隨附于相符配對的語言專案，這就會有最佳效果。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> 屬性 (Property)。

12. 大功告成。

### <a name="summary"></a>摘要
 相符的大括弧運算通常僅限於一組簡單的語言專案。 更複雜的元素（例如，比對三 ( ""、""、" `if(...)` `{` "、"" `}` `else` 、" `{` " 和 " `}` " ) ）可以反白顯示為字完成作業的一部分。 例如，當 "else" 單字完成時，可以反白顯示相符的 " `if` " 語句。 如果有一系列的 `if` / `else if` 語句，則可以使用相同的機制來反白顯示所有的語句。 <xref:Microsoft.VisualStudio.Package.Source>基類已支援這項功能，如下所示：掃描器必須傳回 token 觸發程式值， <xref:Microsoft.VisualStudio.Package.TokenTriggers> 並與 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 游標位置之前的標記觸發值結合。

 如需詳細資訊，請參閱 [舊版語言服務中的括弧](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)比對。

## <a name="parsing-for-colorization"></a>顏色標示剖析
 標示原始程式碼很簡單，只是識別權杖的類型，並傳回與該類型有關的色彩資訊。 <xref:Microsoft.VisualStudio.Package.Colorizer>類別會作為編輯器與掃描器之間的媒介，以提供每個標記的色彩資訊。 <xref:Microsoft.VisualStudio.Package.Colorizer>類別會使用 <xref:Microsoft.VisualStudio.Package.IScanner> 物件來協助標示一行，也會收集原始程式檔中所有行的狀態資訊。 在 MPF 語言服務類別中， <xref:Microsoft.VisualStudio.Package.Colorizer> 不需要覆寫類別，因為它只能透過介面與掃描器進行通訊 <xref:Microsoft.VisualStudio.Package.IScanner> 。 您可以藉 <xref:Microsoft.VisualStudio.Package.IScanner> 由覆寫類別上的方法，提供可執行介面的物件 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> 。

 <xref:Microsoft.VisualStudio.Package.IScanner>掃描器會透過方法提供一行原始程式碼 <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> 。 方法的呼叫 <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> 會重複以取得該行中的下一個 token，直到程式程式碼用盡權杖為止。 針對顏色標示，MPF 會將所有原始程式碼視為一連串的行。 因此，掃描器必須能夠以行作為來源。 此外，任何一行都可以隨時傳遞至掃描器，唯一的保證是掃描器會從要掃描的行之前的那一行接收狀態變數。

 <xref:Microsoft.VisualStudio.Package.Colorizer>類別也會用來識別權杖觸發程式。 這些觸發程式會告訴 MPF，特定權杖可以起始更複雜的作業，例如文字完成或配對的大括弧。 因為識別這類觸發程式必須很快，而且必須在任何位置進行，掃描器最適合這項工作。

 如需詳細資訊，請參閱 [舊版語言服務中的語法標示](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。

## <a name="parsing-for-functionality-and-scope"></a>功能和範圍剖析
 剖析功能和範圍需要更多的工作，而不只是識別所遇到的權杖類型。 剖析器必須識別權杖的類型，以及使用權杖的功能。 例如，識別碼只是一個名稱，但在您的語言中，識別碼可以是類別、命名空間、方法或變數的名稱（視內容而定）。 權杖的一般類型可以是識別碼，但識別碼也可能有其他意義，視其本身和定義位置而定。 此識別要求剖析器需要更廣泛的知識來剖析所剖析的語言。 這是類別的 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 來源位置。 <xref:Microsoft.VisualStudio.Package.AuthoringSink>類別會收集識別碼、方法、比對語言組的相關資訊 (例如大括弧和括弧) ，以及語言三合一 (類似于語言組，但有三個部分，例如 "" "" `foreach()` `{` 和 " `}` " ) 。 此外，您可以覆寫 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 類別以支援程式碼識別，這項功能可用於早期驗證中斷點，而不需要載入偵錯工具，而 [自動變數偵錯工具] 視窗 **則會** 在偵錯工具時自動顯示本機變數和參數，而且除了偵錯工具所呈現的參數和參數之外，還會要求剖析器識別適當的區域變數和參數。

 <xref:Microsoft.VisualStudio.Package.AuthoringSink>物件會傳遞至剖析器作為物件的一部分 <xref:Microsoft.VisualStudio.Package.ParseRequest> ，並在 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 每次建立新物件時建立新的物件 <xref:Microsoft.VisualStudio.Package.ParseRequest> 。 此外，此 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法必須傳回 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 用來處理各種 IntelliSense 作業的物件。 <xref:Microsoft.VisualStudio.Package.AuthoringScope>物件會維護宣告的清單，以及方法的清單，這些方法會根據剖析的原因來填入。 必須實作為 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 類別。

## <a name="see-also"></a>另請參閱
- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [舊版語言服務概觀](../../extensibility/internals/legacy-language-service-overview.md)
- [舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [舊版語言服務中的括號對稱](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
