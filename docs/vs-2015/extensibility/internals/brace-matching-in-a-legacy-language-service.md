---
title: 舊版語言服務中的比對的大括號 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 70ad3062a4cbbce8ef46c3afe8851382949fe3f3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753218"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>舊版語言服務中的括號對稱
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

大括號比對，可協助開發人員追蹤發生在一起，例如括號和大括號所需要的語言項目。 當開發人員輸入右括號時，左括號會反白顯示。  
  
 您可以比對兩個或三個共同發生的項目，稱為組和三合一。 三合一是共同發生的三個元素的集合。 比方說，在 C# 中，`foreach`陳述式構成三重物件:"`foreach()`"，"`{`"，和 「`}`"。 輸入右括號時，會反白顯示三個項目。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新的方式是使用 MEF 擴充功能。 若要深入了解實作大括號比對的新方式，請參閱[逐步解說︰ 顯示對稱的括號](../../extensibility/walkthrough-displaying-matching-braces.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 盡。 這會改善您的語言服務的效能，並可讓您充分利用新編輯器功能。  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink>類別支援這兩組，而且與 triples<xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A>和<xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A>方法。  
  
## <a name="implementation"></a>實作  
 語言服務，就必須找出在語言中的所有相符項目，然後找出所有配對。 這通常透過實作<xref:Microsoft.VisualStudio.Package.IScanner>來偵測相符的語言，然後使用<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>項目相符的方法。  
  
 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法呼叫來 token 化列，並傳回之前插入號的語彙基元掃描器。 掃描器會指出，找到語言項目配對權杖的觸發程序將值設定為<xref:Microsoft.VisualStudio.Package.TokenTriggers>上目前的語彙基元。 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法呼叫<xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>接著會呼叫的方法<xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A>方法的剖析原因值<xref:Microsoft.VisualStudio.Package.ParseReason>找出相符的語言項目。 找到相符的語言項目時，會反白顯示兩個項目。  
  
 輸入一個大括號如何觸發的大括號反白顯示的完整說明，請參閱主題中的 「 範例剖析作業 」 區段[舊版語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)。  
  
## <a name="enabling-support-for-brace-matching"></a>啟用支援的括號對稱  
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>屬性可以設定`MatchBraces`， `MatchBracesAtCaret`，以及`ShowMatchingBrace`具名參數設定的對應屬性<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別。 使用者也可以設定語言喜好設定的屬性。  
  
|登錄項目|屬性|描述|  
|--------------------|--------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|啟用括號對稱|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|移動插入號所在的啟用括號對稱。|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|反白顯示對稱的括號。|  
  
## <a name="matching-conditional-statements"></a>比對條件陳述式  
 可以比對條件陳述式，例如`if`， `else if`，並`else`，或`#if`， `#elif`， `#else`， `#endif`，做為相符的分隔符號相同的方式。 您可以進行子分類<xref:Microsoft.VisualStudio.Package.AuthoringSink>類別，並提供可以加上文字的方法跨越以及要內部陣列的相符項目分隔符號。  
  
## <a name="setting-the-trigger"></a>設定觸發程序  
 下列範例示範如何偵測相符的括號、 大括號和方括號，和在掃描器上設定它的觸發程序。 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法<xref:Microsoft.VisualStudio.Package.Source>類別會偵測觸發程序，並呼叫的剖析器來尋找相符的配對 （請參閱本主題的 「 尋找比對 」 一節）。 這個範例是僅供示範用途。 它會假設您的掃描器，包含方法`GetNextToken`的識別，並從文字行，傳回權杖。  
  
```csharp  
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
  
## <a name="matching-the-braces"></a>比對大括號  
 以下是簡化的範例相符語言項目 {}、 （） 和 []，並加入其範圍<xref:Microsoft.VisualStudio.Package.AuthoringSink>物件。 這個方法並不建議的方法來剖析原始程式碼;它是僅供示範用途。  
  
```csharp  
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
  
## <a name="see-also"></a>另請參閱  
 [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [舊版語言服務的剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

