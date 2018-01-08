---
title: "舊版語言服務剖析器與掃描器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 755516fb9d341193005ad39e419e708b6d28867c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-language-service-parser-and-scanner"></a>舊版語言服務剖析器與掃描器
剖析器為語言服務的核心。 Managed Package Framework (MPF) 語言類別，需要選取要顯示的程式碼的相關資訊的語言剖析器。 剖析器會將文字分隔為語彙基元，並再識別這些語彙基元的類型和功能。  
  
## <a name="discussion"></a>討論  
 以下是 C# 方法。  
  
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
  
 在此範例中，語彙基元是字和標點符號。 語彙基元類型如下所示。  
  
|語彙基元名稱|語彙基元類型|  
|----------------|----------------|  
|命名空間、 類別、 公用、 void、 int|keyword|  
|=|運算子|  
|{ } ( ) ;|分隔符號|  
|MyNamespace、 MyClass、 MyFunction、 arg1、 var1|識別項|  
|MyNamespace|namespace|  
|MyClass|Class - 類別|  
|MyFunction|方法|  
|arg1|參數|  
|var1|區域變數|  
  
 剖析器的角色是識別權杖。 某些語彙基元可以有一個以上的類型。 剖析器發現語彙基元之後，要提供有用的功能，例如語法反白顯示，大括號比對的資訊和 IntelliSense 作業，可以使用之語言服務。  
  
## <a name="types-of-parsers"></a>剖析器的類型  
 語言服務剖析器不是做為編譯器的一部分使用的剖析器相同。 不過，這種剖析器需要掃描器和剖析器，用於與編譯器剖析器相同的方式。  
  
-   掃描器用來識別類型的語彙基元。 反白顯示語法及快速識別可以觸發其他作業，例如括號 token 類型比對，會使用這項資訊。 此程式由<xref:Microsoft.VisualStudio.Package.IScanner>介面。  
  
-   剖析器用來描述的功能與語彙基元的範圍。 這項資訊用於 IntelliSense 作業中，以識別語言的項目，例如方法、 變數、 參數和宣告，並提供成員與方法簽章內容為基礎的清單。 此剖析器也會用來尋找相符的語言項目組，例如大括號和括號中。 透過存取此剖析器<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法中的<xref:Microsoft.VisualStudio.Package.LanguageService>類別。  
  
 如何為您的語言服務實作的掃描器和剖析器是由您決定。 數個資源可供使用，描述剖析器的運作方式，以及如何撰寫自己的剖析器。 此外，有數個免費及商用產品，協助建立剖析器。  
  
### <a name="the-parsesource-parser"></a>ParseSource 剖析器  
 不同於使用的編譯器 （語彙基元會轉換為某種形式的可執行程式碼） 的一部分的剖析器，可以有許多原因，並在許多不同的內容中呼叫語言服務剖析器。 在這種方法的實作方式<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法中的<xref:Microsoft.VisualStudio.Package.LanguageService>類別是由您決定。 請務必記住，<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>可能會在背景執行緒上呼叫方法。  
  
> [!CAUTION]
>  <xref:Microsoft.VisualStudio.Package.ParseRequest>結構包含參考<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>物件。 這<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>物件不能在背景執行緒。 事實上，許多基底的 MPF 類別不能在背景執行緒。 這些包括<xref:Microsoft.VisualStudio.Package.Source>， <xref:Microsoft.VisualStudio.Package.ViewFilter>，<xref:Microsoft.VisualStudio.Package.CodeWindowManager>類別，以及直接或間接進行通訊與檢視任何其他類別。  
  
 此剖析器通常會剖析整個來源檔案的第一個時間呼叫它，或當剖析原因值<xref:Microsoft.VisualStudio.Package.ParseReason>指定。 後續呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法處理已剖析的程式碼的一小部分，而且可以使用先前的完整剖析作業的結果更快速地執行。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法通訊透過在剖析作業的結果<xref:Microsoft.VisualStudio.Package.AuthoringSink>和<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件。 <xref:Microsoft.VisualStudio.Package.AuthoringSink>物件用來收集特定的剖析原因，例如，資訊的範圍相符的大括號或具有參數清單的方法簽章的資訊。 <xref:Microsoft.VisualStudio.Package.AuthoringScope>提供宣告與方法簽章和也支援的集合移至進階編輯選項 (**移至定義**，**移至宣告**，**移至參考**)。  
  
