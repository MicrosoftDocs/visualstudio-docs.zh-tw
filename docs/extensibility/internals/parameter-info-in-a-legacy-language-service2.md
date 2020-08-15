---
title: 舊版語言 Service2 中的參數資訊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dff6e871320d0727ed2fbec4188e8f7af2e5c5fe
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2020
ms.locfileid: "88237954"
---
# <a name="parameter-info-in-a-legacy-language-service-2"></a>舊版語言服務中的參數資訊2
IntelliSense 參數資訊是一個工具提示，會在使用者輸入參數清單開始字元時顯示方法的簽章， (通常是方法參數清單的左括弧) 。 在輸入每個參數且參數分隔符號 (通常是以逗號) 類型時，工具提示會更新，以粗體顯示下一個參數。

 Managed package framework (MPF) 類別提供管理參數資訊工具提示的支援。 剖析器必須偵測參數開始、參數下一個和參數結尾字元，而且必須提供方法簽章的清單及其相關聯的參數。

 舊版語言服務會實作為 VSPackage 的一部分，但執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解，請參閱 [擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將可改善語言服務的效能，並可讓您利用新的編輯器功能。

## <a name="implementation"></a>實作
 剖析器應該在 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 找到參數清單開始字元時設定觸發程式值， (通常是左括弧) 。 它應該 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 在找到參數分隔符號時設定觸發程式， (通常是逗號) 。 這會更新 [參數資訊] 工具提示，並以粗體顯示下一個參數。 <xref:Microsoft.VisualStudio.Package.TokenTriggers>如果找到參數清單結尾字元 (通常是右括弧) ，剖析器應該設定觸發程式值。

 <xref:Microsoft.VisualStudio.Package.TokenTriggers>觸發程式值會起始對方法的呼叫 <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> ，這會接著以 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 剖析原因呼叫方法剖析器 <xref:Microsoft.VisualStudio.Package.ParseReason> 。 如果剖析器判斷出參數清單起始字元之前的識別碼是可辨識的方法名稱，它會傳回物件中相符的方法簽章清單 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 。 如果找到任何方法簽章，就會在清單中顯示 [參數資訊] 工具提示與第一個簽章。 然後，此工具提示會隨著輸入的簽章數目的增加而更新。 輸入參數清單結尾字元時，會從 view 中移除參數資訊工具提示。

> [!NOTE]
> 若要確保參數資訊工具提示的格式正確，您必須覆寫類別上的屬性， <xref:Microsoft.VisualStudio.Package.Methods> 以提供適當的字元。 基類會 <xref:Microsoft.VisualStudio.Package.Methods> 假設使用 c # 樣式的方法簽章。 <xref:Microsoft.VisualStudio.Package.Methods>如需如何完成此作業的詳細資訊，請參閱類別。

## <a name="enabling-support-for-the-parameter-info"></a>啟用參數資訊的支援
 若要支援參數資訊工具提示，您必須將的 `ShowCompletion` 已具名引數設定 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 為 `true` 。 語言服務會從屬性讀取這個登錄專案的值 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 。

 此外， <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> 屬性必須設定為，才能 `true` 顯示 [參數資訊] 工具提示。

### <a name="example"></a>範例
 以下是一個簡單的範例，可偵測參數清單字元並設定適當的觸發程式。 這個範例僅供說明之用。 它假設您的掃描器包含 `GetNextToken` 可識別並從文字行傳回權杖的方法。 範例程式碼只會在它看到正確種類的字元時設定觸發程式。

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

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>支援剖析器中的參數資訊工具提示
 <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringSink> 當顯示並更新參數資訊工具提示時，類別會對和類別的內容做出一些假設。

- <xref:Microsoft.VisualStudio.Package.ParseReason>當輸入參數清單開始字元時，會提供剖析器。

- 物件中指定的位置 <xref:Microsoft.VisualStudio.Package.ParseRequest> 會緊接在參數清單開始字元之後。 剖析器必須收集該位置上所有可用方法宣告的簽章，並將其儲存在您的物件版本的清單中 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 。 這份清單包含方法名稱、方法類型 (或傳回類型) ，以及可能的參數清單。 此清單稍後會在 [參數資訊] 工具提示中，搜尋要顯示的方法簽章或簽章。

  剖析器接著必須剖析物件所指定的行， <xref:Microsoft.VisualStudio.Package.ParseRequest> 以收集所輸入之方法的名稱，以及使用者在輸入參數中的距離。 這是藉由將方法的名稱傳遞給物件上的方法來完成，然後在剖析參數清單開始字元時呼叫方法，在剖析參數清單 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> 下一個字元時呼叫方法，最後在剖析 <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> 參數清單結尾字元時呼叫方法。 類別會使用這些方法呼叫的結果， <xref:Microsoft.VisualStudio.Package.Source> 以適當地更新參數資訊工具提示。

### <a name="example"></a>範例
 以下是使用者可能輸入的一行文字。 行下方的數位指出剖析器在行中該位置所採取的步驟， (假設剖析會從左至右移動) 。 這裡的假設是，在行前面的所有專案都已經剖析為方法簽章，包括 "testfunc" 方法簽章。

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 剖析器所採取的步驟如下所述：

1. 剖析器會呼叫 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> 具有文字 "testfunc" 的。

2. 剖析器會呼叫 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> 。

3. 剖析器會呼叫 <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> 。

4. 剖析器會呼叫 <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> 。
