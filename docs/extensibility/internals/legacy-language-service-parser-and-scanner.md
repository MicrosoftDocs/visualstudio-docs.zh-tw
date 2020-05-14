---
title: 傳統語言服務解析器和掃描器 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c87f447a4b8bca804d27aae4967f4adaf389c627
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707319"
---
# <a name="legacy-language-service-parser-and-scanner"></a>舊版語言服務的剖析器和掃描器
解析器是語言服務的核心。 託管套件框架 (MPF) 語言類需要語言解析器來選擇有關顯示的代碼的資訊。 解析器將文本分隔成詞法標記,然後按類型和功能標識這些標記。

## <a name="discussion"></a>討論區
 下面是 C# 方法。

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

 在此示例中,標記是單詞和標點符號。 令牌的種類如下。

|權杖名稱|權杖類型|
|----------------|----------------|
|命名空間, 類別, 一般, 不合法, 不合法, int|關鍵字 (keyword)|
|=|! 運算子之後|
|{ } ( ) ;|分隔符號|
|MyNamespace, 我的類別, 我的功能, arg1, var1|識別碼 (identifier)|
|我的命名空間|namespace|
|MyClass|Class - 類別|
|我的功能|method|
|arg1|參數 (parameter)|
|瓦爾1|區域變數 (local variable)|

 解析器的作用是標識權杖。 某些權杖可以有多個類型。 解析器標識權杖後,語言服務可以使用該資訊提供有用的功能,如語法突出顯示、大括弧匹配和 IntelliSense 操作。

## <a name="types-of-parsers"></a>分析器的類型
 語言服務解析器與用作編譯器一部分的解析器不同。 但是,這種解析器需要同時使用掃描器和解析器,就像編譯器解析器一樣。

- 掃描器用於標識權杖的類型。 這項資訊可用於反白顯示語法及快速識別可以觸發其他作業 (例如括號對稱) 的 Token 類型。 此掃描器由<xref:Microsoft.VisualStudio.Package.IScanner>介面表示。

- 解析器用於描述權杖的函數和範圍。 此資訊用於 IntelliSense 操作中,用於標識語言元素,如方法、變數、參數和聲明,並基於上下文提供成員和方法簽名的清單。 此解析器還用於查找匹配的語言元素對,如大括弧和括弧。 此解析器通過<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A><xref:Microsoft.VisualStudio.Package.LanguageService>類中的方法進行訪問。

  如何為語言服務實現掃描器和分析程式由您決定。 有幾個資源可用於描述解析器的工作原理以及如何編寫自己的解析器。 此外,還有幾種免費和商業產品,有助於創建解析器。

### <a name="the-parsesource-parser"></a>The ParseSource Parser
 與用作編譯器一部分的解析器(其中令牌轉換為某種形式的可執行代碼)不同,可以出於許多不同的原因和許多不同的上下文中調用語言服務解析器。 如何在<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A><xref:Microsoft.VisualStudio.Package.LanguageService>類中的方法中實現此方法由您決定。 請務必記住,<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>該方法可能在後台線程上調用。

> [!CAUTION]
> 結構<xref:Microsoft.VisualStudio.Package.ParseRequest>包含對<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>物件的引用。 此<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>物件不能在後台線程中使用。 事實上,許多基本 MPF 類不能在後台線程中使用。 其中包括、<xref:Microsoft.VisualStudio.Package.Source><xref:Microsoft.VisualStudio.Package.ViewFilter><xref:Microsoft.VisualStudio.Package.CodeWindowManager>類和直接或間接與視圖通信的任何其他類。

 此解析器通常在首次調用整個源檔或給出<xref:Microsoft.VisualStudio.Package.ParseReason>的解析原因值時對其進行分析。 對方法的<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>後續調用處理已分析代碼的一小部分,並且可以使用上一個完整分析操作的結果更快地執行。 該方法<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A><xref:Microsoft.VisualStudio.Package.AuthoringSink>通過<xref:Microsoft.VisualStudio.Package.AuthoringScope>和物件傳達分析操作的結果。 該<xref:Microsoft.VisualStudio.Package.AuthoringSink>物件用於收集特定分析原因的資訊,例如,有關匹配大括弧或具有參數清單的方法簽名範圍的資訊。 提供<xref:Microsoft.VisualStudio.Package.AuthoringScope>聲明和方法簽名的集合,並支援「轉到進階編輯」選項(**轉到定義**、**轉到聲明**、**轉到引用**)。

