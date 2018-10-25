---
title: 舊版語言服務剖析器和掃描器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d4ca98b5e4f991e795af95e479fa57a38ca2b57a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912041"
---
# <a name="legacy-language-service-parser-and-scanner"></a>舊版語言服務的剖析器和掃描器
剖析器是語言服務的核心。 Managed Package Framework (MPF) 語言類別需要的語言剖析器，以選取要顯示的程式碼的相關資訊。 剖析器會將文字分隔為語彙基元，並接著識別這些權杖由型別和功能。  
  
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
  
 在此範例中，權杖會是字和標點符號。 語彙基元類型如下所示。  
  
|權杖名稱|語彙基元類型|  
|----------------|----------------|  
|命名空間、 類別、 公用，void、 int|keyword|  
|=|運算子|  
|{ } ( ) ;|分隔符號|  
|MyNamespace 」、 「 MyClass 」、 「 MyFunction 」、 「 arg1、 「 var1|識別項|  
|MyNamespace|namespace|  
|MyClass|Class - 類別|  
|MyFunction|方法|  
|arg1|參數|  
|var1|本機變數|  
  
 剖析器的角色是識別權杖。 某些權杖可以有一個以上的類型。 剖析器發現權杖之後，要提供實用的功能，例如語法醒目提示括號比對的資訊和 IntelliSense 作業，可以使用語言服務。  
  
## <a name="types-of-parsers"></a>類型的剖析器  
 語言服務剖析器不是編譯器的過程中使用的剖析器相同。 不過，這種剖析器必須掃描器和剖析器，用於與編譯器剖析器相同的方式。  
  
- 掃描器會用來識別的權杖類型。 反白顯示語法及快速識別語彙基元型別可以觸發其他作業，例如括號對稱，則會使用這項資訊。 此掃描器由<xref:Microsoft.VisualStudio.Package.IScanner>介面。  
  
- 剖析器用來描述函式和語彙基元的範圍。 這項資訊可在 IntelliSense 作業，來識別語言的項目，例如方法、 變數、 參數和宣告，並提供成員，以及根據內容的方法簽章的清單。 此剖析器也會用來尋找相符的語言項目組，例如大括號和括號中。 透過存取此剖析器<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法中的<xref:Microsoft.VisualStudio.Package.LanguageService>類別。  
  
  如何為您的語言服務實作的掃描器和剖析器是由您決定。 有數個資源剖析器的運作方式，以及如何撰寫您自己的剖析器也是如此。 此外，數個免費及商用產品現已推出，協助建立剖析器。  
  
### <a name="the-parsesource-parser"></a>ParseSource 剖析器  
 與做為一部分 （語彙基元會轉換為某種形式的可執行程式碼） 編譯器的剖析器，不同的語言服務剖析器可以呼叫許多不同的原因，然後在許多不同的內容。 在這種方法的實作方式<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法中的<xref:Microsoft.VisualStudio.Package.LanguageService>類別是由您決定。 請務必記住，<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>可能會在背景執行緒上呼叫方法。  
  
> [!CAUTION]
>  <xref:Microsoft.VisualStudio.Package.ParseRequest>結構包含參考<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>物件。 這<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>物件不能在背景執行緒。 事實上，許多基底的 MPF 類別不能在背景執行緒。 其中包括<xref:Microsoft.VisualStudio.Package.Source>， <xref:Microsoft.VisualStudio.Package.ViewFilter>，<xref:Microsoft.VisualStudio.Package.CodeWindowManager>類別，以及檢視與通訊的直接或間接的任何其他類別。  
  
 此剖析器通常會剖析整個來源檔案的第一個時間呼叫它，或當剖析原因值<xref:Microsoft.VisualStudio.Package.ParseReason>指定。 後續呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法處理剖析程式碼的一小部分，而且可以使用前一個完整的剖析作業的結果更快速地執行。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法進行通訊的剖析作業中透過結果<xref:Microsoft.VisualStudio.Package.AuthoringSink>和<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件。 <xref:Microsoft.VisualStudio.Package.AuthoringSink>物件用來收集特定的剖析原因，例如，範圍的資訊比對括號或有參數清單的方法簽章的資訊。 <xref:Microsoft.VisualStudio.Package.AuthoringScope>提供的宣告和方法簽章以及支援的集合移至進階的編輯選項 (**移至定義**，**移至宣告**，**移至參考**)。  
  
