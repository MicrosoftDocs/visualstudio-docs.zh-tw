---
title: 舊語言服務中的參數資訊2 |微軟文件
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
ms.openlocfilehash: e2c40c9ca5c038a70714545f4133db0c0dd686d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706740"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>舊版語言服務中的參數資訊
IntelliSense 參數資訊是一個工具提示,當用戶鍵入方法參數清單的參數清單開始字元(通常是打開的括弧)時,顯示方法的簽名。 當輸入每個參數並鍵入參數分隔符(通常是逗號)時,工具提示將更新以粗體顯示下一個參數。

 託管包框架 (MPF) 類別支援管理參數資訊工具提示。 解析器必須檢測參數開始、參數下一個和參數結束字元,並且必須提供方法簽名及其關聯參數的清單。

 舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解更多資訊,請參閱[延伸編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將提高語言服務的性能,並允許您利用新的編輯器功能。

## <a name="implementation"></a>實作
 解析器應設定觸發值<xref:Microsoft.VisualStudio.Package.TokenTriggers>,當它找到參數清單開始字元(通常是開放的括弧)時設置它。 當它找到參數分隔<xref:Microsoft.VisualStudio.Package.TokenTriggers>符(通常是逗號)時,它應設置觸發器。 這將導致更新參數資訊工具提示,以粗體顯示下一個參數。 如果找到參數清單結束字元(通常是<xref:Microsoft.VisualStudio.Package.TokenTriggers>近括弧),解析器應設置觸發器值。

 觸發器<xref:Microsoft.VisualStudio.Package.TokenTriggers>值啟動對<xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A>方法的 調用,該方法反過來<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A><xref:Microsoft.VisualStudio.Package.ParseReason>調用具有 分析原因的方法解析器。 如果解析器確定參數清單開始字元之前的標識符是可識別的方法名稱,它將返回<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件中的匹配方法簽名的清單。 找不到任何方法簽名,則參數資訊工具提示將顯示清單中的第一個簽名。 然後,當鍵入更多的簽名時,將更新此工具提示。 鍵入參數清單結束字元時,將從檢視中刪除參數資訊工具提示。

> [!NOTE]
> 為了確保參數資訊工具提示的格式正確,必須重寫<xref:Microsoft.VisualStudio.Package.Methods>類的屬性以提供相應的字元。 基<xref:Microsoft.VisualStudio.Package.Methods>類假定 C#樣式的方法簽名。 有關如何完成<xref:Microsoft.VisualStudio.Package.Methods>此操作的詳細資訊,請參閱該類。

## <a name="enabling-support-for-the-parameter-info"></a>開啟參數資訊支援
 要支援參數資訊工具提示,必須將的`ShowCompletion`<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>命名參數設定為`true`。 語言服務從<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>屬性中讀取此註冊表項的值。

 此外,<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A>必須`true`將 屬性設置為「參數資訊」工具提示才能顯示。

### <a name="example"></a>範例
 下面是檢測參數清單字元和設置相應觸發器的簡化範例。 此示例僅用於說明目的。 它假定掃描器包含一個標識和返回`GetNextToken`文本行中的權杖的方法。 範例代碼只要看到正確的字元類型,即可設置觸發器。

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

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>支援解析器中的參數資訊工具提示
 當<xref:Microsoft.VisualStudio.Package.Source>顯示和更新參數資訊工具提示時,<xref:Microsoft.VisualStudio.Package.AuthoringScope>類<xref:Microsoft.VisualStudio.Package.AuthoringSink>對和 類的內容進行一些假設。

- 鍵入參數清單開始字元<xref:Microsoft.VisualStudio.Package.ParseReason>時,將給出解析器。

- 物件中<xref:Microsoft.VisualStudio.Package.ParseRequest>給出的位置緊接參數清單開始字元。 解析器必須收集該位置上可用的所有方法聲明的簽名,並將它們存儲在<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件版本中的清單中。 此清單包括方法名稱、方法類型(或返回類型)和可能參數的清單。 稍後將搜尋此清單,查找要在參數資訊工具提示中顯示的方法簽名或簽名。

  然後,解析器必須分析<xref:Microsoft.VisualStudio.Package.ParseRequest>物件指定的行,以收集要輸入的方法的名稱以及使用者在鍵入參數方面所走的路。 這是通過將方法的名稱<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A>傳遞<xref:Microsoft.VisualStudio.Package.AuthoringSink>給 物件上的方法,然後在解析參數清單開始字元時<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>調用 該方法,在解析參數清單下一個字元<xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>時調用 該方法,最後在解析參數清單結束字<xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>元時調用 該方法來實現。 <xref:Microsoft.VisualStudio.Package.Source>類使用這些方法調用的結果來適當地更新參數資訊工具提示。

### <a name="example"></a>範例
 下面是使用者可能輸入的文本行。 行下方的數位指示解析器在行中該位置執行哪個步驟(假設解析移動從左到右)。 此處的假設是,行之前的所有內容已解析為方法簽名,包括"testfunc"方法簽名。

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 解析器執行的步驟概述如下:

1. 解析器使用文本<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A>「testfunc」呼叫。

2. 剖析器呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>。

3. 剖析器呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>。

4. 剖析器呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>。