### <a name="the-iscanner-scanner"></a>IScanner 掃描器
 還必須實現實現<xref:Microsoft.VisualStudio.Package.IScanner>的掃描程式。 但是,由於此掃描器通過<xref:Microsoft.VisualStudio.Package.Colorizer>類逐行運行,因此通常更容易實現。 在每行的開頭,MPF<xref:Microsoft.VisualStudio.Package.Colorizer>為 類提供一個值,用作傳遞給掃描器的狀態變數。 在每行的末尾,掃描器返回更新的狀態變數。 MPF 快取每行的狀態資訊,以便掃描程式可以從任何行開始解析,而無需從源檔的開頭開始。 這種對單行的快速掃描使編輯器能夠向使用者提供快速回饋。

## <a name="parsing-for-matching-braces"></a>剖析匹配大括弧
 此示例顯示用於匹配用戶鍵入的關閉大括弧的控制流。 在此過程中,用於著色的掃描器還用於確定權杖的類型以及權杖是否可以觸發匹配括弧操作。 如果找到觸發器,<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>則呼叫 該方法以查找匹配的大括弧。 最後,兩個大括弧高亮顯示。

 即使大括弧用於觸發器的名稱和分析原因,此過程也不限於實際大括弧。 支援指定為匹配對的任何字元對。 範例包括\<( 與 ) 與 >, 以及 [ 與 】 與 】 。

 假定語言服務支援匹配大括弧。

1. 用戶鍵入關閉大括弧 (*)。

2. 大括弧插入到源檔中的游標上,游標由 1 前進。

3. <xref:Microsoft.VisualStudio.Package.Source>類<xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>中的方法使用鍵入的閉合大括弧調用。

4. 方法<xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>調用類<xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A><xref:Microsoft.VisualStudio.Package.Source>中 的方法以在當前游標位置之前的位置獲取令牌。 此令牌對應於鍵入的右大括弧)。

    1. 該方法<xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>調<xref:Microsoft.VisualStudio.Package.Colorizer>用<xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>物件上 的方法以獲取當前行上的所有權杖。

    2. 該方法<xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>使用當前<xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>行 的文本<xref:Microsoft.VisualStudio.Package.IScanner>調用 物件上的方法。

    3. 該方法<xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>反覆調<xref:Microsoft.VisualStudio.Package.IScanner>用<xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A>物件上 的方法以從當前行收集所有令牌。

    4. 該方法<xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>調用類<xref:Microsoft.VisualStudio.Package.Source>中的 私有方法以獲取包含所需位置的權杖,並<xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>傳遞從方法獲取的權杖清單中。

5. 該方法<xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>在<xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>從 方法返回的權<xref:Microsoft.VisualStudio.Package.TokenTriggers>杖上 查找 令牌觸發器標誌;即表示關閉大括弧的權杖)。

6. 如果找到<xref:Microsoft.VisualStudio.Package.TokenTriggers>的觸發器標誌,則調<xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A><xref:Microsoft.VisualStudio.Package.Source>用 類中的方法。

7. 該方法<xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>啟動具有 的解析原因<xref:Microsoft.VisualStudio.Package.ParseReason>值的 解析操作。 此操作最終調用<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A><xref:Microsoft.VisualStudio.Package.LanguageService>類上的方法。 如果啟用非同步分析,則對該方法<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>的此調用將發生在後台線程上。

8. 分析操作完成後,`HandleMatchBracesResponse`<xref:Microsoft.VisualStudio.Package.Source>類別中調用名為的內部完成處理程式(也稱為回調方法)。 此調用由<xref:Microsoft.VisualStudio.Package.LanguageService>基類自動進行,而不是由解析器進行。