### <a name="the-iscanner-scanner"></a>IScanner 掃描器  
 您也必須實作可實作掃描器<xref:Microsoft.VisualStudio.Package.IScanner>。 不過，因為這個掃描器會透過以一行一行基礎<xref:Microsoft.VisualStudio.Package.Colorizer>類別，它是通常更容易實作。 在每一行的開頭，MPF 可讓<xref:Microsoft.VisualStudio.Package.Colorizer>類別要做為傳遞至掃描器的狀態變數的值。 在每一行的結尾，掃描器會傳回已更新的狀態變數。 MPF 會快取這每一行項狀態資訊，好讓掃描器可以開始從任何列剖析，而不需要來源檔案的開頭開始。 單行這個快速掃描，可讓編輯器，提供快速回饋給使用者。  
  
## <a name="parsing-for-matching-braces"></a>比對括號剖析  
 這個範例示範用於比對使用者輸入了右大括號控制流程。 在此程序，用於顏色標示的掃描器也會判斷的權杖和權杖是否觸發比對括號作業類型。 如果找到觸發程序，則<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>呼叫方法來尋找相符的大括號。 最後，會反白顯示兩個大括號。  
  
 即使大括號會在觸發程序的名稱，並剖析的原因，此程序並不限於使用實際的大括號。 支援的字元指定為一組相符的任何一對。 範例包括 （和）\<和 >，以及 [和]。  
  
 假設語言服務支援對稱的括號。  
  
1.  使用者會輸入右大括號 （}）。  
  
2.  在原始程式檔中的資料指標插入的大括號和資料指標一個進階。  
  
3.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法中的<xref:Microsoft.VisualStudio.Package.Source>類別稱為 「 以具類型的右括號。  
  
4.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法呼叫<xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>方法中的<xref:Microsoft.VisualStudio.Package.Source>類別來取得目前的游標位置之前位置的語彙基元。 這個語彙基元對應至具類型的右大括號）。  
  
    1.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>方法呼叫<xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>方法<xref:Microsoft.VisualStudio.Package.Colorizer>物件來取得目前的行上的所有權杖。  
  
    2.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>方法呼叫<xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>方法<xref:Microsoft.VisualStudio.Package.IScanner>目前這一行文字的物件。  
  
    3.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>方法會重複呼叫<xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A>方法<xref:Microsoft.VisualStudio.Package.IScanner>物件來收集所有語彙基元從目前這一行。  
  
    4.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>方法呼叫的私用方法<xref:Microsoft.VisualStudio.Package.Source>類別來取得權杖，其中包含所要的位置，並傳入的語彙基元清單取自<xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>方法。  
  
5.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法會尋找語彙基元的觸發程序旗標<xref:Microsoft.VisualStudio.Package.TokenTriggers>從傳回的權杖上<xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>方法，也就是右大括號表示語彙基元)。  
  
6.  如果觸發程序旗標<xref:Microsoft.VisualStudio.Package.TokenTriggers>找到，則<xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>方法中的<xref:Microsoft.VisualStudio.Package.Source>類別稱為。  
  
7.  <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>方法的剖析作業開頭的剖析原因值<xref:Microsoft.VisualStudio.Package.ParseReason>。 這項作業最後會呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法<xref:Microsoft.VisualStudio.Package.LanguageService>類別。 如果已啟用非同步剖析，此呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法，就會發生在背景執行緒上。  
  
8.  當剖析的作業完成時，名為內部的完成處理常式 （也稱為回呼方法）`HandleMatchBracesResponse`中稱為<xref:Microsoft.VisualStudio.Package.Source>類別。 自動進行此呼叫<xref:Microsoft.VisualStudio.Package.LanguageService>基底類別不是由剖析器。  
  
9. `HandleMatchBracesResponse`方法會取得一份範圍，從<xref:Microsoft.VisualStudio.Package.AuthoringSink>物件，會儲存在<xref:Microsoft.VisualStudio.Package.ParseRequest>物件。 (範圍是<xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>結構，指定原始程式檔中的一系列的線條及字元。)這份清單的範圍通常包含兩個範圍，其中每個左和右大括號。  
  
10. `HandleBracesResponse`方法呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>物件，會儲存在<xref:Microsoft.VisualStudio.Package.ParseRequest>物件。 這會反白顯示的指定的範圍。  
  
11. 如果<xref:Microsoft.VisualStudio.Package.LanguagePreferences>屬性<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>已啟用，`HandleBracesResponse`方法會取得包含所比對的範圍和狀態列中顯示該範圍的前 80 個字元的文字。 這適用於最<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法包含隨附於相符的配對的語言項目。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> 屬性 (Property)。  
  
12. 完成此項目。  
  
