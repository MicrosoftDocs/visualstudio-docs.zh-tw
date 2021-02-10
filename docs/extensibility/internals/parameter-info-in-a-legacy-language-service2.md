---
title: 舊版語言中的參數資訊 Service2 |Microsoft Docs
description: 瞭解如何支援 IntelliSense 參數資訊作業，以便在舊版語言服務中輸入方法時，顯示方法簽章。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 60e24162407c4daeb8643bf106c385f76b11c7d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954523"
---
# <a name="parameter-info-in-a-legacy-language-service-2"></a>舊版語言服務2中的參數資訊
IntelliSense 參數資訊是一種工具提示，可在使用者輸入參數清單開始字元時，顯示方法的簽章， (通常是方法參數清單的左括弧) 。 輸入每個參數，而且參數分隔符號 (通常會輸入逗點) ，工具提示會更新以顯示下一個參數（以粗體顯示）。

 Managed 封裝架構 (MPF) 類別提供管理參數資訊工具提示的支援。 剖析器必須偵測參數開始、參數下一個和參數結尾字元，而且必須提供方法簽章和其相關聯參數的清單。

 舊版語言服務會實作為 VSPackage 的一部分，但是執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解，請參閱 [擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。

> [!NOTE]
> 建議您儘快開始使用新的編輯器 API。 這可改善您的語言服務效能，並讓您利用新的編輯器功能。

## <a name="implementation"></a>實作
 剖析器應該在 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 找到參數清單開始字元時設定觸發程式值， (通常是左括弧) 。 它應該 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 在找到參數分隔符號時設定觸發程式， (通常是逗點) 。 這會讓參數資訊工具提示進行更新，並以粗體顯示下一個參數。 <xref:Microsoft.VisualStudio.Package.TokenTriggers>如果找到參數清單結尾字元 (通常是右括弧) ，剖析器應該設定觸發程式值。

 <xref:Microsoft.VisualStudio.Package.TokenTriggers>觸發程式值會起始對方法的呼叫，然後再呼叫 <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法剖析器並剖析原因為 <xref:Microsoft.VisualStudio.Package.ParseReason> 。 如果剖析器判斷參數清單開始字元之前的識別碼是可辨識的方法名稱，則會傳回物件中相符的方法簽章清單 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 。 如果找到任何方法簽章，就會顯示參數資訊工具提示，其中包含清單中的第一個簽章。 然後會更新此工具提示，因為輸入的簽章越多。 當輸入參數清單結尾字元時，就會從 view 中移除參數資訊工具提示。

> [!NOTE]
> 為了確保參數資訊工具提示的格式正確，您必須覆寫類別上的屬性， <xref:Microsoft.VisualStudio.Package.Methods> 以提供適當的字元。 基類會 <xref:Microsoft.VisualStudio.Package.Methods> 假設 c # 樣式的方法簽章。 <xref:Microsoft.VisualStudio.Package.Methods>如需如何完成此操作的詳細資訊，請參閱類別。

## <a name="enabling-support-for-the-parameter-info"></a>啟用參數資訊的支援
 若要支援參數資訊工具提示，您必須將的 `ShowCompletion` 具名引數設定 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 為 `true` 。 語言服務會從屬性讀取這個登錄專案的值 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 。

 此外，您 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> 必須將屬性設定為，才能 `true` 顯示參數資訊工具提示。

### <a name="example"></a>範例
 以下是一個簡單的範例，說明如何偵測參數清單字元以及設定適當的觸發程式。 此範例僅供說明之用。 它會假設您的掃描器包含一個方法 `GetNextToken` ，該方法會從文字行識別並傳回權杖。 範例程式碼只會在它看到正確種類的字元時，設定觸發程式。

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

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>在剖析器中支援參數資訊工具提示
 <xref:Microsoft.VisualStudio.Package.Source>類別會在 <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringSink> 顯示和更新參數資訊工具提示時，對和類別的內容提出一些假設。

- <xref:Microsoft.VisualStudio.Package.ParseReason>當輸入參數清單開始字元時，就會提供剖析器。

- 物件中提供的位置 <xref:Microsoft.VisualStudio.Package.ParseRequest> 緊接在參數清單開始字元之後。 剖析器必須收集該位置所有可用方法宣告的簽章，並將其儲存在您的物件版本的清單中 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 。 這份清單包含方法名稱、方法類型 (或傳回類型) ，以及可能參數的清單。 稍後會在此清單中搜尋方法簽章或簽章，以顯示在參數資訊工具提示中。

  剖析器接著必須剖析物件所指定的行， <xref:Microsoft.VisualStudio.Package.ParseRequest> 以收集所輸入的方法名稱，以及使用者在輸入參數時的距離。 這是藉由將方法的名稱傳遞至 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> 物件上的方法， <xref:Microsoft.VisualStudio.Package.AuthoringSink> 然後在剖析 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> 參數清單開始字元時呼叫方法，在剖析參數清單 <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> 下一個字元時呼叫方法，最後在剖析 <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> 參數清單結尾字元時呼叫方法來完成。 這些方法呼叫的結果會由 <xref:Microsoft.VisualStudio.Package.Source> 類別用來適當地更新參數資訊工具提示。

### <a name="example"></a>範例
 以下是使用者可能輸入的一行文字。 該行下方的數位指出剖析器會在該行的那個位置採取哪一個步驟， (假設剖析是由左到右) 。 此處的假設是已針對方法簽章剖析行之前的所有專案，包括 "testfunc" 方法簽章。

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 剖析器所採取的步驟如下所示：

1. 剖析器會呼叫 " <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> testfunc" 文字。

2. 剖析器會呼叫 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> 。

3. 剖析器會呼叫 <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> 。

4. 剖析器會呼叫 <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> 。
