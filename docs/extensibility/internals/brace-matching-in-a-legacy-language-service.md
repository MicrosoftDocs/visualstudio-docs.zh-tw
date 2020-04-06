---
title: 舊語言服務中的大括弧匹配 |微軟文件
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
ms.openlocfilehash: 0081be3e3ab5a53f7d85f77475d4288aa5c87092
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709810"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>舊語言服務中的支撐符合
大括弧匹配可説明開發人員跟蹤需要一起出現的語言元素,例如括弧和大括弧。 當開發人員進入關閉大括弧時,打開大括弧將突出顯示。

 您可以匹配兩個或三個共發生的元素,稱為對和三重元素。 三重組是三個共發生元素集。 例如,在 C#`foreach`中 ,語句`foreach()`形成`{`三`}`重 : 和 。 鍵入右大括弧時,所有三個元素都突出顯示。

 舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解有關實現大括弧匹配的新方法的更多,請參閱[演練:顯示匹配大括弧](../../extensibility/walkthrough-displaying-matching-braces.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將提高語言服務的性能,並允許您利用新的編輯器功能。

 類<xref:Microsoft.VisualStudio.Package.AuthoringSink>支援 對和三<xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A>重<xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A>與和 方法。

## <a name="implementation"></a>實作
 語言服務需要標識語言中的所有匹配元素,然後找到所有匹配對。 這通常是通過實現<xref:Microsoft.VisualStudio.Package.IScanner>來檢測匹配的語言<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>, 然後使用 方法匹配元素來實現的。

 該方法<xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>調用掃描器標記行並在 caret 之前返回權杖。 掃描程式指示通過在當前權杖上設置的<xref:Microsoft.VisualStudio.Package.TokenTriggers>令牌觸發器值找到語言元素對。 該方法<xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>調用<xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>的方法 ,該方法反過來<xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A>調用 該方法具有<xref:Microsoft.VisualStudio.Package.ParseReason>解析原因值 以查找匹配的語言元素。 找到匹配的語言元素時,這兩個元素都會突出顯示。

 有關鍵入大括弧如何觸發大括弧突出顯示的完整說明,請參閱文章[「舊語言服務解析器」和「掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)」中的 *「示例解析」操作*部分。

## <a name="enable-support-for-brace-matching"></a>開啟對大括弧符合的支援
 該<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>屬性可以設置**匹配Braces、MatchBracesAtCaret**和**ShowMatchBrace**註冊表項,<xref:Microsoft.VisualStudio.Package.LanguagePreferences>這些註冊表項設置**MatchBracesAtCaret**類的相應屬性。 也可以由用戶設置語言首選項屬性。

|登錄項目|屬性|描述|
|--------------------|--------------|-----------------|
|匹配支架|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|啟用大括弧匹配。|
|符合支架AtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|啟用大括弧匹配,因為護理器移動。|
|顯示符合支架|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|突出顯示匹配的大括弧。|

## <a name="match-conditional-statements"></a>符合條件語句
 `if`可以匹配條件語句,如、`else if``else``#if``#elif``#else`、、、、`#endif`與與符合分隔符相同。 可以對類進行類<xref:Microsoft.VisualStudio.Package.AuthoringSink>子類,並提供一個方法,可以將文本範圍以及分隔符添加到匹配元素的內部數組中。

## <a name="set-the-trigger"></a>設定觸發器
 下面的示例演示如何檢測匹配的括弧、大括弧和方形大括弧,以及如何在掃描器中為其設置觸發器。 類<xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A><xref:Microsoft.VisualStudio.Package.Source>上的方法檢測觸發器並調用解析器以查找匹配對(請參閱本文中的 *"查找匹配*"部分)。 此示例僅用於說明目的。 它假定掃描器包含一個標識和返回`GetNextToken`文本行中的權杖的方法。

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
 下面是一個用於匹配語言`{ }``( )`元素`[ ]`和 以及將其範圍添加到<xref:Microsoft.VisualStudio.Package.AuthoringSink>物件中的 簡化範例。 此方法不是分析原始程式碼的建議方法;因此,此方法不是分析原始程式碼的方法。僅用於說明目的。

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
- [傳統語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)
- [舊語言服務解析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
