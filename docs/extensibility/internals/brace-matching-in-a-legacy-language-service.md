---
title: "大括號比對以舊版語言服務 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c496c65244f0ede0c3a6385f6cf1329479a17c22
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="brace-matching-in-a-legacy-language-service"></a>大括號比對以舊版語言服務
大括號比對，可協助開發人員追蹤需要一起發生，例如括弧和大括號的語言項目。 當開發人員輸入右括號時，左括號會反白顯示。  
  
 您可以比對兩個或三個共同發生的項目，稱為組和三合一。 三合一是共同發生的三個元素的集合。 比方說，在 C# 中，`foreach`陳述式構成 triple:"`foreach()`"，"`{`」，和 「`}`"。 輸入右括號時，會反白顯示三個項目。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新方法是使用 MEF 擴充功能。 若要了解有關實作括號對稱的新方法的詳細資訊，請參閱[逐步解說： 顯示對稱的括號](../../extensibility/walkthrough-displaying-matching-braces.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會提升語言服務的效能，並可讓您充分利用新編輯器功能。  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink>類別支援這兩組，而且與 triples<xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A>和<xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A>方法。  
  
## <a name="implementation"></a>實作  
 語言服務需要識別在語言中的所有相符項目，然後找出所有配對。 這通常透過實作<xref:Microsoft.VisualStudio.Package.IScanner>來偵測相符的語言，然後將<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法來比對項目。  
  
 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法呼叫來 token 化列，並傳回之前插入號的語彙基元掃描器。 掃描器表示發現已透過設定語彙基元的觸發程序值的語言項目組<xref:Microsoft.VisualStudio.Package.TokenTriggers>上目前的語彙基元。 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法呼叫<xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>會依序呼叫的方法<xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A>方法以剖析原因值<xref:Microsoft.VisualStudio.Package.ParseReason>來尋找相符的語言項目。 找到相符的語言項目時，會反白顯示兩個項目。  
  
 輸入大括號如何觸發，大括號反白顯示的完整說明，請參閱主題中的 「 範例剖析作業 」 區段[舊版語言服務剖析器與掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)。  
  
## <a name="enabling-support-for-brace-matching"></a>啟用支援括號對稱  
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>屬性可以設定`MatchBraces`， `MatchBracesAtCaret`，和`ShowMatchingBrace`名為設定的對應屬性參數<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別。 使用者也可以設定語言喜好設定的屬性。  
  
|登錄項目|屬性|描述|  
|--------------------|--------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|啟用括號對稱|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|移動插入號所在的啟用括號對稱。|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|反白顯示對稱的括號。|  
  
## <a name="matching-conditional-statements"></a>比對的條件陳述式  
 您也可以符合條件陳述式，例如`if`， `else if`，和`else`，或`#if`， `#elif`， `#else`， `#endif`，方式與相符的分隔符號相同。 您可以子類別化為<xref:Microsoft.VisualStudio.Package.AuthoringSink>類別，並提供要在內部陣列的相符項目分隔符號以及跨越可以加入文字的方法。  
  
## <a name="setting-the-trigger"></a>設定觸發程序  
 下列範例顯示如何偵測相符的括號、 大括號和方括號，以及設定觸發程序，於掃描器中。 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法<xref:Microsoft.VisualStudio.Package.Source>類別偵測到觸發程序，呼叫以尋找相符的配對 （請參閱本主題的 「 尋找相符項目 」 一節） 剖析器。 這個範例是僅供說明。 它會假設您的掃描器包含方法`GetNextToken`的識別，並傳回從文字行的語彙基元。  
  
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
  
## <a name="matching-the-braces"></a>對稱的括號  
 以下是相符的語言項目 {}、 （） 和 []，並加入其範圍的簡化的範例<xref:Microsoft.VisualStudio.Package.AuthoringSink>物件。 這個方法並不是建議的方法來剖析原始程式碼。它是僅供說明。  
  
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
  
## <a name="see-also"></a>請參閱  
 [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [舊版語言服務的剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)