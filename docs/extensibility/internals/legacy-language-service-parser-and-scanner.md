---
title: "舊版的語言服務剖析器和掃描器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "剖析器，語言服務 [受管理的封裝 framework]"
  - "語言服務 [受管理的封裝 framework] 剖析器"
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 舊版的語言服務剖析器和掃描器
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

剖析器做為語言服務的核心。 管理封裝架構 \(MPF\) 語言類別，需要的語言剖析器，以選取要顯示的程式碼的相關資訊。 剖析器將文字分成語彙基元，並再找出這些語彙基元型別和功能。  
  
## 討論  
 以下是 C\# 方法。  
  
```c#  
namespace MyNamespace { class MyClass { public void MyFunction(int arg1) { int var1 = arg1; } } }  
```  
  
 在此範例中的權杖是字和標點符號。 種類的語彙基元如下所示。  
  
|語彙基元名稱|語彙基元類型|  
|------------|------------|  
|命名空間、 類別、 public void，int|keyword|  
|\=|運算子|  
|{ } \( \) ;|分隔符號|  
|MyNamespace、 MyClass、 MyFunction、 arg1、 var1|識別項|  
|MyNamespace|namespace|  
|MyClass|Class \- 類別|  
|MyFunction|方法|  
|arg1|參數|  
|var1|區域變數|  
  
 剖析器的角色是識別權杖。 某些權杖可以有一個以上的類型。 剖析器已識別的語彙基元之後，語言服務可以使用的資訊可以提供有用的功能，例如語法反白顯示，大括號比對和 IntelliSense 的操作。  
  
## 剖析器的類型  
 語言服務剖析器不是編譯器的一部分的剖析器相同。 不過，這種剖析器需要使用掃描器和剖析器，編譯器剖析器方式相同。  
  
-   掃描器用來識別的權杖類型。 反白顯示語法及快速識別語彙基元型別可以觸發其他作業，例如，括號對稱，則會使用此資訊。 此程式由 <xref:Microsoft.VisualStudio.Package.IScanner> 介面。  
  
-   剖析器用來描述函式和範圍的語彙基元。 這項資訊用於 IntelliSense 作業，以識別語言項目，例如方法、 變數、 參數和宣告，並提供成員與方法簽章內容為基礎的清單。 這個剖析器也會用來尋找相符的語言項目組，例如大括號和括號中。 這個剖析器會透過存取 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法中的 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別。  
  
 如何為您的語言服務實作掃描器和剖析器是由您決定。 有數個資源的描述剖析器的運作方式，以及如何撰寫自己的剖析器。 此外，有許多免費及商用產品，協助建立剖析器。  
  
### ParseSource 剖析器  
 不同於使用的編譯器 \(語彙基元會轉換為某種形式的可執行程式碼\) 的一部分的剖析器，可以有許多原因，並在許多不同的內容中呼叫語言服務剖析器。 在這種方法的實作方式 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法中的 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別是由您決定。 請務必記住， <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 可能會在背景執行緒上呼叫方法。  
  
> [!CAUTION]
>  <xref:Microsoft.VisualStudio.Package.ParseRequest> 結構包含的參考 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 物件。 這 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 物件不能用在背景執行緒。 事實上，許多基底的 MPF 類別不能在背景執行緒。 這些包括 <xref:Microsoft.VisualStudio.Package.Source>, ，<xref:Microsoft.VisualStudio.Package.ViewFilter>, ，<xref:Microsoft.VisualStudio.Package.CodeWindowManager> 類別，以及直接或間接與檢視通訊的任何其他類別。  
  
 這個剖析器通常會剖析整個來源檔案的第一個時間呼叫它，或當剖析原因值 <xref:Microsoft.VisualStudio.Package.ParseReason> 指定。 後續呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法處理剖析程式碼的一小部分，並使用前一個完整的剖析作業的結果可以更快速地執行。<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法通訊透過在剖析作業結果 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 和 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 物件。<xref:Microsoft.VisualStudio.Package.AuthoringSink> 物件用來收集資訊針對特定的剖析原因，例如，範圍的資訊比對括號或具有參數清單的方法簽章。<xref:Microsoft.VisualStudio.Package.AuthoringScope> 提供的宣告和方法簽章以及支援的集合移至進階的編輯選項 \(**移至定義**, ，**移至宣告**, ，**移至參考**\)。  
  
