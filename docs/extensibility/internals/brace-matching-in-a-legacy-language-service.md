---
title: 舊版語言服務中的括弧對稱 |Microsoft Docs
description: 深入瞭解舊版語言服務中的大括弧比對，可協助您追蹤必須一起發生的語言專案，例如括弧和大括弧。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d9f93f0081d45e986ab6845cdaee53209b84e13
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190001"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>舊版語言服務中的括弧對稱
括弧對稱可協助開發人員追蹤需要一起發生的語言元素，例如括弧和大括弧。 當開發人員輸入右大括弧時，會反白顯示左大括弧。

 您可以比對兩個或三個共發生的元素，稱為「配對」和「三合一」。 三元組是三個共發生元素的集合。 例如，在 c # 中， `foreach` 語句形成三種： `foreach()` 、 `{` 和 `}` 。 當輸入右大括弧時，就會反白顯示所有三個元素。

 舊版語言服務會實作為 VSPackage 的一部分，但是執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解如何執行大括弧比對的新方式，請參閱 [逐步解說：顯示成對的大括弧](../../extensibility/walkthrough-displaying-matching-braces.md)。

> [!NOTE]
> 建議您儘快開始使用新的編輯器 API。 這可改善您的語言服務效能，並讓您利用新的編輯器功能。

 <xref:Microsoft.VisualStudio.Package.AuthoringSink>類別支援搭配和方法的成對和三 <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> 合一 <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> 。

## <a name="implementation"></a>實作
 語言服務需要識別語言中所有相符的專案，然後找到所有相符的配對。 這通常是藉由實 <xref:Microsoft.VisualStudio.Package.IScanner> 作為偵測相符的語言，然後使用方法來比對專案來達成 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 。

 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法會呼叫掃描器來 token 化這一行，並在插入號之前傳回權杖。 掃描器會藉由 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 在目前的權杖上設定的 token 觸發程式值，來指出已找到語言元素組。 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>方法 <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> 會呼叫方法，而這個方法會接著 <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> 使用的剖析原因值來呼叫方法， <xref:Microsoft.VisualStudio.Package.ParseReason> 以找出相符的語言元素。 找到相符的語言專案時，會反白顯示這兩個元素。

 如需如何鍵入括弧來觸發括弧醒目提示的完整說明，請參閱 [舊版語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)一文中的 *範例剖析* 作業一節。

## <a name="enable-support-for-brace-matching"></a>啟用括弧配對的支援
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>屬性可以設定 **MatchBraces**、 **MatchBracesAtCaret** 和 **ShowMatchingBrace** 登錄專案，以設定類別的對應屬性 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 。 語言喜好設定屬性也可以由使用者設定。

|登錄項目|屬性|描述|
|--------------------|--------------|-----------------|
|MatchBraces|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|啟用括弧對稱。|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|當插入點移動時啟用括弧比對。|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|反白顯示相符的括弧。|

## <a name="match-conditional-statements"></a>符合條件陳述式
 您可以將條件陳述式（如、、和、、、、）與相符 `if` `else if` `else` `#if` `#elif` `#else` `#endif` 分隔符號的相同方式進行比對。 您可以將 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 類別子類別化，並提供可將文字範圍和分隔符號加入至相符元素內部陣列的方法。

## <a name="set-the-trigger"></a>設定觸發程式
 下列範例顯示如何在掃描器中偵測相符的括弧、大括弧和方括弧，以及設定它的觸發程式。 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>類別上的方法會 <xref:Microsoft.VisualStudio.Package.Source> 偵測觸發程式，並呼叫剖析器來尋找相符的配對 (請參閱本文中的 *尋找相符* 區段) 。 此範例僅供說明之用。 它會假設您的掃描器包含一個方法 `GetNextToken` ，該方法會從文字行識別並傳回權杖。

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

## <a name="match-the-braces"></a>符合大括弧
 以下是比對語言元素 `{ }` 、 `( )` 和 `[ ]` ，以及將其範圍加入至物件的簡化範例 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 。 這種方法不是剖析原始程式碼的建議方法;它僅供說明之用。

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
- [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)
- [舊版語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
