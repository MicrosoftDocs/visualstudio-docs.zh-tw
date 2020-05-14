---
title: 支援舊語言服務中的自動視窗 |微軟文件
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
ms.openlocfilehash: 75f8c761721dde5dad4bb75b8675f71f678b06df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704888"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>舊版語言服務中對自動變數視窗的支援
**"自動"** 視窗顯示運算式,如變數和參數,這些運算式在調試的程式暫停時位於作用域中(由於斷點或異常)。 這些運算式可以包括變數、局部變數或全域變數以及已在本地作用域中更改的參數。 **"自動"** 視窗還可以包括類、結構或某些其他類型的實例化。 表達式賦值器可以計算的任何內容都可能顯示在 **「自動」** 視窗中。

 託管包框架 (MPF) 不提供對**自動視窗**的直接支援。 但是,如果重寫方法,<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>則可以傳回要在 **「自動」** 視窗中顯示的運算式清單。

## <a name="implementing-support-for-the-autos-window"></a>實作對自動視窗
 支援**Autos**視窗<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A><xref:Microsoft.VisualStudio.Package.LanguageService>只需在 類中實現 該方法。 在源檔中的位置,實現必須決定哪些運算式應出現在 **「自動」** 視窗中。 該方法返回字串清單,其中每個字串表示單個表達式。 的<xref:Microsoft.VisualStudio.VSConstants.S_OK>返回值表示列表包含表達式,而<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>表示沒有要顯示的表達式。

 返回的實際運算式是出現在代碼中該位置的變數或參數的名稱。 這些名稱將傳遞給表達式賦值器,以獲取隨後在 **「自動」** 視窗中顯示的值和類型。

### <a name="example"></a>範例
 下面的範例顯示了使用分析原因<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A><xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A><xref:Microsoft.VisualStudio.Package.ParseReason>從方法獲取表達式清單的方法的實現。 每個表示式都包裝為實現介面的`TestVsEnumBSTR`<xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR>。

 請注意,`GetAutoExpressionsCount``GetAutoExpression`和 方法是`TestAuthoringSink`物件上的 自定義方法,並且添加是為了支援此示例。 它們表示解析器向`TestAuthoringSink`物件添加的運算式(透過呼<xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A>叫方法)可以在解析器外部存取的一種方式。

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