### <a name="the-iscanner-scanner"></a>IScanner 掃描器  
 您也必須實作可實作掃描器<xref:Microsoft.VisualStudio.Package.IScanner>。 不過，因為這個掃描器運作透過一行一行地根據<xref:Microsoft.VisualStudio.Package.Colorizer>類別，它是通常更容易實作。 在每一行的開頭，MPF 可讓<xref:Microsoft.VisualStudio.Package.Colorizer>類別做為傳遞至掃描器狀態變數的值。 在每一行的結尾，掃描器會傳回更新的狀態變數。 MPF 會快取這項狀態資訊的每一行，這樣掃描器可以啟動而不需要原始程式檔的開頭開始剖析來自任何一行。 單行這個快速掃描時，可讓編輯器中，以提供快速的意見反應給使用者。  
  
## <a name="parsing-for-matching-braces"></a>剖析對稱的括號  
 此範例示範用於比對使用者輸入右大括號控制流程。 在此程序，也會使用用於顏色標示掃描器來決定的語彙基元和語彙基元是否可以觸發比對括號作業類型。 如果找到觸發程序，<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>呼叫方法來尋找相符的大括號。 最後，會反白顯示兩個大括號。  
  
 即使大括號用來觸發程序的名稱，而且剖析原因，此程序並不限於實際的大括號。 支援任何一對的字元指定為相符配對。 範例包括 （和）\<和 >，以及 [和]。  
  
 假設該語言服務支援對稱的括號。  
  
1.  使用者會輸入右大括號 （}）。  
  
2.  在原始程式檔中的資料指標插入的大括號和資料指標一個進階。  
  
3.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法中的<xref:Microsoft.VisualStudio.Package.Source>類別稱為具類型的右大括號。  
  
4.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法呼叫<xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>方法中的<xref:Microsoft.VisualStudio.Package.Source>類別來取得目前游標位置之前位置的語彙基元。 這個語彙基元對應至具類型的右大括號）。  
  
    1.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>方法呼叫<xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>方法<xref:Microsoft.VisualStudio.Package.Colorizer>物件，取得目前的行上的所有權杖。  
  
    2.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>方法呼叫<xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>方法<xref:Microsoft.VisualStudio.Package.IScanner>物件使用目前這一行的文字。  
  
    3.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>方法重複呼叫<xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A>方法<xref:Microsoft.VisualStudio.Package.IScanner>物件從目前的行收集的所有權杖。  
  
    4.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>方法會呼叫私用的方法中<xref:Microsoft.VisualStudio.Package.Source>類別取得的權杖，其中包含所要的位置，並從取得的權杖清單中的傳遞<xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>方法。  
  
5.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法會尋找語彙基元的觸發程序旗標為<xref:Microsoft.VisualStudio.Package.TokenTriggers>上從傳回的語彙基元<xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>方法，也就是右大括號表示語彙基元)。  
  
6.  如果觸發程序的旗標的<xref:Microsoft.VisualStudio.Package.TokenTriggers>找到，<xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>方法中的<xref:Microsoft.VisualStudio.Package.Source>類別呼叫。  
  
7.  <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>方法以剖析原因值開頭的剖析作業<xref:Microsoft.VisualStudio.Package.ParseReason>。 這項作業最後呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法<xref:Microsoft.VisualStudio.Package.LanguageService>類別。 如果已啟用非同步剖析，此呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法，就會發生在背景執行緒上。  
  
8.  當在剖析作業完成時，名為內部完成處理常式 （也稱為回呼方法）`HandleMatchBracesResponse`中呼叫<xref:Microsoft.VisualStudio.Package.Source>類別。 進行這個呼叫時自動由<xref:Microsoft.VisualStudio.Package.LanguageService>不是由剖析器的基底類別。  
  
9. `HandleMatchBracesResponse`方法會取得一份範圍從<xref:Microsoft.VisualStudio.Package.AuthoringSink>物件儲存在<xref:Microsoft.VisualStudio.Package.ParseRequest>物件。 (範圍是<xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>原始程式檔中指定的行和字元範圍的結構。)這份清單的範圍通常包含兩個範圍，其中每個左和右大括號。  
  
10. `HandleBracesResponse`方法呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>物件儲存在<xref:Microsoft.VisualStudio.Package.ParseRequest>物件。 這會反白顯示指定的範圍。  
  
11. 如果<xref:Microsoft.VisualStudio.Package.LanguagePreferences>屬性<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>已啟用，`HandleBracesResponse`方法會取得比對範圍所包含，並在狀態列中顯示該範圍的前 80 個字元的文字。 這最適合如果<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法包含隨附一組相符的語言項目。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> 屬性 (Property)。  
  
12. 完成。  
  
