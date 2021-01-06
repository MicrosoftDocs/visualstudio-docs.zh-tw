---
title: 支援舊版語言服務中的 [自動變數] 視窗
description: 瞭解如何執行 [自動變數] 視窗的支援，它會顯示在正在進行程式設計的程式暫停時，範圍內的運算式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c97ab4db9b71c91689abe0afb85230e5b0242962
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876502"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>舊版語言服務中的 [自動變數] 視窗支援

[自動變數] 視窗會顯示如中斷點或例外狀況) 而暫停 **(的變數** 和參數等運算式。 運算式可以包含變數、本機或全域，以及已在區域範圍中變更的參數。 [自動變數] 視窗也可以包含類別、結構或其他 **類型的具** 現化。 運算式評估工具可以評估的任何作業都可能會顯示在 **[自動** 變數] 視窗中。

 受控封裝架構 (MPF) 不會提供自動 **變數視窗的** 直接支援。 但是，如果您覆寫 <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> 方法，您可以傳回要在 [自動變數] 視窗中顯示的運算式清單。

## <a name="implementing-support-for-the-autos-window"></a>執行自動變數視窗的支援

 為了支援 [自動 **變數] 視窗** ，您只需要 <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> 在類別中執行方法 <xref:Microsoft.VisualStudio.Package.LanguageService> 。 如果原始程式檔中的位置出現 **在 [自動變數] 視窗** 中，則您的實行必須決定。 方法會傳回字串清單，其中每個字串都代表單一運算式。 的傳回值 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 表示清單包含運算式，而 <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> 表示沒有可顯示的運算式。

 傳回的實際運算式是在程式碼中出現于該位置的變數或參數名稱。 這些名稱會傳遞給運算式評估工具，以取得接著顯示在 [自動變數] 視窗 **中的值** 和類型。

### <a name="example"></a>範例
 下列範例示範如何 <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> 使用剖析原因，從方法取得運算式清單的方法的執行 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.ParseReason> 。 每個運算式都會包裝為可實 `TestVsEnumBSTR` <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> 介面的。

 請注意， `GetAutoExpressionsCount` 和 `GetAutoExpression` 方法是物件的自訂方法 `TestAuthoringSink` ，並已加入以支援此範例。 它們表示剖析器 (由剖析器加入至物件的其中一種方法，方法是 `TestAuthoringSink` 呼叫方法，) 可在剖析器 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> 之外存取。

```csharp
using Microsoft.VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override int GetProximityExpressions(IVsTextBuffer buffer,
                                                    int line,
                                                    int col,
                                                    int cLines,
                                                    out IVsEnumBSTR ppEnum)
        {
            int retval = VSConstants.E_NOTIMPL;
            ppEnum = null;
            if (buffer != null)
            {
                IVsTextLines textLines = buffer as IVsTextLines;
                if (textLines != null)
                {
                    Source src = this.GetSource(textLines);
                    if (src != null)
                    {
                        TokenInfo tokenInfo = new TokenInfo();
                        string text = src.GetText();
                        ParseRequest req = CreateParseRequest(src,
                                                              line,
                                                              col,
                                                              tokenInfo,
                                                              text,
                                                              src.GetFilePath(),
                                                              ParseReason.Autos,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        retval = VSConstants.S_FALSE;
                        int spanCount = sink.GetAutoExpressionsCount();
                        if (spanCount > 0) {
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();
                            for (int i = 0; i < spanCount; i++)
                            {
                                TextSpan span;
                                sink.GetAutoExpression(i, out span);
                                string expression = src.GetText(span.iStartLine,
                                                                span.iStartIndex,
                                                                span.iEndLine,
                                                                span.iEndIndex);
                                bstrList.AddString(expression);
                            }
                            ppEnum = bstrList;
                            retval = VSConstants.S_OK;
                        }
                    }
                }
            }
            return retval;
        }
    }
}
```