### IScanner 掃描器  
 您也必須實作可實作掃描器 <xref:Microsoft.VisualStudio.Package.IScanner>。 不過，因為此程式的運作方式透過一行一行基礎 <xref:Microsoft.VisualStudio.Package.Colorizer> 類別，它是通常比較容易實作。 在每一行的開頭，讓 MPF <xref:Microsoft.VisualStudio.Package.Colorizer> 類別做為傳遞至掃描器的狀態變數的值。 在每一行的結尾，掃描器會傳回更新的狀態變數。 MPF 快取此狀態資訊的每一行，以便掃描器可以開始剖析從任何列，而不需要原始程式檔的開頭開始。 單行這個快速掃描，可讓編輯器\] 提供快速回饋給使用者。  
  
## 比對括號剖析  
 此範例顯示用於比對與使用者輸入右括號控制流程。 此程序，用於顏色標示的掃描程式也用來決定的權杖和權杖是否可以觸發比對括號作業類型。 如果找到觸發程序，則 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 會呼叫方法來尋找相符的大括號。 最後，會反白顯示兩個大括號。  
  
 即使大括號可以用在觸發程序的名稱，並剖析原因，此程序並不限於實際的大括號。 支援任何一組字元，指定要相符的配對。 範例包括 \(且\)、 \< 和 \> 和 \[和\]。  
  
 假設語言服務支援對稱的括號。  
  
1.  使用者會輸入右大括號 \(}\)。  
  
2.  原始程式檔中的游標處插入的大括號和資料指標一個進階。  
  
3.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 方法中的 <xref:Microsoft.VisualStudio.Package.Source> 類別稱為具類型的右大括號。  
  
4.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 方法呼叫 <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 方法中的 <xref:Microsoft.VisualStudio.Package.Source> 類別，以取得位於目前的游標位置之前的語彙基元。 這個語彙基元對應至具類型的右大括號\)。  
  
    1.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 方法呼叫 <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 方法 <xref:Microsoft.VisualStudio.Package.Colorizer> 物件來取得目前的行上的所有權杖。  
  
    2.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 方法呼叫 <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> 方法 <xref:Microsoft.VisualStudio.Package.IScanner> 物件包含目前行的文字。  
  
    3.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 方法會重複呼叫 <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> 方法 <xref:Microsoft.VisualStudio.Package.IScanner> 物件來收集所有權杖，從目前這一行。  
  
    4.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 方法會呼叫私用方法中 <xref:Microsoft.VisualStudio.Package.Source> 類別來取得權杖，其中包含所要的位置，並從傳入的語彙基元清單取得 <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 方法。  
  
5.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 方法會尋找語彙基元的觸發程序旗標為 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 從傳回的權杖上 <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 方法，也就是代表右大括號的語彙基元\)。  
  
6.  如果觸發程序的旗標的 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 找到，則 <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> 方法中的 <xref:Microsoft.VisualStudio.Package.Source> 類別呼叫。  
  
7.  <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> 方法開頭的剖析原因值剖析作業 <xref:Microsoft.VisualStudio.Package.ParseReason>。 這項作業最後呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別。 如果已啟用非同步剖析，此呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法就會發生在背景執行緒上。  
  
8.  當剖析作業完成時，名為內部完成處理常式 \(也稱為回呼方法\) `HandleMatchBracesResponse` 中呼叫 <xref:Microsoft.VisualStudio.Package.Source> 類別。 自動進行這個呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService> 基底類別不是由剖析器。  
  
9. `HandleMatchBracesResponse` 方法會取得一份範圍從 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 物件儲存在 <xref:Microsoft.VisualStudio.Package.ParseRequest> 物件。 \(Span <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> 原始程式檔中指定的線條或字元範圍的結構。\) 這份清單的範圍通常包含兩個範圍，每個左和右括號。  
  
10. `HandleBracesResponse` 方法呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> 方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 物件儲存在 <xref:Microsoft.VisualStudio.Package.ParseRequest> 物件。 這會反白顯示指定的範圍。  
  
11. 如果 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 屬性 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> 已啟用， `HandleBracesResponse` 方法會取得比對範圍所包含，並在狀態列中顯示該範圍的第一次 80 個字元的文字。 這最適合如果 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法包含隨附一組相符的語言項目。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> 屬性 \(Property\)。  
  
12. 完成。  
  