### <a name="summary"></a>總結  
 比對括號作業是通常限制為簡單的語言項目組。 更複雜的項目，例如比對等三合一 (「`if(...)`"，"`{`"和"`}`"，或"`else`"，"`{`"和"`}`")，可以反白顯示文字完成作業的一部分。 例如，"else"word 完成時，比對"`if`"陳述式可以反白顯示。 如果有一系列的`if` / `else if`陳述式，全部都無法使用相同的機制，做為對稱的括號反白顯示。 <xref:Microsoft.VisualStudio.Package.Source>基底類別所支援，如下： 掃描器必須傳回的語彙基元的觸發程序值<xref:Microsoft.VisualStudio.Package.TokenTriggers>與觸發程序值結合<xref:Microsoft.VisualStudio.Package.TokenTriggers>的游標位置之前的權杖。  
  
 如需詳細資訊，請參閱[舊版語言服務中的大括號比對](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)。  
  
## <a name="parsing-for-colorization"></a>剖析顏色標示  
 標示色彩原始程式碼相當簡單，只要識別的色彩語彙基元並傳回該類型的資訊類型。 <xref:Microsoft.VisualStudio.Package.Colorizer>類別是做為編輯器和掃描器，提供有關每個語彙基元的色彩資訊之間的媒介。 <xref:Microsoft.VisualStudio.Package.Colorizer>類別會使用<xref:Microsoft.VisualStudio.Package.IScanner>物件協助以色彩標示一條線並收集原始程式檔中的所有行的狀態資訊。 MPF 語言服務類別，在<xref:Microsoft.VisualStudio.Package.Colorizer>類別並沒有覆寫，因為它與掃描器通訊只能透過<xref:Microsoft.VisualStudio.Package.IScanner>介面。 提供實作的物件<xref:Microsoft.VisualStudio.Package.IScanner>藉由覆寫介面<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法<xref:Microsoft.VisualStudio.Package.LanguageService>類別。  
  
 <xref:Microsoft.VisualStudio.Package.IScanner>掃描器有透過原始程式碼行<xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>方法。 呼叫<xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A>方法重複取得行中的下一個權杖，直到線條會用完的語彙基元。 顏色標示、 MPF 會視為一系列線條來源的所有程式碼。 因此，將掃描器必須能夠應付為線條即將在它的來源。 此外，任何列可以在任何時候，傳遞至掃描器，且唯一能保證掃描器會從行之前會掃描即將接收狀態變數。  
  
 <xref:Microsoft.VisualStudio.Package.Colorizer>類別也可以用來識別權杖的觸發程序。 這些觸發程序告訴 MPF 特定語彙基元可以起始更複雜的作業，例如文字完成或對稱的括號。 因為用來識別這類觸發程序必須快速，必須發生在任何位置，將掃描器最適合用於這項工作。  
  
 如需詳細資訊，請參閱[語法色彩標示在舊版語言服務](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。  
  
## <a name="parsing-for-functionality-and-scope"></a>剖析功能和領域  
 剖析功能和領域需要較多的工作比只指出發生的語彙基元的類型。 剖析器具有識別，而不是只是語彙基元的類型語彙基元，會使用的功能。 例如，識別項是只有名稱，但您的語言識別碼可能是類別、 命名空間、 方法或變數，視內容而定的名稱。 一般類型的語彙基元可能是識別碼，但識別碼也可能有其他的意義，根據它是什麼，並定義的位置。 這個識別會需要有更廣泛的知識，有關正在剖析的語言剖析器。 這是 where<xref:Microsoft.VisualStudio.Package.AuthoringSink>進來的類別。 <xref:Microsoft.VisualStudio.Package.AuthoringSink>類別會收集識別項、 方法、 相符的語言組 （例如大括號和括號） 和語言等三合一的相關資訊 (但會有三個部分，例如，類似的語言組"`foreach()`""`{`"和"`}`")。 此外，您可以覆寫<xref:Microsoft.VisualStudio.Package.AuthoringSink>類別，以支援程式碼識別為驗證中所使用早期的中斷點，讓偵錯工具沒有載入，而**自動變數**偵錯視窗中，會顯示本機變數和參數自動當程式正在偵錯，需要識別適當的本機變數和參數，除了偵錯工具會顯示剖析器。  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink>物件的一部分傳遞給剖析器<xref:Microsoft.VisualStudio.Package.ParseRequest>物件和新<xref:Microsoft.VisualStudio.Package.AuthoringSink>物件是每次建立新<xref:Microsoft.VisualStudio.Package.ParseRequest>建立物件。 此外，<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法必須傳回<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件，用來處理各種 IntelliSense 作業。 <xref:Microsoft.VisualStudio.Package.AuthoringScope>物件會維護宣告的清單和清單的方法，可能是其中已填入，根據剖析的原因。 <xref:Microsoft.VisualStudio.Package.AuthoringScope>類別必須實作。  
  
## <a name="see-also"></a>請參閱  
 [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [舊版語言服務概觀](../../extensibility/internals/legacy-language-service-overview.md)   
 [語法色彩標示在舊版語言服務](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [舊版語言服務中的括號對稱](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)