---
title: 舊版語言服務 2 中的參數資訊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 57c5516c70819f8f86d56e93f78ec5d877c72a78
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640372"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>舊版語言服務中的參數資訊
IntelliSense 的 參數資訊就是當使用者輸入的參數清單時，會顯示方法的簽章的工具提示開始字元 （通常是左括號） 的方法參數清單。 在輸入每個參數及參數分隔符號 （通常為逗號） 型別時，工具提示會更新以顯示下一個參數以粗體顯示。

 Managed 的封裝架構 (MPF) 類別提供管理參數資訊工具提示的支援。 參數會啟動，參數接下來，而且參數結尾字元，而且必須提供的方法簽章和其相關聯的參數清單，就必須偵測剖析器。

 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新的方式是使用 MEF 擴充功能。 若要深入了解，請參閱[擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。

> [!NOTE]
>  我們建議您開始使用新的編輯器 API 盡。 這會改善您的語言服務的效能，並可讓您充分利用新編輯器功能。

## <a name="implementation"></a>實作
 剖析器應設定觸發程序值<xref:Microsoft.VisualStudio.Package.TokenTriggers>設定當它找到的參數清單開始字元 （通常左括號）。 它應該設定<xref:Microsoft.VisualStudio.Package.TokenTriggers>找到參數分隔符號 （通常是以逗號） 時，觸發程序。 這會導致更新，而且以粗體顯示的下一個參數的參數資訊工具提示。 剖析器應設定觸發程序值<xref:Microsoft.VisualStudio.Package.TokenTriggers>時如果找到參數清單結尾字元 （通常右括號）。

 <xref:Microsoft.VisualStudio.Package.TokenTriggers>觸發程序值開始呼叫<xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A>方法，再呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法的剖析器剖析原因為<xref:Microsoft.VisualStudio.Package.ParseReason>。 如果剖析器會判斷之前參數清單開始字元的識別碼是可辨識的方法名稱，它會傳回一份在方法簽章相符<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件。 如果找不到任何方法簽章，就會顯示在清單中的第一個簽章的參數資訊工具提示。 依照多個簽章的輸入，然後更新此工具提示。 參數清單結尾字元輸入時，會從檢視中移除的參數資訊工具提示。

> [!NOTE]
>  若要確保已正確格式化的參數資訊工具提示，您必須覆寫的屬性上<xref:Microsoft.VisualStudio.Package.Methods>類別，以提供適當的字元。 基底<xref:Microsoft.VisualStudio.Package.Methods>類別假設 C#-樣式方法簽章。 請參閱<xref:Microsoft.VisualStudio.Package.Methods>類別，如需有關如何完成。

## <a name="enabling-support-for-the-parameter-info"></a>啟用支援的參數資訊
 若要支援的參數資訊工具提示，您必須設定`ShowCompletion`具名的參數<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>至`true`。 語言服務會讀取此登錄項目的值從<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>屬性。

 颾魤 ㄛ<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A>屬性必須設為`true`參數資訊工具提示會顯示。

### <a name="example"></a>範例
 以下是一個簡單的例子，偵測參數清單的字元，並設定適當的觸發程序。 這個範例是僅供示範用途。 它會假設您的掃描器，包含方法`GetNextToken`的識別，並從文字行，傳回權杖。 範例程式碼只需設定觸發程序，每當它看見正確類型的字元。

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char parameterListStartChar = '(';
        private const char parameterListEndChar   = ')';
        private const char parameterNextChar      = ',';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (Char.IsPunctuation(c))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                    tokenInfo.EndIndex = index;

                    if (c == parameterListStartChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;
                    }
                    else if (c == parameterListNextChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;
                    else if (c == parameterListEndChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;
                    }
                }
            return foundToken;
        }
    }
}
```

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>剖析器中支援的參數資訊工具提示
 <xref:Microsoft.VisualStudio.Package.Source>類別會做出一些假設的內容<xref:Microsoft.VisualStudio.Package.AuthoringScope>和<xref:Microsoft.VisualStudio.Package.AuthoringSink>類別時的參數資訊工具提示會顯示，並且會更新。

- 指定剖析器<xref:Microsoft.VisualStudio.Package.ParseReason>輸入參數清單的起點字元時。

- 指定的位置<xref:Microsoft.VisualStudio.Package.ParseRequest>物件是參數清單開始字元之後，立即。 剖析器必須收集可在所有的方法宣告的簽章的位置，並將它們儲存在您的版本中的清單<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件。 這份清單包含方法名稱、 方法型別 （或傳回型別），以及一份可用的參數。 這份清單稍後搜尋的方法簽章或簽章，以顯示參數資訊工具提示中。

  剖析器必須再剖析由指定的行<xref:Microsoft.VisualStudio.Package.ParseRequest>物件來收集輸入的方法，以及使用者過程的進展的名稱是輸入參數。 藉由傳遞至方法的名稱即可達成<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A>方法<xref:Microsoft.VisualStudio.Package.AuthoringSink>物件，然後再呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>剖析方法的參數清單開始字元時，呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>方法時的參數清單下一個字元是剖析，而最後呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>方法剖析的參數清單結尾字元時。 會由使用這些方法呼叫的結果<xref:Microsoft.VisualStudio.Package.Source>類別，以適當地更新參數資訊工具提示。

### <a name="example"></a>範例
 以下是文字的使用者可能輸入行。 這一行下方的數字會指出哪一個步驟由剖析器 （假設剖析將從左到右） 的一行中該位置。 這裡的假設是之前, 的所有項目已經過剖析方法簽章，包括 「 testfunc"方法簽章。

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 剖析器接受步驟說明如下：

1.  剖析器呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A>以文字"testfunc 」。

2.  剖析器呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>。

3.  剖析器呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>。

4.  剖析器呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>。