### 總結  
 比對的大括號作業是通常只有簡單組語言項目。 更複雜的項目，例如比對三合一 \("`if(…)`"，"`{`"和"`}`"，或"`else`"，"`{`"和"`}`」\)，可以反白顯示文字完成作業的一部分。 例如，"else"word 完成時，比對"`if`"陳述式可以反白顯示。 如果有一系列的 `if`\/`else if` 陳述式，全部都可以使用相同的機制，做為比對括號反白顯示。<xref:Microsoft.VisualStudio.Package.Source> 基底類別已經支援，，如下所示: 掃描器必須傳回的語彙基元的觸發程序值 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 結合與觸發程序值 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 游標位置之前的語彙基元。  
  
 如需詳細資訊，請參閱[舊版語言服務中的比對括號](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)。  
  
## 剖析顏色標示  
 色彩標示程式碼很簡單，只是識別該類型的權杖，並傳回色彩資訊的類型。<xref:Microsoft.VisualStudio.Package.Colorizer> 類別是做為編輯器和掃描器，以提供有關每個權杖的色彩資訊之間的媒介。<xref:Microsoft.VisualStudio.Package.Colorizer> 類別會使用 <xref:Microsoft.VisualStudio.Package.IScanner> 物件上色功能列中的 \[說明及收集的原始程式檔中的所有行的狀態資訊。 在 MPF 語言服務類別中， <xref:Microsoft.VisualStudio.Package.Colorizer> 類別沒有覆寫，因為它與掃描器通訊只能透過 <xref:Microsoft.VisualStudio.Package.IScanner> 介面。 提供實作的物件 <xref:Microsoft.VisualStudio.Package.IScanner> 藉由覆寫介面 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 方法 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別。  
  
 <xref:Microsoft.VisualStudio.Package.IScanner> 掃描器有透過原始程式碼行 <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> 方法。 呼叫 <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> 方法會重複直到行已用完的語彙基元取得行中的下一個語彙基元。 顏色標示、 MPF 會視為一連串的程式碼行中所有原始程式碼。 因此，掃描器必須能夠應付為線條即將在它的來源。 此外，任何列可以在任何時間，傳遞至掃描器，唯一能保證是，掃描器便會收到狀態變數的行之前要掃描。  
  
 <xref:Microsoft.VisualStudio.Package.Colorizer> 類別也可以用來識別權杖的觸發程序。 這些觸發程序告訴 MPF 特定語彙基元可以起始更複雜的作業，例如文字完成或比對括號。 由於識別這類觸發程序必須盡快，而且必須發生在任何位置，掃描器最適合這項工作。  
  
 如需詳細資訊，請參閱[語法色彩標示在舊版語言服務](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)。  
  
## 剖析功能和領域  
 剖析功能和領域需要較多的工作，比只識別遇到的語彙基元類型。 剖析器已識別的類型語彙基元，不僅權杖用的功能。 例如，識別項是只有名稱，但您的語言識別項可能是類別、 命名空間、 方法或變數，根據內容的名稱。 一般類型的語彙基元可能是識別項，但識別項，也可能有其他的意義，根據它是什麼，以及定義所在。 這個識別需要具備更廣泛的知識要剖析的語言相關的剖析器。 這正是 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 進來的類別。<xref:Microsoft.VisualStudio.Package.AuthoringSink> 類別會收集識別項、 方法、 相符的語言組 \(例如大括號和括號\) 和語言三合一的相關資訊 \(除了會有三個部分，例如，類似的語言組"`foreach()`""`{`"和"`}`」\)。 此外，您可以覆寫 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 類別，以支援程式碼識別，會使用在早期驗證中的中斷點，以便偵錯工具並沒有載入，而 **自動變數** 偵錯視窗，顯示區域變數和參數自動時進行偵錯的程式，並需要找出適當的本機變數和參數，除了偵錯工具顯示剖析器。  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 物件的一部分，會傳遞給剖析器 <xref:Microsoft.VisualStudio.Package.ParseRequest> 物件，並新增 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 物件是每次建立新 <xref:Microsoft.VisualStudio.Package.ParseRequest> 建立物件。 此外， <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法必須傳回 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 物件，用來處理各種 IntelliSense 作業。<xref:Microsoft.VisualStudio.Package.AuthoringScope> 物件會維護一份宣告清單和清單的方法，是其中已填入，根據剖析的原因。<xref:Microsoft.VisualStudio.Package.AuthoringScope> 類別必須實作。  
  
## 請參閱  
 [實作傳統語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [舊版的語言服務概觀](../../extensibility/internals/legacy-language-service-overview.md)   
 [語法色彩標示在舊版語言服務](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [舊版語言服務中的比對括號](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)