### <a name="summary"></a>總結  
 比對的大括號作業僅限於通常簡單組的語言項目。 更複雜的項目，例如比對三合一 ("`if(...)`"，"`{`"和"`}`"，或 「`else`"，"`{`"和"`}`」)，可以反白顯示文字自動完成作業的一部分。 例如，"else"word 完成時，比對"`if`」 陳述式可以反白顯示。 如果有一系列`if` / `else if`陳述式中，所有人都可以使用相同的機制，做為對稱的括號反白顯示。 <xref:Microsoft.VisualStudio.Package.Source>基底類別已經支援此做法，，如下所示： 掃描器必須傳回語彙基元的觸發程序的值<xref:Microsoft.VisualStudio.Package.TokenTriggers>結合觸發程序值<xref:Microsoft.VisualStudio.Package.TokenTriggers>游標位置之前的語彙基元。  
  
 如需詳細資訊，請參閱 <<c0> [ 舊版語言服務中的大括號比對](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)。  
  
## <a name="parsing-for-colorization"></a>剖析的顏色標示  
 色彩標示程式碼很簡單，只找出該類型的語彙基元和傳回色彩資訊的類型。 <xref:Microsoft.VisualStudio.Package.Colorizer>類別是做為編輯器和掃描器，提供有關每個語彙基元的色彩資訊之間的媒介。 <xref:Microsoft.VisualStudio.Package.Colorizer>類別會使用<xref:Microsoft.VisualStudio.Package.IScanner>物件中標示色彩列的 說明及收集的原始程式檔中的所有行的狀態資訊。 MPF 語言服務類別時，在<xref:Microsoft.VisualStudio.Package.Colorizer>類別並沒有覆寫，因為它會與掃描器通訊只能透過<xref:Microsoft.VisualStudio.Package.IScanner>介面。 提供實作的物件<xref:Microsoft.VisualStudio.Package.IScanner>介面，藉由覆寫<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法<xref:Microsoft.VisualStudio.Package.LanguageService>類別。  
  
 <xref:Microsoft.VisualStudio.Package.IScanner>掃描器有透過原始程式碼行<xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>方法。 呼叫<xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A>方法會重複直到線條會用完的權杖，取得行中的下一個 token。 用於顏色標示，MPF 會視為一串線的所有原始程式碼。 因此，掃描器必須能夠處理即將在它為線條的來源。 此外，任何一條線可以傳遞至掃描器在任何時間，而且唯一能保證掃描器會接收從行之前要掃描的狀態變數。  
  
 <xref:Microsoft.VisualStudio.Package.Colorizer>類別也用來識別權杖的觸發程序。 這些觸發程序會告訴 MPF 特定語彙基元可以起始更複雜的作業，例如文字自動完成或比對括號。 因為必須盡快識別這類觸發程序，而且必須發生在任何位置，掃描器會是最適合這項工作。  
  
 如需詳細資訊，請參閱 <<c0> [ 舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。  
  
## <a name="parsing-for-functionality-and-scope"></a>剖析功能和範圍  
 剖析功能和領域需要更多所需的動作只指出發生的語彙基元的類型。 剖析器識別不只一種權杖，但也使用權杖的功能。 比方說，識別項是只是名稱，但在您的語言，識別碼可能是類別、 命名空間、 方法或變數，根據內容的名稱。 一般類型的語彙基元可能是識別項，但識別項可能也有其他的意義，根據它是什麼，並定義的位置。 這個識別必須有更廣泛的知識，有關正在剖析的語言剖析器。 這正是<xref:Microsoft.VisualStudio.Package.AuthoringSink>進來的類別。 <xref:Microsoft.VisualStudio.Package.AuthoringSink>類別會收集識別項、 方法、 相符的語言組 （例如大括號和括號） 和語言的一組相關的資訊 (但不包含有三個部分，例如，類似的語言組"`foreach()`""`{`"和"`}`」)。 此外，您可以覆寫<xref:Microsoft.VisualStudio.Package.AuthoringSink>類別，以支援程式碼識別，其會在早期驗證中斷點以便偵錯工具並沒有載入，而 **[自動變數]** 偵錯視窗中，顯示本機變數和參數自動當程式正在偵錯，並需要找出適當的本機變數和參數，除了偵錯工具會顯示剖析器。  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink>物件的一部分，會傳遞給剖析器<xref:Microsoft.VisualStudio.Package.ParseRequest>物件，而新<xref:Microsoft.VisualStudio.Package.AuthoringSink>物件是每次建立新<xref:Microsoft.VisualStudio.Package.ParseRequest>建立物件。 颾魤 ㄛ<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法必須傳回<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件，用來處理各種 IntelliSense 作業。 <xref:Microsoft.VisualStudio.Package.AuthoringScope>物件會維護宣告的清單，以及方法中，清單可能是其中已填入，根據剖析的原因。 <xref:Microsoft.VisualStudio.Package.AuthoringScope>類別必須實作。  
  
## <a name="see-also"></a>另請參閱  
 [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [舊版語言服務概觀](../../extensibility/internals/legacy-language-service-overview.md)   
 [舊版語言服務中的語法上色](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [舊版語言服務中的括號對稱](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)