9. 該方法`HandleMatchBracesResponse`從存儲<xref:Microsoft.VisualStudio.Package.AuthoringSink><xref:Microsoft.VisualStudio.Package.ParseRequest>在 物件中的對象獲取範圍清單。 (範圍是指定<xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>源檔中的行和字元範圍的結構。此範圍清單通常包含兩個範圍,每個範圍用於開口和關閉大括弧。

10. 該方法`HandleBracesResponse`調<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView><xref:Microsoft.VisualStudio.Package.ParseRequest>存儲在 物件中的物件上的方法。 這將突出顯示給定的跨度。

11. 如果啟用<xref:Microsoft.VisualStudio.Package.LanguagePreferences><xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>了 該`HandleBracesResponse`屬性, 該方法將獲取匹配範圍包含的文本,並在狀態列中顯示該範圍的前 80 個字元。 如果<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>該方法包含匹配對附帶的語言元素,則此方法效果最佳。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> 屬性 (Property)。

12. 大功告成。

### <a name="summary"></a>摘要
 匹配的大括弧操作通常僅限於簡單的語言元素對。 更複雜的元素,如匹配三重`if(...)`元素("",""`{``}`和""," 或"""""""`else``{`和`}`""), 可以作為單詞完成操作的一部分突出顯示。 例如,當"else"字完成後,可以突出顯示匹配的""`if`語句。 如果有一系列`if`/`else if`語句,則可以使用與匹配大括弧相同的機制突出顯示所有這些語句。 基<xref:Microsoft.VisualStudio.Package.Source>類已經支援此功能,如下所示:掃描程序必須返回令牌觸發器<xref:Microsoft.VisualStudio.Package.TokenTriggers>值 與游標位置之前標記的觸<xref:Microsoft.VisualStudio.Package.TokenTriggers>發器 值組合。

 有關詳細資訊,請參閱[舊語言服務中的"大括弧匹配](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)"。

## <a name="parsing-for-colorization"></a>色化分析
 著色原始碼非常簡單,只需標識權杖的類型並返回有關該類型的顏色資訊。 類<xref:Microsoft.VisualStudio.Package.Colorizer>充當編輯器和掃描器之間的仲介,以提供有關每個令牌的顏色資訊。 類<xref:Microsoft.VisualStudio.Package.Colorizer>使用<xref:Microsoft.VisualStudio.Package.IScanner>對象 幫助對行著色,還收集源檔中所有行的狀態資訊。 在 MPF 語言服務<xref:Microsoft.VisualStudio.Package.Colorizer>類中 ,不必重寫該類,因為<xref:Microsoft.VisualStudio.Package.IScanner>它只能通過 介面與掃描器通信。 通過重寫<xref:Microsoft.VisualStudio.Package.LanguageService>類上的方法<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>來<xref:Microsoft.VisualStudio.Package.IScanner>提供 實現介面的物件。

 通過<xref:Microsoft.VisualStudio.Package.IScanner><xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>該方法為掃描器提供了一行原始程式碼。 重複對<xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A>方法的調用以獲取行中的下一個令牌,直到行用完令牌。 對於著色,MPF 將所有原始碼視為行序列。 因此,掃描器必須能夠處理源作為行。 此外,任何線路可以隨時傳遞到掃描器,唯一的保證是掃描器在要掃描的行之前從行接收狀態變數。

 該<xref:Microsoft.VisualStudio.Package.Colorizer>類還用於標識令牌觸發器。 這些觸發器告訴 MPF 特定權杖可以啟動更複雜的操作,例如單詞完成或匹配大括弧。 由於識別此類觸發器必須快速,並且必須在任何位置發生,因此掃描器最適合此任務。

 有關詳細資訊,請參閱[舊語言服務中的語法著色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。

## <a name="parsing-for-functionality-and-scope"></a>分析功能和範圍
 分析功能和範圍需要付出更多的努力,而不僅僅是識別遇到的權杖類型。 解析器不僅要標識令牌的類型,還要標識使用令牌的功能。 例如,標識碼只是一個名稱,但在您的語言中,標識符可以是類、命名空間、方法或變數的名稱,具體取決於上下文。 令牌的一般類型可能是標識符,但標識符可能還有其他含義,具體取決於它是什麼和在哪裡定義它。 此標識要求解析器對正在分析的語言有更廣泛的知識。 這就是<xref:Microsoft.VisualStudio.Package.AuthoringSink>課程的用處。 該<xref:Microsoft.VisualStudio.Package.AuthoringSink>類別收集有關識別碼、方法、匹配語言對(如大括弧和括弧)和語言三重(類似於語言對,但有三個部分,例如""""`foreach()``{`和`}`") 的資訊。 此外,還可以重寫<xref:Microsoft.VisualStudio.Package.AuthoringSink>類以支援代碼標識(用於早期驗證斷點,以便不必載入調試器)和**Autos**調試視窗,該視窗在調試程式時自動顯示局部變數和參數,並要求解析器除調試器提供這些變數和參數外,還標識適當的局部變數和參數。

 對<xref:Microsoft.VisualStudio.Package.AuthoringSink>象<xref:Microsoft.VisualStudio.Package.ParseRequest>作為 物件的一部分傳遞給解析器,並且每次<xref:Microsoft.VisualStudio.Package.AuthoringSink><xref:Microsoft.VisualStudio.Package.ParseRequest>創建新 物件時都會創建新物件。 此外,<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>該方法必須返回一<xref:Microsoft.VisualStudio.Package.AuthoringScope>個 物件,該物件用於處理各種 IntelliSense 操作。 對<xref:Microsoft.VisualStudio.Package.AuthoringScope>象 維護聲明的清單和方法的清單,其中任一都填充,具體取決於分析的原因。 必須<xref:Microsoft.VisualStudio.Package.AuthoringScope>實現類。

## <a name="see-also"></a>另請參閱
- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [舊版語言服務概觀](../../extensibility/internals/legacy-language-service-overview.md)
- [舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [舊版語言服務中的括號對稱](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
