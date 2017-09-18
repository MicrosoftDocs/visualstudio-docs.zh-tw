---
title: "舊版語言服務中的比對括號 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "括號對稱"
  - "語言服務 [受管理的封裝 framework] 括號對稱"
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# 舊版語言服務中的比對括號
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

大括號比對，可協助開發人員追蹤需要一起發生，例如括號和大括號的語言項目。 當開發人員輸入右括號時，左括號會反白顯示。  
  
 您可以比對兩個或三個共同發生的項目，稱為組和三合一。 三合一是共同發生的三個元素的集合。 比方說，在 C\# 中， `foreach` 陳述式構成 triple:"`foreach()`"，"`{`」，和 「`}`」。 輸入右括號時，會反白顯示三個項目。  
  
 舊版的語言服務會實作成，VSPackage 的一部分，但實作語言服務功能的較新的方法是使用 MEF 延伸模組。 若要了解有關實作括號對稱的新方法的詳細資訊，請參閱 [逐步解說︰ 顯示對稱的括號](../../extensibility/walkthrough-displaying-matching-braces.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會改善語言服務的效能，並可讓您充分利用新編輯器功能。  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 類別支援配對，而且與 triples <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> 和 <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> 方法。  
  
## 實作  
 語言服務需要找出在語言中的所有相符項目，然後找出所有配對成功。 這通常透過實作 <xref:Microsoft.VisualStudio.Package.IScanner> 偵測相符的語言，然後使用 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法來比對項目。  
  
 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 方法呼叫來 token 化列，並傳回之前插入號的語彙基元的掃描程式。 掃描器表示語言項目組已找到的語彙基元的觸發程序將值設定為 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 上目前的語彙基元。<xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 方法呼叫 <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> 方法，接著呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> 剖析原因值的方法 <xref:Microsoft.VisualStudio.Package.ParseReason> 來尋找相符的語言項目。 找到相符的語言項目時，會反白顯示兩個項目。  
  
 輸入一個大括號如何觸發，大括號反白顯示的完整說明，請參閱本主題的 「 範例剖析作業 」 一節 [舊版的語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)。  
  
## 啟用支援括號對稱  
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 屬性可以設定 `MatchBraces`, ，`MatchBracesAtCaret`, ，和 `ShowMatchingBrace` 具名參數所設定的對應屬性 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 類別。 使用者也可以設定語言喜好設定的屬性。  
  
|登錄項目|屬性|描述|  
|----------|--------|--------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|啟用括號對稱|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|啟用插入號移比對括號。|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|反白顯示對稱的括號。|  
  
## 比對的條件陳述式  
 可以比對條件陳述式，例如 `if`, ，`else if`, ，和 `else`, ，或 `#if`, ，`#elif`, ，`#else`, ，`#endif`, ，做為分隔符號比對相同的方式。 您可以子類別 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 類別，並提供可以加入文字的方法，跨越以及內部陣列的相符項目分隔符號。  
  
## 設定觸發程序  
 下列範例示範如何偵測到相符的括號、 大括號和方括號，以及掃描程式設定它的觸發程序。<xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 方法 <xref:Microsoft.VisualStudio.Package.Source> 類別偵測到觸發程序，並呼叫剖析器來尋找相符的配對 （請參閱本主題的 「 尋找相符項目 」 一節）。 這個範例是僅供示範用途。 它會假設您的掃描器都包含一種方法 `GetNextToken` ，識別，並傳回權杖，從一行文字。  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private const string braces = "()[]{}";  
        private Lexer lex;  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false;  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char firstChar = token[0];  
                if (Char.IsPunctuation(firstChar) && token.Length > 0)  
                {  
                    if (braces.IndexOf(firstChar) != -1)  
                    {  
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;  
                    }  
                }  
            }  
            return foundToken;  
        }  
```  
  
## 比對大括號  
 以下是一個簡單的例子，相符的語言項目 {}、 （） 和 \[\]，並加入其範圍 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 物件。 此方法不是建議的方法來剖析程式碼。它是僅供示範用途。  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class Parser  
    {  
         private IList<TextSpan[]> m_braces;  
         public IList<TextSpan[]> Braces  
         {  
             get { return m_braces; }  
         }  
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)  
         {  
             if IsMatch(braceSpan1, braceSpan2)  
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });  
         }  
  
         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)  
         {  
             //definition for matching here  
          }  
    }  
  
    public class TestLanguageService : LanguageService  
    {  
         Parser parser = new Parser();  
         Source source = (Source) this.GetSource(req.FileName);  
  
         private AuthoringScope ParseSource(ParseRequest req)  
         {  
             if (req.Sink.BraceMatching)  
             {  
                 if (req.Reason==ParseReason.MatchBraces)  
                 {  
                     foreach (TextSpan[] brace in parser.Braces)  
                     {  
                         req.Sink.MatchPair(brace[0], brace[1], 1);  
                     }  
                 }  
             }  
             return new TestAuthoringScope();  
         }  
    }  
}  
```  
  
## 請參閱  
 [舊版的語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [舊版的語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)